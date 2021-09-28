# Introducción de Tornado.Cash



![](.gitbook/assets/image.png)

Tornado Cash es un **protocolo** **no custodiado** **totalmente descentralizado** que permite transacciones privadas en el espacio crypto.

Como protocolo descentralizado, el smart contract Tornado.Cash se ha implementado en la blockchain Ethereum haciéndolo inmutable. No se puede ni cambiar ni manipular. Por tanto, nadie - incluyendo a los desarrolladores iniciales - lo puede modificar o eliminar. La gobernanza y el minado de los smart contracts se ha desplegado de manera descentralizada.

Como protocolo no custodiado, los usuarios mantienen la custodia de sus cryptodivisas mientras operan en Tornado.Cash. En efecto, por cada depósito, el usuarios obtiene la clave privada que le permite acceder a los fondos previamente depositados, lo cual brinda al usuario el control total de sus activos.

## ¿Cómo se consigue privacidad?

Tornado Cash mejora la privacidad de las transacciones rompiendo la cadena de unión entre las direcciones fuente y destino. Usa un smart contract que acepta el depósito de ETH y otros tokens desde una dirección y habilita su retirada desde otra dirección.

Para preservar la privacidad, es recomendable seguir algunas buenas prácticas, tales como el uso de un relayer para los pagos de gas en las retiradas de fondos mediante una dirección vacía o sin balance previo.

Más detalles disponibles en _Behind the scenes:_ [¿Cómo funciona Tornado.Cash?](https://docs.tornado.cash/v/es/how-does-tornado.cash-work) __y [Consejos para mantener anónimo](https://docs.tornado.cash/v/es/tips-to-remain-anonymous).

## ¿Donde esta actualmente Tornado.Cash?

El protocolo ha estado operando en la **blockchain Ethereum** desde su concepción en 2019. Recientemente se ha desplegado, en junio de 2021, en **Binance Smart Chain** y **Polygon**.

Hoy en día, Tornado.Cash se puede usar con los tokens siguientes:

* En Ethereum : **ETH** _\(Ethereum\)_, **DAI** _\(Dai\)_, **cDAI** _\(Compound Dai\)_, **USDC** _\(USD Coin\)_, **USDT** _\(Tether\)_ & **WBTC** _\(Wrapped Bitcoin\)_
* En Binance Smart Chain: **BNB** _\(Binance Coin\)_.
* En Polygon Network: **MATIC** _\(Polygon\)_

![](.gitbook/assets/non-custodial-anonymous-transactions-on-ethereum-3-.png)

El protocolo también incluye un **sistema de minado anónimo para algunos de sus tokens**, permitiendo a los usuarios ganar **tokens de gobernanza**. Gracias a los tokens TORN, los usuarios de Tornado Cash participan activamente en el modelado del protocolo. La comunidad tiene un peso importante en la evolución de Tornado Cash y la mejora de sus características. En efecto, a través de su gobernanza, la comunidad tiene pleno control sobre los parámetros del protocolo y la distribución de tokens.

Mas información disponible en [Anonymity mining ](https://docs.tornado.cash/v/es/anonymity-mining)y [Tornado.Cash token](https://docs.tornado.cash/v/es/torn).

## ¿Como funciona Tornado.Cash?

[El código tras el funcionamiento de Tornado.Cash](https://github.com/tornadocash) - smart contracts, circuitos y toolchain - son completamente **open sourced.** Trabajando como DAO \(Decentralized Autonomous Organization u Organización Descentralizada Autónoma\), la gobernanza y minado de los smart contracts de Tornado.Cash han sido desplegados enteramente por su comunidad.

El protocolo también funciona con zk-SNARK, lo cual habilita las _**zero-knowledge proofs**_, pruebas de conocimiento cero, permitiendo a los usuarios demostrar la posesión de cierta información sin necesidad de relevarla explícitamente. El uso de esta tecnología se basa en **investigaciones en código abierto realizadas por el equipo de Zcash con la ayuda de la comunidad Ethereum**. Para configurar las claves iniciales de zk-SNARK, la Tornado.Cash[ Trusted Setup Community](https://tornado-cash.medium.com/tornado-cash-trusted-setup-ceremony-b846e1e00be1) se lanzó en mayo de 2020 representada [por 114 contribuyentes](https://tornado-cash.medium.com/the-biggest-trusted-setup-ceremony-in-the-world-3c6ab9c8fffa). Este número significativo de contribuyentes hace imposible comprometer el protocolo mediante la falsificación de las pruebas de conocimiento cero.

La interfaz de usuario está alojada en **IPFS** \(InterPlanetary File System\) por la comunidad, minimizando el riesgo de eliminación de datos. En efecto, la interfaz seguirá existiendo mientras quede al menos un solo usuario alojándola.

_Escrito por_ [_**@ayefda**_](https://torn.community/u/ayefda)  
_****Traducido por_ [_@EeXavi_](https://twitter.com/EeXavi?s=09)

