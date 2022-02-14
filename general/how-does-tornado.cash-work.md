# ¿Cómo funciona Tornado Cash?

Antes de sumergirse en los tutoriales que explican y facilitan el uso de Tornado.Cash, aquí hay una descripción general del funcionamiento global del protocolo.

### Resumen global del funcionamiento de Tornado.Cash

Para lograr privacidad, Tornado.Cash **utiliza contratos inteligentes que aceptan depósitos de tokens desde una dirección y permiten su retiro desde una dirección diferente**. Esos contratos inteligentes funcionan como pools que mezclan todos los activos depositados.&#x20;

Una vez que los fondos son retirados de esas pools por una dirección completamente nueva, se rompe el vínculo en la blockchain entre el origen y el destino. Por lo tanto, los criptoactivos retirados se anonimizan.&#x20;

Mientras los tokens están en un pool de Tornado Cash, la custodia permanece en manos de los usuarios. Los usuarios, en consecuencia, tienen control completo sobre sus tokens.

**Para pools tradicionales de monto fijo de Tornado Cash**:

* Cuando un usuario deposita fondos en un pool (el depósito), se genera una nota privada. Esta nota privada funciona como una clave privada para que el usuario acceda a esos fondos más adelante. Para retirarlos, el usuario puede usar una dirección diferente, una antigua o una nueva, y recuperar sus fondos gracias a esta clave privada.

**Para Tornado Cash Nova, el nuevo pool de ETH con montos arbitrarios y transferencias protegidas**:

* Los fondos están directamente vinculados a una dirección de billetera determinada. No hay nota o clave privada. Los usuarios pueden acceder a sus fondos conectándose al pool con la dirección adecuada.
* La custodia se adquiere mediante el acto de depositar tokens en el pool o registrándose en el pool y recibiendo transferencias protegidas desde otra dirección.

La fuerza de dicho protocolo proviene naturalmente de su número de usuarios y el tamaño de su pool. Cuantos más usuarios depositen en el pool, mejor. Sin embargo, para preservar la privacidad y el anonimato, el usuario debe tener en cuenta algunas reglas básicas, tales como:

* Utilizar un "relayer" (repetidor) para pagar el gas en el retiro;
* Dejando un lapso de tiempo entre el depósito y la acción de retiro;
* Mezclar los fondos con la multitud esperando varias transacciones antes de recuperar los activos.

_Se proporcionan más recomendaciones en:_ [_Consejos para permanecer anónimo_](tips-to-remain-anonymous.md)_._

### Contribución de zk-SNARK y proceso de hashing

Tornado.Cash utiliza un "Zero-Knowledge Succinct Non-Interactive Argument of Knowledge" (argumento de conocimiento sucinto no interactivo de conocimiento cero) (también llamado zk-SNARK) para verificar y permitir transacciones.

Para procesar un depósito, Tornado.Cash genera un área aleatoria de bytes, lo calcula a través del [Hash de Pederson](https://iden3-docs.readthedocs.io/en/latest/iden3\_repos/research/publications/zkproof-standards-workshop-2/pedersen-hash/pedersen.html) (ya que es amistoso con zk-SNARK), luego envía el token y el hash de 20 mimc al contrato inteligente. El contrato finalmente lo insertará en el árbol de Merkle.

Para procesar un retiro, la misma área de bytes se divide en dos partes separadas: el **secreto** en un lado y el **anulador** en el otro lado. El anulador es encriptado. Este anulador es una entrada pública que se envía en la blockchain para que se verifique con el contrato inteligente y los datos del árbol de Merkle. Evita que se gaste el doble, por ejemplo.

Gracias a zk-SNARK, es posible probar el hash de 20 mimc del compromiso inicial y del anulador sin revelar ninguna información. Incluso si el anulador es público, la privacidad se mantiene, ya que no hay forma de vincular el anulador con hash al compromiso inicial. Además, incluso si la información de que la transacción está presente en la raíz de Merkle es pública, la información sobre la ruta exacta de Merkle y la ubicación de la transacción, se siguen manteniendo privada.

Los depósitos son simples desde un punto de vista tecnológico, pero costosos en términos de gas, ya que necesitan calcular el hash de 20 mimc y actualizar el árbol de Merkle. Por el contrario, el proceso de retiro es complejo, pero más económico ya que solo se necesita gas para el hash anulador y el "zero-knowledge proof" (la prueba de conocimiento cero) .

_Escrito y editado por_ [_@ayefda_](https://torn.community/u/ayefda)__