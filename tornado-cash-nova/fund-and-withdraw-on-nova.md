# Fondeos y retiros en Nova

Tornado Cash funciona al romper el vínculo que existe entre las direcciones de origen y destino en la blockchain. Para hacerlo, el protocolo necesita que los tokens se depositen en un pool desde una dirección y luego se retiren a través de otra dirección.

Este principio sigue siendo el mismo para Tornado Cash Nova. En cuanto a los pools tradicionales de cantidad fija, estas dos acciones son fundamentales para la eficiencia de la herramienta:

* El proceso de “Financiación o Fondeo”,
* El proceso de “Retiro”.

## Proceso de financiación <a href="#funding-process" id="funding-process"></a>

La gran novedad en comparación con los pools de Tornado Cash tradicionales es que **las cantidades depositadas ya no están predefinidas.** Los usuarios pueden elegir una cantidad personalizada dentro de la capacidad del saldo de sus billeteras.

Por lo tanto, si deseas poner 0,4 ETH en el pool, puedes hacerlo todo a la vez en lugar de realizar cuatro transacciones separadas con el pool tradicional de 0,1 ETH.

![](https://i.imgur.com/rqmzdgG.gif)

### ¿Cómo funciona? <a href="#how-does-it-work" id="how-does-it-work"></a>

#### **El primer depósito 💰**

* El primer paso es iniciar sesión en Tornado Cash Nova a través de una cuenta de Metamask.
* Tu cuenta no está configurada aún (botón `Set up account` visible en la esquina superior derecha). Para configurar tu cuenta, puedes:
    * **Haz clic en `Set up account`**: la dirección de tu wallet se registrará en Nova sin necesidad de depositar tokens. Esta acción te va a permitir recibir transferencias o depósitos dentro del pool desde cualquier otra dirección.
   * **Elige la dirección de tu wallet activa como la dirección del destinatario**: al depositar tokens en el pool, tu cuenta (con tu dirección protegida y clave protegida) se creará automáticamente. Los fondos depositados complementarán tu saldo protegido.
   * **Elige otra dirección registrada:** los tokens se agregarán al saldo protegido de la dirección del destinatario elegido. Esta dirección del recipiente debe ser una dirección protegida que se haya registrado anteriormente en el pool.

Cuando inicias sesión, la `Recipient address` o `Dirección del destinatario` se completa de forma predeterminada con la dirección de tu wallet. Puedes cambiarlo dependiendo de cómo deseas usar la herramienta.

Si configuras una nueva cuenta, podrás iniciar sesión en el pool más tarde, verificar tu saldo protegido de Tornado o recibir transferencias protegidas utilizando tu dirección protegida o tu clave protegida.

_Toda la información sobre cómo usar estos elementos para iniciar sesión o dónde encontrar tu clave protegida está disponible en_ [log-in-tornado-cash-nova.md](log-in-tornado-cash-nova.md "mention") _._

#### **Los siguientes depósitos 💸**

Los siguientes depósitos están sujetos a las mismas reglas que el primero, excepto que la cuenta ya está configurada.

Al iniciar sesión en el pool con tu dirección / clave protegida, puedes depositar las cantidades elegidas en tu dirección protegida elegida como tú desees.

⚠️ Debido que es una versión beta, los depósitos actualmente están limitados a 1 ETH por transacción.
Sin embargo, si la comunidad desea aumentar este límite, la cantidad máxima de 1 ETH siempre se puede cambiar a través de una propuesta de gobernanza.

## Proceso de retiro <a href="#withdrawing-process" id="withdrawing-process"></a>

![](https://i.imgur.com/qn9eJXS.gif)

Para retirar fondos del pool Nova, puedes:

* elige entre un conjunto de cuatro cantidades predeterminadas (0.1, 0.3, 0.5 y 1 ETH),
* elige una cantidad completamente personalizada a través del botón `Set custom`.

### Opción personalizada para retiros <a href="#custom-option-for-withdrawal" id="custom-option-for-withdrawal"></a>

**La opción personalizada solo debe elegirse con pleno conocimiento de los siguientes hechos y con total confianza en tus acciones.**

Para mantener tu privacidad, se recomienda encarecidamente elegir una de las cuatro cantidades sugeridas, ya que permitirá que el retiro se mezcle con el retiro de la multitud.

De hecho, dependiendo de la cantidad elegida, se puede deducir una conexión entre tu transacción inicial de fondos y tu retiro si:

* la cantidad financiada inicialmente y la cantidad retirada son exactamente iguales,
* los montos financiados y retirados se pueden vincular fácilmente a través de una suma.

_Por ejemplo, un depósito de 0,42 ETH se puede vincular a un retiro de exactamente 0,42 ETH o dos veces 0,21 ETH, lo que podría comprometer el anonimato. Sin embargo, con un retiro de 0.391 ETH, la privacidad se preserva mejor, ya que no existe un vínculo obvio entre las cantidades de 0.42 y 0.391._

### Transacciones a través de Gnosis Chain (L2) <a href="#transctions-through-gnosis-chain-l2" id="transctions-through-gnosis-chain-l2"></a>

Para transacciones más baratas, Gnosis Chain (anteriormente xDAI Chain) se usa como Layer-2. Para ello, se utiliza un puente entre la red principal de ETH "Mainnet" y WETH de Gnosis Chain.

Por lo tanto, para evitar ataques de spam que sobrecarguen el puente, el monto del retiro debe ser superior a los 0,05 ETH.

_Escrito por_ [_@ayefda_](https://torn.community/u/ayefda)__