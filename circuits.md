# Tornado.cash Circuits

Behind the Tornado.cash front-end sits a number of [Circom](https://docs.circom.io/) circuits, which enable the
fundamental privacy guarantees that Tornado.cash users enjoy. These circuits implement the
[Zero Knowledge protocol](https://en.wikipedia.org/wiki/Zero-knowledge_proof) that Tornado.cash's smart contracts
interface with to prove claims about a user's deposit, such as that it is valid, that is hasn't already been withdrawn,
and in the context of [Anonymity Mining](anonymity-mining.md), the number of blocks that exist between a note's deposit
transaction and its withdrawal.

## How ZK Circuits Work

### SNARKs and PLONK

Before trying to understand how Tornado.cash works under the hood, you first need to understand Zero Knowledge circuits,
how they're constructed, and how proofs are generated client-side, then verified on-chain. While there are a
[few different types](https://en.wikipedia.org/wiki/Zero-knowledge_proof#Zero_knowledge_types) of ZK systems,
Tornado.cash relies upon a variant known as "succinct non-interactive arguments of knowledge" (SNARK),
specifically a variant called [PLONK](https://eprint.iacr.org/2019/953).

If you want to develop a deep understanding of how PLONK works, there is a
[great explanation](https://vitalik.ca/general/2019/09/22/plonk.html) by none other than Vitalik Buterin himself.
If you're not a math nerd, but can follow along with a bit of math talk, Vitalik's explanation can be best summarized as:

> ... the "fancy cryptography" it relies on is one single standardized component, called a "polynomial commitment" ...
> A polynomial commitment is a short object that "represents" a polynomial, and allows you to verify evaluations of that
> polynomial, without needing to actually contain all of the data in the polynomial. That is, if someone gives you a
> commitment `𝑐` representing `𝑃(𝑥)`, they can give you a proof that can convince you, for some specific `𝑧`, what the
> value of `𝑃(𝑧)` is.
> 
> So how do the commitments themselves work? ... A trusted-setup procedure generates a set of elliptic curve points
> `𝐺, 𝐺 * 𝑠, 𝐺 * 𝑠² ... 𝐺 * 𝑠ⁿ`, as well as `𝐺₂ * 𝑠`, where `𝐺` and `𝐺₂` are the generators of two elliptic curve
> groups and `𝑠` is a secret that is forgotten once the procedure is finished.
> 
> These points are published and considered to be "the proving key" of the scheme; anyone who needs to make a polynomial
> commitment will need to use these points. A commitment to a degree-d polynomial is made by multiplying each of the
> first d+1 points in the proving key by the corresponding coefficient in the polynomial, and adding the results together.
> 
> Given a program `𝑃`, you convert it into a circuit, and generate a set of equations ..., then convert this set of
> equations into a single polynomial equation. You also generate from the circuit a list of copy constraints. ...
> To generate a proof, you compute the values of all the wires and convert them into three polynomials. ... There is a
> set of equations between the polynomials that need to be checked; you can do this by making commitments to the
> polynomials, opening them at some random `𝑧`, and running the equations on these evaluations instead of the original
> polynomials. The proof itself is just a few commitments and openings and can be checked with a few equations.
> 
> **And that's all there is to it!**

Simple, right? Great.

### Circom and snarkjs

Because we're not all Vitalik, it's best if we have some simple tools that will abstract away the generation and
execution of these complicated polynomial commitments. This is where [Circom](https://docs.circom.io/) and
[snarkjs](https://github.com/iden3/snarkjs) come in.

Circom is easiest to think of as a compiler for a circuit language which acts very much like the kind of
[hardware description language](https://en.wikipedia.org/wiki/Hardware_description_language) that electrical engineers
would use to describe an electrical circuit. Except instead of an electrical circuit, we're describing an
**arithmetic circuit**, which contains components, and the way that they connect together.

When you compile a Circom circuit, the resulting output is an
[R1CS constraint system](https://docs.circom.io/1.-an-introduction/background#rank-1-constraint-system) and a
[Wasm](https://en.wikipedia.org/wiki/WebAssembly) executable that will be used to generate a
[witness](https://docs.circom.io/1.-an-introduction/background#witness).

#### R1CS

To understand R1CS (Rank-1 constraint system), there is of course more math. And where there's important
cryptosystem math, there's a [post by Vitalik](https://medium.com/@VitalikButerin/quadratic-arithmetic-programs-from-zero-to-hero-f6d558cea649#5539).

> An R1CS is a sequence of groups of three vectors `(a, b, c)`, and the solution to an R1CS is a vector `s`, where `s`
> must satisfy the equation `s . a * s . b - s . c = 0`, where `.` represents the dot product - in simpler terms, if we
> "zip together" `a` and `s`, multiplying the two values in the same positions, and then take the sum of these products,
> then do the same to `b` and `s` and then `c` and `s`, then the third result equals the product of the first two results.
> 
> The next step is taking this R1CS and converting it into QAP form, which implements the exact same logic except using
> polynomials instead of dot products ... instead of checking the constraints in the R1CS individually, we can now
> check all of the constraints at the same time by doing the dot product check on the polynomials.
> 
> If we try to falsify any of the variables in the R1CS solution that we are deriving this QAP solution from - say, set
> the last one to 31 instead of 30, then we get a `t` polynomial that fails one of the checks.

In short, the R1CS is a set of polynomial constraints which any proof generated by the circuit must satisfy. These
constraints are [generated by Circom](https://docs.circom.io/2.-circom-fundamentals/constraints-generation) based on the
relationship between various "signals" and operations in your circuit design.

#### Witnesses

Now, depending on what you're using Tornado.cash for, you might not want any witnesses. However, don't worry, if
everything is working correctly, all of the witnesses to your interactions with Tornado.cash will be aggressively
compacted, and their bodies disposed of as you please.

In the context of a PLONK circuit, a witness is the set of values that need to be generated from the inputs to the
circuit, based on the circuit design, to satisfy all of the constraints imposed by the circuit. You can think of the
witness generator produced by Circom as a circuit-specific decompression function which runs your inputs through the
circuit, and snapshots all of the various intermediate values that are produced along the way.

With this expanded form generated from your inputs, you know which values must be assigned to the constraints specified
by the R1CS in order to construct a valid proof.

#### Proof

When you think of a "proof", you probably imagine that it's an incontrovertible guarantee that something is true.
However, in the context of a SNARK, a "proof" actually represents an *argument* that something is *almost certainly*
true. If we were to try to transmit the solution to every single polynomial constraint imposed by a circuit, we would
end up with proofs that were orders of magnitude larger than if we simply show that certain sorts of relationships hold
true between the intermediate state values within the circuit.

It's possible that for any given circuit, someone with sufficient computing power could generate a proof that satisfies
the circuit's constraints in a malformed way, but this would be roughly equivalent in difficulty to
[factoring large primes](https://en.wikipedia.org/wiki/RSA_Factoring_Challenge).

So, when generating a proof for a SNARK circuit, you're calculating the intermediate states of your circuit for a given
input (witness generation), and then calculating the relationships between your inputs, the intermediate states, and
the circuit's outputs.

Once you have the proof that you've satisfied the necessary set of constraints, you can then publish that proof and 
some subset of your inputs and outputs (a.k.a. public signals). Knowing the R1CS, your public signals, your proof, and
the circuit's proving key, anyone can then verify that your proof satisfies the R1CS, and that your public signals
are what would be expected to correspond to your proof.

## Circuits

With that understanding of ZK proving circuits well-in-hand, let's delve into how Tornado.cash uses some very simple
circuits to enable you to privately 

### Deposit

### Tornado Trees



### Tornado Anonymity Mining


