# Herramienta de Cumplimiento Normativo

Por diseño, todo es público en la blockchain, lo cuál priva al usuario de su derecho a la privacidad. Cualquiera puede tener acceso a el historial completo de transacciones. Como respuesta a este problema fundamental, el protocolo Tornado.Cash permite a los propietarios de cryptodivisas recuperar su privacidad y ganar en anonimato. En efecto, permite a los usuarios romper el nexo on-chain entre direcciones origen y destino.

No obstante, mantener la privacidad y preservar la libertad financiera no deberia ocurrir a expensas del incumplimiento normativo. El derecho a privacidad se sustenta en la capacidad de controlar la información que revelamos y a quién la revelamos.

En esta medida, **La Herramienta de Cumplimiento Normativo de Tornado.Cash permite al usuario probar el origen de sus fondos.** Gracias a la nota generada después de cada depósito, **esta herramienta genera una prueba cryptográficamente verificada del historial de transacciones** utilizando la direccion Ethereum empleada en el depósito y retiro de los activos.

Puede visitar en Medium el articulo relacionado con esta herramienta para aprender mas sobre su desarrollo y puesta en marcha: [**Tornado.Cash compliance Medium Post**](https://tornado-cash.medium.com/tornado-cash-compliance-9abbf254a370).

En conclusión, si usted necesita en alguna ocasión probar el origen de activos retirados de alguna pool de Tornado.Cash, le invitamos a usar la siguiente [Herramienta](https://app.tornado.cash/compliance/):

![https://app.tornado.cash/compliance/](.gitbook/assets/capture-de-cran-2021-09-02-a-14.57.11.png)

## Cómo usar la Herramienta de Cumplimiento Normativo?

Con cada depósito realizado con [Tornado.Cash app](https://app.tornado.cash/), una nueva Nota es generada por el protocolo. Esta Nota es necesaria para retirar los activos depositados posteriormente a cualquier direccion de retiro. Es la misma Nota que, si fuera necesario, permite al usuario generar el Informe de Cumplimiento Normativo \(_Compliance Report_\) para probar el origen de sus activos. 

_Mas información sobre cómo depositar y retirar activos en Tornado.Cash a su disposición en: _[_Deposit & Withdraw_](untitled.md)_._

Para obtener el Informe de Cumplimiento Normativo, el usuario solamente necesita copiar la Nota, generada después del depósito, en el cuadro dedicado.

### Antes del retiro

Si la Nota no se ha consumido todavía \(p.e. los activos no se han retirado todavía\), la Herramienta de Cumplimiento solamente le entregará información sobre el depósito:

* Hash de la transacción de depósito;
* Direccion origen;
* Hash del _commitment_.

El _commitment_ es el hash aleatorio del área de bytes generado en cada depósito que se envía al smart contract de Tornado.Cash para caracterizar la transacción.

![https://app.tornado.cash/compliance/](.gitbook/assets/capture-de-cran-2021-09-02-a-15.07.01.png)

_Puede encontrar mas información sobre cómo Tornado.Cash consigue darle privacidad leyendo_ [_How does Tornado.Cash work?_](how-does-tornado.cash-work.md)

### Después del retiro

Si la Nota ya se ha usado \(p.e. los activos se retiraron a una direccion utilizando la Nota\), la Herramienta de Cumplimiento completará la información anterior añadiendo:

* Hash de la transacción de retiro;
* Dirección destino;
* Hash del _nullifier_.

El hash del _nullifier_ es un parámetro público que se envia on-chain para ser comprobado con el smart contract y el árbol de datos de Merkle para permitir el retiro.

![https://app.tornado.cash/compliance/](.gitbook/assets/capture-de-cran-2021-09-02-a-15.12.23.png)

En conclusión, la herramienta permite a los usuarios rehacer la conexión entre direcciones origen y destino con el propósito de probar el historial de transacción de activos utilizado en Tornado.Cash.

Esta información se puede descargar en formato PDF, facilitando su envío a terceras partes:

![https://app.tornado.cash/compliance/](.gitbook/assets/capture-de-cran-2021-09-02-a-15.12.53.png)

_Escrito por_ [_@ayefda_](https://torn.community/u/ayefda)

_Traducido por_ [_@EeXavi_](https://twitter.com/EeXavi?s=09) 