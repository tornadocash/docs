# Cómo Retirar De Tornado Cash
Los usuarios pueden retirar sus tokens de la plataforma Tornado Cash en cualquier momento, pero para asegurar un nivel de privacidad alto se recomienda esperar hasta que haya algunos depósitos posteriores al suyo.
Para las retiradas, se requiere que los usuarios dispongan de:
- Note
- Dirección de recepción 
 
![withdraw button](https://siasky.net/IAA0oMfBCz3vPgANvIUsGBS84y4eC0DFgrbuVWVDwX5i9Q)

Rellene los detalles obligatorios. Obtendrá los detalles de ***Note*** de la transacción de depósito original.
Una vez haya cumplimentado los detalles de Note, los demás detalles sobre su depósito se mostrarán.

 ![withdraw details](https://siasky.net/TAB6fl4n3yj1f_cd59CzRUEap6QvaPe3fslWThwC6KWBlQ)

Desde la pestaña de configuración de Withdraw, usted puede escoger entre dos opción para la retirada:
- Via Relayer (usando un retransmisor)
- Web3 wallet (usando un monedero Web3 como Metamask)

Usted puede escoger el método de retirada ***Web3 wallet*** pero necesitará una direccion completamente nueva de Ethereum con algunos ETH en su balance. La obtencion de esos ETH podría eventualmente llevar a la perdida de anonimato.

  ![withdraw wallet](https://siasky.net/MACMuLY11IK0h2b1MON8k0gUjZHLNVqwDYdX5tW9-npAhw)
  
Por tanto, es recomendable escoger el metodo de retirada a traves de un ***Relayer***. Un relayer se usa para preservar la privacidad. Con la opción Relayer no hay manera de conectar las direcciones de ingreso y retirada.

  ![relayer](https://siasky.net/MAALGPo1Emw_K_-y6t6EaB6Ao--NPnSuIQfTfqI28qSUCw)
  
Cuando selecciona este metodo de retirada, se genera su prueba zk-SNARK.
La tecnología xk-SNARK es un método que ayuda a los usuarios a verificar que estos poseen la clave secreta relacionada con un ***commitment*** no gastado de los existentes en la lista de depósitos sin que se revele el depósito preciso asociado con dicha clave.

  ![confirmation](https://siasky.net/GADcmOqr30fMXl7neBtSR6knAzPg8x_4mxQtUt96dQSa1w)
  
Confirme el proceso.\
Usted ahora podrá ver los detalles de la transacción de retiro en la parte inferior.
Un aspecto interesante que notará es que la recompensa del usuario se incrementa constantemente.   

   ![final withdraw detail](https://siasky.net/KAAxcbm5QgjFr7mTKFqBU8uVKKNHKsaWz3-m85iQOP-6kg)
 
Para verificar el anonimato, clique en el hash de la transacción y compruebe la dirección ethereum que se menciona en el log.

 ![txn hash](https://siasky.net/DADzeQWIwr8CkZIRyLyUJTzs8kdve1kNlvOwwc6WBz8gqg)
 
Podrá facilmente comprobar que la dirección origen difiere de la dirección original de su monedero.
Adicionalmente, no hay detalles de la transacción en la dirección del monedero destino.

 ![metamask activity](https://siasky.net/VAAJZImmqf15RxJJp3nbgSrKUPaFpljsh6pQyvpxZavdIw)
 
Como buena práctica, se recomienda destruir el documento ***Note*** una vez haya finalizado el retiro de fondos exitosamente.
