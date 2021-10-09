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



## Circuits

## Deposit

### Tornado Trees



### Tornado Anonymity Mining


