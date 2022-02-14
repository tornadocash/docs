# Gobernanza

Las siguientes reglas de gobernanza se aplican a todas las pools de Tornado Cash (incluido Tornado Cash Nova).

### ¿Cómo sugerir una propuesta?

Para participar en la gobernanza de Tornado.Cash, lo primero que deben hacer los usuarios es bloquear tokens en el contrato de gobernanza. Si un usuario vota o crea una propuesta, los tokens no se pueden desbloquear antes de que finalice el período de ejecución de la propuesta (8.25 días desde la creación de la propuesta). Los tokens bloqueados también se pueden delegar a otra dirección.

Para crear una propuesta, un usuario debe tener al menos `1,000 TORN`. Todas las propuestas deben ser contratos inteligentes con código verificado que se ejecutan desde el [contrato de gobernanza](https://etherscan.io/address/0x5efda50f22d34F262c29268506C5Fa42cB56A1Ce) (usando `delegatecall`). De esta manera, es fácil auditar y probar cualquier cambio de la gobernanza.

El período de votación de una propuesta es de 3 días. Una propuesta tendrá éxito si recibe una mayoría simple de votos y si hay al menos "25,000 votos TORN" en total (si la participación es demasiado baja, la propuesta falla automáticamente).

Una vez que una propuesta es aprobada, está sujeta a un plazo de 2 días. Después de este periodo de tiempo, cualquier usuario puede ejecutar la propuesta (que inicia los cambios). Si la propuesta no se ejecuta durante 3 días después de ser aprobada, se considera _expired_ (caducada) y ya no se podrá ejecutar.

Todos estos parámetros iniciales son relativamente pequeños, ya que no habrá muchos tokens TORN en circulación desde el principio. Pero a medida que aumente el suministro circulante de TORN, la gobernanza puede ajustar estos umbrales.

Una propuesta puede ser de la siguiente naturaleza:

* Agregar un nuevo pool de Tornado Cash en el proxy
* Cambiar los parámetros de las tasas de recompensa AP
* Despausar/Pausar el token TORN
* Cambiar algunos contratos básicos de minería como el contrato `TornadoTrees`
* Una combinación de todo lo mencionado anteriormente 

Y se pueden hacer muchos más cambios. Para saber exactamente qué se puede cambiar a través de la gobernanza en el protocolo, busca las funciones con el modificador `onlyGovernance` en los contratos inteligentes.

Las funciones de gobernanza están representadas por una flecha roja en [este diagrama de arquitectura](https://viewer.diagrams.net/?highlight=0000ff\&edit=\_blank\&layers=1\&nav=1\&title=tornado-cash-contract-overview.drawio#Uhttps%3A%2F%2Fraw.githubusercontent.com%2FRezan-vm%2Ftornado-cash-edu%2Fmain%2Ftornado-cash-contract-overview.drawio)

NOTA: Partes de este artículo fueron tomadas de [esta publicación de medium](https://tornado-cash.medium.com/tornado-cash-governance-proposal-a55c5c7d0703) Los créditos van al equipo de cash de Tornado.

### ¿Cómo votar?

Primero tienes que depositar (o bloquear) tokens TORN en el contrato de gobernanza.

Ve a: [https://app.tornado.cash/governance](https://app.tornado.cash/governance)

Haz clic en `Manage` -> `Lock Tab`

Aprueba el contrato de gobernanza para transferir tus tokens TORN haciendo clic en el botón `Approve`. Una vez confirmado, elige la cantidad que deseas depositar y haz clic en `Lock`. Confirma la transacción en tu billetera y espera la confirmación.

![](../.gitbook/assets/c05e5a1813edad280544b627b24002dc8d5adcf2.png)

Antes de la votación, el siguiente paso es revisar la propuesta.\
&#x20;Las propuestas legítimas deben tener un post dedicado en [Torn.community](https://torn.community) en la categoría "Proposal". La publicación del foro proporcionará contexto adicional y argumentos sobre la propuesta. Leer el hilo y opinar sobre el tema o problema.

Una vez que se envía una propuesta, debe aparecer en:\
[https://app.tornado.cash/governance](https://app.tornado.cash/governance)\
&#x20;La propuesta se implementa en forma de un contrato inteligente que realiza cambios en el sistema. Por lo tanto, es importante verificar la dirección del contrato inteligente y revisar su código. Encuentra la dirección del contrato de propuesta aquí:

![](../.gitbook/assets/181d612b6c57964bab59c8e5b766f5247211083d.png)

Busca la dirección del contrato en Etherscan y asegúrate de que el código fuente esté verificado y sea legible.

![](../.gitbook/assets/d2d37d169a94f09156e76fa522b7974cb7c9ac3f.png)

Lee el código fuente y asegúrate de que coincida con lo que se describe en el post del foro.

Si no tienes conocimientos técnicos o no te sientes cómodo leyendo el código (Solidity), pídele a alguien de confianza que verifique el contrato por tí.

Si estás de acuerdo (o en desacuerdo) con el código de la propuesta, ¡es hora de votar!

Las propuestas tienen una ventana de votación de 3 días. Esto significa que tenemos 3 días para alcanzar el quórum de votación de 25,000 TORN.

Importante: una vez que has votado, tus tokens se bloquearán durante 8.25 días desde el momento en que se envió la propuesta (el comienzo del período de votación de 3 días). Después de los 8.25 días, podrás retirar tus tokens del contrato de gobernanza. Ten en cuenta de que puedes votar 2 propuestas al mismo tiempo sin incurrir en un período de bloqueo adicional (solo la propuesta enviada más recientemente importará para el bloqueo de 8.25 días).

Para votar, simplemente debes hacer clic en la marca de verificación verde o en la cruz roja, según aceptes o rechaces la propuesta. ¡Confirma la transacción con tu Metamask y tu voto estará adentro!

### ¿Cómo delegar el voto?

Si eres poseedor de tokens TORN, puedes delegar tu poder de voto en otra persona sin tener que enviarle a esa persona los tokens.

IMPORTANTE: si delegas tus tokens y tu delegado vota o inicia una propuesta, tus tokens se bloquearán durante 8.25 días desde el momento en que comenzó la propuesta por la que votó el delegado. Ten en cuenta que siempre puedes dejar de delegar en cualquier momento.

Para delegar, ve a:[https://app.tornado.cash/governance](https://app.tornado.cash/governance)

Primero es necesario que bloquees tus tokens en el contrato de gobernanza. Haz clic en la pestaña **`Manage`** -> **`Lock`**

Aprueba el contrato de gobernanza para transferir tus tokens TORN haciendo clic en el botón **`Approve`**. Una vez confirmado, elige la cantidad que deseas delegar y haz clic en **`Lock`**. Confirma la transacción en tu billetera y espera la confirmación.

![](<../.gitbook/assets/c05e5a1813edad280544b627b24002dc8d5adcf2 (1).png>)

El último paso, es hacer la delegación propiamente dicha. Ir de nuevo a [https://app.tornado.cash/governance](https://app.tornado.cash/governance)

Haz clic en la pestaña **`Manage`** -> **`Delegate`**

Inserta la dirección a la que deseas delegar y haz clic en **`Delegate`**. Aprueba la transacción en tu billetera y espera la confirmación.

![](../.gitbook/assets/43c05d176d7f75a336af7a865565c9b23786b98c.png)

La totalidad de tu balance bloqueado se delegará.

Puedes dejar de delegar en cualquier momento. Para anular la delegación, simplemente usa el botón `Undelegate` en la pestaña `Manage` -> `Undelegate`.

_Escrito por_ [_@rezan_](https://torn.community/u/Rezan/summary)__