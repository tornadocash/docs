# Outil de conformité

Par conception, tout est public sur la blockchain, ce qui peut priver les utilisateurs de leur droit à la vie privée. N'importe qui peut avoir accès à l'ensemble de l'historique des transactions de chacun. En réponse à ce problème central, le protocole Tornado.Cash permet aux détenteurs de crypto-monnaies de regagner leur vie privée et de gagner en anonymat. En effet, il permet aux utilisateurs de rompre le lien on-chain entre une adresse source et une adresse de destination.

Cependant, le maintien de la vie privée et la préservation de la liberté financière ne devraient jamais se faire au détriment de la non-conformité. Le droit à la vie privée réside dans la possibilité de contrôler les informations que nous fournissons et à qui nous les fournissons.

Dans cette mesure, l'**outil de conformité Tornado.Cash** **permet aux utilisateurs de prouver l'origine de leurs fonds**. Grâce à la note générée après chaque dépôt, **cet outil émettra une preuve cryptographiquement vérifiée de l'historique des transactions** en utilisant les adresses Ethereum utilisées pour déposer et retirer les actifs.

Vous pouvez visiter le Medium Post relatif à cet outil pour en savoir plus sur son développement et son lancement : [Article Medium relatif au lancement de l'outil de conformité.](compliance-tool.md#how-to-use-the-compliance-tool)

Par conséquent, si vous avez un jour besoin de prouver l'origine des actifs détenus retirés d'un des pools Tornado.Cash, nous vous invitons à utiliser l'[outil de conformité ](compliance-tool.md#how-to-use-the-compliance-tool)suivant:

![https://app.tornado.cash/compliance/](<../.gitbook/assets/Capture d’écran 2021-09-02 à 14.57.11.png>)

## Comment utiliser l'outil de conformité?

A chaque dépôt effectué par [l'application Tornado.Cash](https://app.tornado.cash), une nouvelle note est générée par le protocole. Cette note est nécessaire pour retirer les actifs déposés ultérieurement. C'est cette même note qui permet aux utilisateurs de générer un rapport de conformité pour prouver l'origine de leurs actifs.

Plus d'informations sur la façon de déposer et retirer des actifs sur Tornado.Cash sur : [Dépôt & Retrait](deposit-withdraw.md).&#x20;

Pour obtenir un rapport de conformité, l'utilisateur doit uniquement copier la note, générée après le dépôt, dans la case prévue à cet effet.

### Avant le retrait

Si la note n'a pas encore été dépensée (c'est-à-dire que les actifs n'ont pas encore été retirés de Tornado.Cash), l'outil de conformité vous fournira uniquement des informations sur le dépôt :&#x20;

* Le hachage de transaction du dépôt;
* L'adresse de la source;
* Le hachage de l'engagement.

L'engagement est la zone aléatoire hachée d'octets générée à chaque dépôt qui est envoyée au contrat intelligent Tornado.Cash pour caractériser la transaction.

![https://app.tornado.cash/compliance/](<../.gitbook/assets/Capture d’écran 2021-09-02 à 15.07.01.png>)

_Vous trouverez davantage d'information sur comment Tornado.Cash fonctionne_ [_ici_](../general/how-does-tornado.cash-work.md)_._

### Après le retrait

Si la note a été dépensé (c'est-à-dire que des actifs ont été retirés à une adresse donnée en utilisant la note), l'outil de conformité complétera les informations ci-dessus en ajoutant :

* Le hachage de transaction du retrait;
* L'adresse de destination;
* Le hachage de nullité;

Le hachage _nullifier_ est une entrée publique qui est envoyée sur la chaîne pour être vérifiée avec le contrat intelligent et les données de l'arbre de Merkle (Merkle tree) pour autoriser le retrait.

![https://app.tornado.cash/compliance/](<../.gitbook/assets/Capture d’écran 2021-09-02 à 15.12.23.png>)

Par conséquent, l'outil permet aux utilisateurs de relier les adresses de source et de destination afin de prouver l'historique des transactions pour les actifs utilisés sur Tornado.Cash. Ces informations peuvent également être téléchargées au format PDF, ce qui facilite leur envoi à un tier:

![https://app.tornado.cash/compliance/](<../.gitbook/assets/Capture d’écran 2021-09-02 à 15.12.53.png>)

_Écrit par_ [_@ayefda_](https://torn.community/u/ayefda)__

_Traduit par @erikA_
