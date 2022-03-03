# Minería de Anonimato

La minería de anonimato es un incentivo para aumentar el nivel de privacidad en cualquier protocolo de unión o mezcla de monedas al recompensar a los participantes con puntos de anonimato (AP) dependiendo de cuánto tiempo mantengan sus activos en un pool.

{% hint style="warning" %}
_El programa de minería de anonimato de Tornado Cash comenzó el 18 de diciembre de 2020 y finalizó el 18 de diciembre de 2021._
{% endhint %}

Las personas depositan en cualquiera de los pools de anonimato admitidos (ETH, WBTC, DAI o cDAI) y se les recompensa con una cantidad fija de AP por bloque, durante el período que su depósito permanece en el pool. Estos puntos se pueden canjear por TORN una vez reclamados.

### Puntos de anonimato (AP)

_Los lectores deben de tener en cuenta que algunos depósitos de menor denominaciones en el momento de escribir este artículo no producen un rendimiento positivo debido a los costos de gas necesarios para retirar, canjear e intercambiar puntos de anonimato_

Uno de los miembros de la comunidad creó [una hoja de cálculo de minería 13](https://torn.community/t/anonymity-mining-spreadsheet/720) que ayuda a calcular el rendimiento porcentual anual (APY) para cada pool y cada conjunto de denominación, a través de la estimación de las tarifas requeridas para reclamar una recompensa. **Se recomienda ver esta hoja de cálculo y planificarse antes de esperar obtener rendimientos.** En la parte inferior de la hoja de cálculo, puedes ver cada pool seleccionando la pestaña asociada.

### Cómo obtener AP

1\. Decide qué cantidad y activo depositar seleccionándolo a través del menú desplegable, antes de hacer clic en "Connect" y "Deposit".

![](../.gitbook/assets/m3fh0gl.png)

2\. Toma un registro de la nota de depósito y haz una copia de seguridad de forma segura, **no compartas esto con nadie o te arriesgarás a perder tu depósito y recompensa.**

![](../.gitbook/assets/vhustru.png)

3\. Genera la prueba y envía la transacción.

4\. Tu depósito ahora debería poder verse en la parte inferior de la página, puedes rastrear cuánto AP ganarás aquí; recuerda que cuanto más tiempo permanezca activo tu depósito, más AP ganarás.

![](../.gitbook/assets/k6juetp.png)

_Las notas que están activas (no retiradas) se conocen como notas "no gastadas o usadas"._

### Cómo reclamar AP

1\. Primero tienes que crear una cuenta de minería y almacenar esas credenciales en la blockchain para una fácil recuperación (requiere una transacción), **al igual que al depositar notas, nunca compartas tu clave de recuperación de minería con nadie** y asegúrate de hacer una copia de seguridad y de guardarlo en un lugar seguro. Esta característica no es compatible con las billeteras de hardware, por lo que se recomienda almacenar la información tal y como se presenta_._

![](../.gitbook/assets/lskzkgk.png)

2\. Toma un depósito activo proporcionando una nota que no ha sido reclamada y retírala a la dirección que prefieras y decide si usar un retransmisor o no (_para mantener el anonimato de un depósito, siempre se recomienda usar un retransmisor_), esto llevará la nota a un estado de "usado o gastado".

![](../.gitbook/assets/aid86cj.png)

**Recuerda mantener tus notas de depósito en secreto incluso después de retirarlas, ya que aún conservan la capacidad de canjear AP.**

![](../.gitbook/assets/bpsqxxr.png)

3\. Visita la ruta de minería de la aplicación e ingresa tu nota usada, es posible que te enfrentes a una de las siguientes situaciones.

* **La capacidad de reclamar tu nota usada**: haz clic en el botón "Claim reward" y envía la transacción, ya sea mediante el uso de un repetidor o no, una vez confirmado, tu saldo de AP debería actualizarse para reflejar la acción.

![](../.gitbook/assets/e9jyqhu.png)

* **La imposibilidad de reclamar una nota usada:** _“Warning: The note is not yet ready for anonymity mining. You can wait few days before trying again”, traducido “Advertencia: La nota aún no está lista para la minería de anonimato. Puedes esperar unos días antes de volver a intentarlo”_: esto significa que los árboles de Merkle no están sincronizados y requieren una transacción para actualizarse.

![](../.gitbook/assets/i6qtr0f.png)

Actualizar los árboles puede ser un proceso costoso, **se recomienda que los usuarios con pequeños depósitos que esperen a que los mineros más grandes actualicen los árboles, esto podría llevar desde unos pocos días hasta una semana**. Si deseas ver tu evento en relación con los lotes pendientes actuales, haz clic en el hipervínculo _“show mining note information”_, aquí también puedes pagar las tarifas de transacción para sincronizar el árbol relativo a tu retiro a través del botón “Update trees”.

![](../.gitbook/assets/d8dmxjj.png)

### Cómo intercambiar AP

1\. Navega a la pestaña "Swap" en la página de minería a la que se puede acceder a través de la segunda barra de navegación desde la parte superior de la página.

![](../.gitbook/assets/ahrjxbq.png)

2\. Ingresa la cantidad de AP solicitada para cambiar o selecciona la opción “Maximum”, "Máximo", para convertir tu saldo activo. Debajo de esta entrada, se mostrará información sobre la tasa AP/TORN actual y la recompensa de salida. Proporciona una dirección de preferencia para recibir la recompensa, finaliza generando la prueba y enviando la transacción a través de un repetidor o no.

![](../.gitbook/assets/wo55lao.png)

3\. Si todos los pasos fueron seguidos correctamente, el TORN será transferido a la dirección de preferencia proporcionada en el paso 2 de esta sección.

### Comentarios de cierre

¡Felicidades , participaste con éxito en la minería de anonimato!

Siempre se recomienda planificar al decidir minar cualquiera de los pools de anonimato, los usuarios también deben ser conscientes de que la [tasa AP/TORN](https://duneanalytics.com/luckyallocator/Daily-AP-TORN-Rate-v2) depende de la oferta y la demanda, por lo tanto, **cuanta más gente reclama, más alta se vuelve la tasa, y cuantas menos personas reclaman, más baja se vuelve**.

Para obtener más información sobre la minería de anonimato, revisa los siguientes recursos:

* [Artículo de propuesta de gobernanza de Tornado.Cash](https://tornado-cash.medium.com/tornado-cash-governance-proposal-a55c5c7d0703)
* [Artículo de optimización de minería de anonimato de Tornado.Cash](https://tornado-cash.medium.com/gas-price-claimed-anonymity-mining-a-victim-but-now-everyone-can-claim-ap-5441aaa32a1a)
* [Minería de anonimato explicada (ártico técnico)](https://torn.community/t/anonymity-mining-technical-overview/15)

_Saludos a_ [_@sockawoo_](https://torn.community/u/sockawoo) _y_ [_@ethdev_](https://torn.community/u/ethdev) _por asistir en el "peer-reviewing"_

_Escrito por_ [_**@xgozzy**_](https://torn.community/u/xgozzy/summary)__
