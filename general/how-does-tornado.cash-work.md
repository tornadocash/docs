# Comment Tornado.Cash fonctionne?

Avant de se lancer dans des tutoriels spécifiques expliquant et facilitant l'utilisation de Tornado.Cash, voici un aperçu général du fonctionnement du protocole.

### Aperçu global du fonctionnement de Tornado.Cash

Pour assurer la confidentialité, Tornado.Cash utilise des **contrats intelligents qui acceptent les dépôts de tokens depuis une adresse et permettent leur retrait depuis une autre adresse**. Ces contrats intelligents fonctionnent comme des pools qui mélangent tous les actifs déposés.

Une fois que les fonds sont retirés de ces pools par une toute nouvelle adresse, le lien sur la chaîne entre la source et la destination est rompu. Les crypto-actifs retirés sont donc anonymisés.

#### **Pour Tornado Cash Classic, pools à montants fixes**

Lorsqu'un utilisateur met des fonds dans un pool (c'est-à-dire le dépôt), une note privée est générée. Cette note privée fonctionne comme une clé privée permettant à l'utilisateur d'accéder ultérieurement à ces fonds. Pour les retirer, le même utilisateur peut utiliser une adresse différente - une ancienne ou une nouvelle - et récupérer ses fonds grâce à cette clé privée.

#### **Pour Tornado Cash Nova, pools à montants arbitraires et transferts **_**shielded**_

* Les fonds sont directement liés à l'adresse du _wallet_ préalablement indiqué. Il n'y a pas de note ou de clé privée. Les utilisateurs peuvent accéder à leurs fonds en se connectant à la pool avec l'adresse _wallet_ appropriée.
* La propriété est acquérie soit par le fait de déposer les tokens dans la pool, soit en s'enregistrant à la pool ou en recevant un transfert shielded depuis une autre adresse de _wallet_.

La force d'un tel protocole vient naturellement de son nombre d'utilisateurs et de la taille de sa réserve. Plus il y a d'utilisateurs qui déposent des fonds dans la réserve, plus ils sont nombreux. Cependant, pour préserver sa confidentialité et so, anonymat, l'utilisateur doit garder à l'esprit quelques règles de base telles que :

* Utiliser un relais pour payer les frais de gazs - _gas fee_ lors du retrait,
* Laisser un maximum de temps entre le dépôt et le retrait.

_Davantage de recommandations sur :_ [_Conseils pour rester anonyme_](tips-to-remain-anonymous.md)_._

### L'apport du zk-SNARK & du processus de hash

Tornado.Cash utilise le Zero-Knowledge Succinct Non-Interactive Argument of Knowledge (également appelé zk-SNARK) pour vérifier et autoriser les transactions.

Pour traiter un dépôt, Tornado.Cash génère une zone aléatoire d'octets, la calcule par le biais du [hachage Pederson](how-does-tornado.cash-work.md#global-overview-of-tornado.cash-functioning), puis envoie le jeton et le hachage 20 mimc au contrat intelligent. Le contrat l'insère alors dans le Merkle tree.

Pour traiter un retrait, la même zone d'octets est divisée en deux parties distinctes : le **secret** d'un côté et le **nullifier** de l'autre. Le nullifier est haché. Ce nullifier est une entrée publique qui est envoyée sur la chaîne pour être vérifiée avec le contrat intelligent et les données du Merkle tree. Cela permet d'éviter la problématique de doubles dépenses, par exemple.

Grâce à zk-SNARK, il est possible de prouver le hachage 20 mimc d'engagement initial ainsi que du nullifier sans révéler aucune information. Même si le nullifier est public, la confidentialité est maintenue car il n'y a aucun moyen de relier le hashed-nullifier à l'engagement initial. En outre, même si l'information selon laquelle la transaction est présente dans la Merkle-root, l'information sur le Merkle-path exact ainsi que la localisation de la transaction, reste anonyme.

Les dépôts sont simples d'un point de vue technologique, mais coûteux en termes de gaz car il faut calculer le hash 20 mimc et mettre à jour le Merkle tree. À l'inverse, le processus de retrait est complexe, mais moins coûteux car le gaz n'est nécessaire que pour le hachage du nullifier et la zk-SNARK proof.

Écrit par __ [_@ayefda_](https://torn.community/u/ayefda)_._

Traduit par @erikA
