# Introducción de Tornado Cash

![](.gitbook/activos/imagen.png)

Tornado Cash es un **protocolo totalmente descentralizado** y **sin custodia** que permite transacciones privadas en el espacio cripto.

Como protocolo descentralizado, los contratos inteligentes de Tornado.Cash se implementaron dentro de la red de Ethereum, lo que los hace inmutables. No se pueden cambiar ni manipular. Por lo tanto, nadie, incluidos los desarrolladores iniciales, puede modificarlos o cerrarlos. Todos los contratos inteligentes de gobernanza y minería son implementados por la comunidad de manera descentralizada.

Como protocolo sin custodia, los usuarios mantienen la custodia de sus criptomonedas mientras operan Tornado.Cash. De hecho, en cada depósito, se les proporciona la clave privada que permite el acceso a los fondos depositados, lo que brinda a los usuarios un control total sobre sus activos.

## ¿Cómo se logra la privacidad?

Tornado Cash mejora la privacidad de las transacciones al romper el vínculo que existe entre las direcciones de origen y destino. Utiliza un contrato inteligente que acepta ETH y otros depósitos de tokens desde una dirección y permite su retiro desde una dirección diferente.

Para preservar la privacidad, se recomiendan algunas buenas prácticas, como el uso de un repetidor para los pagos de gas para retirar fondos hacia una dirección sin saldo preexistente.

Hay más detalles disponibles en _Detrás de escena:_ [_¿Cómo funciona Tornado.Cash?_](general/how-does-tornado.cash-work.md) _\*\*\*\*_ & [Consejos para permanecer anónimo](general/consejos-para-permanecer-anónimo.md).

## ¿Dónde está Tornado.Cash?

Desde su creación en 2019, Tornado Cash ha estado operando **en la red de Ethereum**. El protocolo ha estado ofreciendo pools diversificados de cantidad fija para seis tokens (ETH, DAI, cDAI, USDC, USDT y WBTC) manejados por la red de Ethereum.

Desde junio de 2021, además de la red de Ethereum, los contratos inteligentes de Tornado Cash **también se implementaron en otras redes laterales y secundarias**. Estas implementaciones permitieron que la herramienta admitiera nuevos tokens o se beneficiara de las ventajas de la Layer-2 "L2", como transacciones más rápidas y económicas.

Por lo tanto, a partir de hoy, Tornado Cash está operando actualmente en:

* **Ethereum Blockchain**: **ETH** (Ethereum), **DAI** (Dai), **cDAI** (Dai compuesto), **USDC** (USD Coin), **USDT* * (Tether) y **WBTC** (Wrapped Bitcoin),
* **Binance Smart Chain**: **BNB** (Binance Coin),
* **Red Polygon**: **MATIC** (Polygon),
* **Red Gnosis (antigua xDAI chain)**: **xDAI** (xDai),
* **Red principal Avalanche**: **AVAX** (Avalanche),
* **Optimism**, como Layer-2 "L2" para **ETH** (Ethereum),
* **Arbitrum One**, como Layer-2 "L2" de **ETH** (Ethereum).

![](.gitbook/assets/logotipos.png)

Hasta diciembre de 2021, el protocolo incluía un sistema de extracción de anonimato para algunos de estos tokens, lo que permitía a sus usuarios obtener un token de gobernanza llamado (**TORN**). Los usuarios finalmente pudieron ganar TORN depositando en los pools de ETH, DAI, cDAI y WBTC.

_Más información sobre_ [_Minería de anonimato_](tornado-cash-classic/anonymity-mining.md) _&_ [_Token de Tornado.Cash_](general/torn.md) _están disponibles._

**Gracias al token TORN, los usuarios de Tornado Cash pueden participar activamente en la configuración del protocolo**. La comunidad tiene un fuerte peso en la evolución de Tornado Cash y la mejora de sus características. De hecho, los parámetros del protocolo y la distribución de tokens están completamente bajo el control de la comunidad a través de esta gobernanza.

Se puede acceder a todos los pools mencionados anteriormente en [tornadocash.eth.link](https://tornadocash.eth.link). Operan **bajo el principio de depósitos y retiros de monto fijo**. Significa que cada token tiene de 2 a 4 pools diferentes, lo que permite transacciones de solo 2 a 4 montos fijos diferentes _(por ejemplo, ETH tiene cuatro pools diferentes, uno para cada uno de estos montos: 0.1, 1, 10 y 100 ETH)_.

### Tornado Cash Nova

Con el [**lanzamiento de Tornado Cash Nova** (versión beta) en diciembre de 2021](https://tornado-cash.medium.com/tornado-cash-introduces-arbitrary-amounts-shielded-transfers-8df92d93c37c), Se ha agregado al protocolo un **pool actualizado con nuevas características únicas**. Los usuarios ya no están limitados por transacciones con cantidades fijas. Con la incorporación de Tornado Cash Nova, pueden beneficiarse del uso de **un pool de montos arbitrarios y transferencias protegidas**.

Tornado Cash Nova opera en Gnosis Chain (anteriormente xDai Chain) como "Layer" o "Capa" 2 para optimizar la velocidad y el costo. Permite **depósitos y retiros de montos completamente personalizados en ETH**. Este pool también permite transacciones protegidas en las que los usuarios pueden **transferir la custodia de sus tokens mientras permanecen en el pool**.

Se puede acceder a Tornado Cash Nova (versión beta) en [nova.tornadocash.eth.link](https://nova.tornadocash.eth.link). Puedes encontrar más información relacionada con el funcionamiento de Tornado Cash Nova en la sección dedicada de nuestros documentos.

## ¿Cómo funciona Tornado.Cash?

[Los códigos detrás del funcionamiento de Tornado.Cash](https://github.com/tornadocash) - los contactos inteligentes, circuitos y la cadena de herramientas - son completamente **de código abierto.** Trabajando como DAO (Organización Autónoma Descentralizada), la gobernanza de Tornado.Cash y los contratos inteligentes de minería son desplegados por su comunidad.

El protocolo también funciona con zk-SNARK, que permite pruebas de conocimiento cero que permiten a los usuarios demostrar la posesión de información sin necesidad de revelarla. El uso de esta tecnología se basa **en investigaciones de código abierto realizadas por el equipo de Zcash con la ayuda de la comunidad de Ethereum**. Para configurar las claves iniciales de zk-SNARK, Tornado.Cash [ "Trusted Setup Community"](https://tornado-cash.medium.com/tornado-cash-trusted-setup-ceremony-b846e1e00be1) se lanzó en mayo de 2020 y se contabilizó [para 1114 contribuciones](https://tornado-cash.medium.com/the-biggest-trusted-setup-ceremony-in-the-world-3c6ab9c8fffa). Este número significativo de contribuyentes hace que sea imposible comprometer el protocolo falsificando pruebas de conocimiento cero.

La interfaz de usuario está alojada en **IPFS** "InterPlanetary File System" o "Sistema de archivos interplanetarios" por la comunidad, lo que minimiza los riesgos de que se eliminen los datos. De hecho, la interfaz funcionará siempre que al menos un usuario la aloje.

_Escrito y editado por_ [_@ayefda_](https://torn.community/u/ayefda)\_\_