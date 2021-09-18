# Cómo funciona Tornado.Cash?

**\[Trabajo en curso\]**

Antes de sumergirnos en tutoriales que explican el uso de Tornado.Cash, aqui recopilamos una visión global de la funcionalidad del protocolo.

### Visión global de funcionalidad de Tornado.Cash

Para conseguir privacidad, Tornado.Cash **utiliza smart contracts que aceptan depósitos de tokens desde una dirección y habilita su retirada desde una dirección diferente**. Estos smart contracts trabajan como pools que mezclan todos los activos depositados.

Una vez los fondos son retirados por una dirección completamente nueva de dichas pools, el nexo en cadena entre el origen y el destino se rompe. En consecuencia, el retiro de los cryptoactivos resulta anónimo. 

Cuando un usuario añade fondos a una pool \(a.k.a. el depósito\), se genera una nota privada. Esta nota privada funciona como una clave privada y proporciona al usuario la capacidad de acceder a los fondos posteriormente. Para retirar lso fondos, el mismo usuario puede usar una dirección diferente - antigua o nueva - y recuperar sus fondos mediante esta clave privada.

La fortaleza del protocolo esta ligada naturalmente al número de usuarios y el tamaño de la pool. Como mas usuarios depositen en la pool mejor. No obstante, para preservar la privacidad y el anonimato, el usuario debe tener en cuenta una serie de reglas básicas:

* Dejar un tiempo entre las acciones de depósito y el retiro de fondos.
* Mezclar sus fondos con los demás esperando varias transacciones antes de recuperar sus activos. 

_Mas recomendaciones en:_ [_Tips to remain anonymous_](tips-to-remain-anonymous.md)_._

### Contribución de los zk-SNARK y el proceso de hashing

Tornado.Cash utiliza Zero-Knowledge Succinct Non-Interactive Argument of Knowledge \(abreviado zk-SNARK\) para verificar y permitir transacciones.

Para procesar un depósito, Tornado.Cash genera una area aleatoria de bytes, los procesa con un [Pederson Hash](https://iden3-docs.readthedocs.io/en/latest/iden3_repos/research/publications/zkproof-standards-workshop-2/pedersen-hash/pedersen.html) \(más adecuado para zk-SNARK\), envía el token y la 20 mimc hash al smart contract. El contrato lo inserta entonces en un árbol de Merkle \(a.k.a. Merkle tree\).

Para procesar un retiro, la misma área de bytes se divide en dos partes separadas: el **secret** por un lado y el **nullifier** por el otro. Al nullifier se le aplica un hash. Este nullifier es una parámetro público que se envia on-chain para ser verificado con el smart contract y los datos en el árbol de Merkle. Por ejemplo, impide el doble gasto.

Gracias a los zk-SNARK, es posible probar el 20 mimc hash del commitment inicial y el nullifier sin revelar ninguna información. Incluso si el nullifier es público, la privacidad se mantiene ya que no hay manera de conectar el hash del nullifier con el commitment inicial. Además, incluso si transciende que la información de la transacción esta presente en la raíz del árbol de Merkle, la información del directorio exacto en el árbol de Merkle, es decir, la localización de la transacción, se mantiene la privada.

Los depósitos son simples desde el punto de vista técnico, pero costosos en términos de gas, ya que necesitan procesar el 20 mimc hash y actualizar el árbol de Merkle. Opuestamente, el retiro es un proceso complejo, pero menos costoso ya únicamente se necesita gas para el hash del nullifier y la zero-knowledge proof.

_Escrito por_ [_@ayefda_](https://torn.community/u/ayefda)\
_Traducido por_ [_@EeXavi_](https://twitter.com/EeXavi?s=09)

