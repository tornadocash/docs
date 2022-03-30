# Staking



Desde su creación, los usuarios de Tornado Cash utilizan el token TORN para la gobernanza. Su principal utilidad es permitir la sugerencia de propuestas y la votación tanto como en la blockchain (a través de TORN bloqueado para propuestas de gobernanza) como fuera de blockchain (en Snapshot).

Desde la ejecución de la [décima propuesta de gobernanza de Tornado Cash](https://tornadocash.eth.link/governance/10), El token TORN ha ganado otra utilidad. De hecho, **con la introducción de un registro de retransmisión descentralizado,** **se implementó una recompensa de staking para todos los poseedores de TORN bloqueado en el contrato de gobernanza.**

[TORN](torn.md) los que posean TORN aún pueden bloquear sus tokens en el contrato de gobernanza como solían hacerlo con fines de gobernanza. La diferencia significativa es que ahora pueden recibir una parte de las tarifas recaudadas por el protocolo de los repetidores. Obviamente, la proporción de la recompensa será igual a la proporción del TORN que tengan bloqueado.

#### **¿ DE DÓNDE PROVIENE ESTAS TARIFAS RECAUDADAS ?**

El cobro de estas tarifas fue posible gracias a la implementación de un registro de repetidores descentralizado. Para aparecer en la interfaz de usuario del protocolo, los repetidores deben hacer staking de una cantidad determinada de TORN (actualmente establecido por la gobernanza en `300 TORN`). El funcionamiento de este registro de repetidores se explica más extensamente [en esta publicación del foro](https://torn.community/t/proposal-relayer-registry-setting-parameters-after-audit/2134) y en la [página de documentación del registro de repetidores](how-to-become-a-relayer.md).

En pocas palabras, por cada retiro a través del método de retransmisión, el retransmisor elegido debe pagar una tarifa al protocolo del saldo en estaking (que debe mantenerse por encima del umbral de `300 TORN` ). Actualmente, esta tarifa ha sido fijada en `0.3%` por la gobernanza y se puede cambiar en cualquier momento a través de una propuesta y votación en la blockchain.

### ¿ Cómo hacer staking de TORN ?

Como se mencionó anteriormente, el proceso para bloquear tokens TORN no ha cambiado.

* Sucede aquí ➡️ [https://tornadocash.eth.link/governance](https://tornadocash.eth.link/governance) ⬅️, haciendo clic en **`Manage`** y luego en la pestaña **`Lock`**
* El contrato de gobernanza debe aprobarse para permitir la transferencia de tus tokens al contrato inteligente. Para hacerlo, debes hacer clic en el botón **`Approve`**
* Una vez que se confirma, puedes elegir la cantidad de token para bloquear, luego haz clic en **`Lock`**
* Todo lo que tienes que hacer después es confirmar la transacción en tu billetera y esperar a que se confirme la transacción.

![](../.gitbook/assets/c05e5a1813edad280544b627b24002dc8d5adcf2.png)

### ¿Cómo reclamar tus recompensas de Staking?

Ahora que tus tokens TORN se han mantenido bloqueados en el contrato de gobernanza, puedes reclamar tus recompensas de staking. ¿Como hacer eso? Puedes conseguir todo aquí ➡️ [https://tornadocash.eth.link/governance](https://tornadocash.eth.link/governance) ⬅️

Tan pronto como inicies sesión en la página, podrás ver tus recompensas de staking en la parte superior, esperando a ser reclamadas. 💰

![](../.gitbook/assets/head.png)

* Clic **`Manage`** -> pestaña **`Claim`** -> _botón._ **`Claim`**

![](<../.gitbook/assets/claim (1).png>)

_Eso es todo, hemos terminado_ :wink:__

__

_Escrito por_ [_**@bt11ba**_](https://torn.community/u/bt11ba/) _y_ [_**@ayefda**_](https://torn.community/u/ayefda)
