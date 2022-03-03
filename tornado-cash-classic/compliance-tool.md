# Herramienta de Cumplimiento

Por diseño, todo es público en la blockchain, lo que puede privar a los usuarios de su derecho a la privacidad. Cualquiera puede tener acceso al historial completo de transacciones de todos. En respuesta a este problema, el protocolo Tornado.Cash permite a los poseedores de criptomonedas recuperar su privacidad y anonimato. De hecho, permite a los usuarios romper el vínculo que existe entre una dirección de origen y una de destino.

Sin embargo, mantener la privacidad y preservar la libertad financiera nunca debe ser a expensas de incumplimientos. El derecho a la privacidad radica en la capacidad de tener control sobre la información que proporcionamos y a quién se la proporcionamos.

De esta manera, **la Herramienta de Cumplimiento de Tornado.Cash permite a los usuarios probar el origen de sus fondos.** Gracias a la Nota generada después de cada depósito, **esta herramienta emitirá una prueba verificada criptográficamente del historial de transacciones** utilizando las direcciones de Ethereum que se utilizaron para depositar y retirar activos.

Puedes visitar la publicación de Medium relacionada con esta herramienta para obtener más información sobre su desarrollo y lanzamiento: [**Tornado.Cash compliance Medium Post**](https://tornado-cash.medium.com/tornado-cash-compliance-9abbf254a370).

Por lo tanto, si alguna vez necesitas probar el origen de los activos retenidos retirados de uno de los pools de Tornado.Cash, te invitamos a utilizar la siguiente [Herramienta de Cumplimiento](https://tornadocash.eth.link/compliance):

![https://app.tornado.cash/compliance/](../.gitbook/assets/capture-de-cran-2021-09-02-a-14.57.11.png)

## ¿Cómo usar la herramienta de cumplimiento?

Con cada depósito realizado a través de la [aplicación Tornado.Cash](https://tornadocash.eth.link), el protocolo genera una nueva Nota. Esta Nota es necesaria para retirar los activos depositados más adelante en cualquier dirección de retiro. Es esta misma Nota que, en caso de ser necesario, permite a los usuarios generar un Informe de Cumplimiento para acreditar el origen de sus activos.

_Más información sobre cómo depositar y retirar activos en Tornado.Cash se encuentra disponible en:_ [_Deposit & Withdraw_](deposit-withdraw.md)_._

Para obtener un Informe de Cumplimiento, el usuario solo necesita copiar la Nota, generada después del depósito, en la casilla correspondiente.

### Antes de retirar

Si la nota aún no ha sido usada (es decir, los activos aún no se retiraron), la herramienta de Cumplimiento solo proporcionará información sobre el depósito:

* Hash de transacción del depósito;
* La dirección de origen;
* El hash de Compromiso.

El compromiso es el área aleatoria de bytes generados en cada depósito que se envía al contrato inteligente Tornado.Cash para caracterizar la transacción.

![https://app.tornado.cash/compliance/](../.gitbook/assets/capture-de-cran-2021-09-02-a-15.07.01.png)

_Puedes encontrar más información sobre cómo Tornado.Cash logra brindar privacidad leyendo [¿Cómo funciona Tornado.Cash?_](../general/how-does-tornado.cash-work.md)__

### Después de retirar

Si la nota se usó (es decir, los activos se retiraron a una dirección determinada usando la nota), la Herramienta de Cumplimiento completará la información anterior agregando:

* Hash de transacción del retiro;
* La dirección de destino;
* El hash anulador.

El hash anulador es una entrada pública que se envía a la red para que se verifique con el contrato inteligente y los datos del árbol Merkle para permitir el retiro.

![https://app.tornado.cash/compliance/](../.gitbook/assets/capture-de-cran-2021-09-02-a-15.12.23.png)

Por lo tanto, la herramienta permite a los usuarios volver a vincular las direcciones de origen y destino para probar el historial de transacciones de los activos utilizados en Tornado.Cash.

Esta información también se puede descargar en formato PDF, lo que facilita su envío a cualquier tercero deseado:

![https://app.tornado.cash/compliance/](../.gitbook/assets/capture-de-cran-2021-09-02-a-15.12.53.png)

_Escrito por_ [_@ayefda_](https://torn.community/u/ayefda)
