# Як працює Tornado.Cash?

Перш ніж зануритися в підручники, що пояснюють та полегшують використання Tornado.Cash, ось загальний огляд глобального функціонування протоколу.

### Глобальний огляд функціонування Tornado.Cash

Для забезпечення конфіденційності Tornado.Cash **використовує розумні контракти, які приймають депозити токенів з однієї адреси та дозволяють їх вилучати з іншої адреси**. Ці розумні контракти працюють як пули, які змішують усі депоновані активи. 

Як тільки засоби виводяться з пулу з нової адреси, зв'язок між джерелом і отримувачами в мережі блокчейн розривається. Таким чином, виведені криптоактиви анонімізуються. 

Коли користувач вкладає кошти в пул \ (він же депозит \), генерується приватна нотатка (note). Ця приватна записка (note) працює як приватний ключ для доступу користувача до цих коштів пізніше. Щоб вивести їх, той самий користувач може використати іншу адресу - стару чи нову - і повернути свої кошти завдяки цьому приватному ключу.

Сила захисту анонімності такого протоколу природно випливає з його кількості користувачів та розміру його пулу. Чим більше користувачів вносить гроші в пул, тим краще. Однак, щоб зберегти конфіденційність та анонімність, користувач повинен мати на увазі деякі основні правила, такі як:

* Використати ретранслятор (relayer) для оплати газу при знятті;
* Залишати деякий проміжок часу між внесенням депозиту та виведенням коштів;
* Змішувати свої активи разом із активами інших користувачів - чекаючи кількох транзакцій, перш ніж вивести свої активи.

_More recommendations are provided on:_ [_Tips to remain anonymous_](tips-to-remain-anonymous.md)_._

### Contribution of zk-SNARK & hashing process

Tornado.Cash use Zero-Knowledge Succinct Non-Interactive Argument of Knowledge \(also called zk-SNARK\) to verify & allow transactions.

To process a deposit, Tornado.Cash generates a random area of bytes, computes it through the [Pederson Hash](https://iden3-docs.readthedocs.io/en/latest/iden3_repos/research/publications/zkproof-standards-workshop-2/pedersen-hash/pedersen.html) \(as it is friendlier with zk-SNARK\), then send the token & the 20 mimc hash to the smart contract. The contract will then insert it into the Merkle tree.

To process a withdrawal, the same area of bytes is split into two separate parts: the **secret** on one side & the **nullifier** on the other side. The nullifier is hashed. This nullifier is a public input that is sent on-chain to get checked with the smart contrat & the Merkle tree data. It avoids double spending for instance.

Thanks to zk-SNARK, it is possible to prove the 20 mimc hash of the initial commitment and of the nullifier without revealing any information. Even if the nullifier is public, privacy is sustained as there is no way to link the hashed nullifier to the initial commitment. Besides, even if the information that the transaction is present in the Merkle root, the information about the exact Merkle path, thus the location of the transaction, is still kept private.

Deposits are simple on a technological point of view, but expensive in terms of gas as they need to compute the 20 mimc hash & update the Merkle tree. At the opposite, the withdrawal process is complex, but cheaper as gas is only needed for the nullifier hash and the zero-knowledge proof.



_Translated by_ [_**@chieftalion**_](https://torn.community/u/chieftalion/)

