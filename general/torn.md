# TORN

## Token

TORN es un token compatible con ERC20 con un suministro fijo que rige [Tornado.Cash](https://tornado.cash). Los poseedores de TORN pueden hacer propuestas y votar para cambiar el protocolo a través de gobernanza.

**TORN no es una app de recaudación de fondos ni una oportunidad de inversión.**

**Así es como se dividiría la distribución inicial de TORN:**

* **5% (500,000 TORN):** Airdrop a los primeros usuarios de las pools de ETH en [Tornado.Cash](https://tornado.cash)
* **10% (1,000,000 TORN):** Minería de anonimato para [Tornado.Cash](https://tornado.cash) pools de ETH, distribuidos linealmente durante 1 año
* **55% (5,500,000 TORN):** Tesorería de la DAO, se desbloqueará linealmente durante 5 años con un "cliff" (período de gracia o tiempo de espera) de 3 meses
* **30% (3,000,000 TORN):** Para los desarrolladores fundadores y los primeros seguidores, se desbloquearán linealmente durante 3 años con un "cliff" (período de gracia o tiempo de espera) de 1 año

![](../.gitbook/assets/1-bjggju1rn4\_qoxgcljfneq.png)

![](../.gitbook/assets/1-gmc0jw8zr5xfvrk5zyqmya.png)

## Airdrop <a href="#f04d" id="f04d"></a>

Los usuarios que creyeron en [Tornado.Cash](https://tornado.cash) desde el principio deberían tener poder de gobernanza en el protocolo. Por esta razón, los primeros usuarios del protocolo recibieron un airdrop de TORN.

Se ha hecho un airdrop de TORN a [todas las billeteras](https://github.com/tornadocash/airdrop/blob/master/airdrop.csv) que hicieron depósitos en el pool de ETH en [Tornado.Cash](https://tornado.cash) antes del bloque `11400000`. Los TORN se repartieron mediante un airdrop en forma de un cupón TORN no transferible (vTORN) que se puede canjear 1:1 a TORN en el periodo de 1 año, desde el 18 de diciembre de 2020 hasta el 18 de diciembre de 2021. Los TORN que no se canjean serán enviados al contrato de gobernanza después de 1 año y pasarán a formar parte de la Tesorería de la DAO. El TORN canjeado estará disponible de inmediato.

La cantidad repartida en el airdrop depende del tamaño y la antigüedad del depósito de los usuarios: los depósitos más grandes y los depósitos más antiguos recibirán más TORN. Los multiplicadores para el tamaño del depósito son logarítmicos:

![](../.gitbook/assets/1-ogfrad8p3gez14zh4jndiq-2x.png)

Entonces, un depósito de 100 ETH obtiene el doble de tokens que un depósito de 1 ETH. El multiplicador permite que ambos, tanto los usuarios grandes y pequeños de [Tornado.Cash](https://tornado.cash) tengan voz en la gobernanza.

La curva exacta para el multiplicador de tiempo se ve así:

![](../.gitbook/assets/1-bje88nlnkbe29-zcs5agkw-2x.png)

La fórmula exacta del airdrop es la siguiente:

![](../.gitbook/assets/1-megm4amqrrkx0qxva9iska-2x.png)

_Escrito por_ [_**El equipo de Tornado**_](https://tornado-cash.medium.com/tornado-cash-governance-proposal-a55c5c7d0703)