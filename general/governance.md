# Gouvernance

Les règles de gouvernance ci-dessous s'applique autant pour Tornado Cash Classic que pour Tornado Cash Nova.

### Comment suggérer une proposition ?

Afin de participer à la gouvernance de Tornado.Cash, les utilisateurs doivent d'abord verrouiller leurs TORN tokens dans le contrat de gouvernance. Si un utilisateur vote ou crée une proposition, les jetons ne peuvent pas être déverrouillés avant la fin de la période d'exécution de la proposition (8,25 jours à partir de la création de la proposition). Les tokens verrouillés peuvent également être délégués à une autre adresse.

Pour créer une proposition, un utilisateur doit disposer d'au moins 1 000 TORN. Toutes les propositions doivent être des smart contracts avec du code vérifié qui sont exécutés à partir du contrat de gouvernance (en utilisant delegatecall). De cette façon, il est facile de vérifier et de tester tout changement de gouvernance.

La période de vote pour une proposition est de 3 jours. Une proposition sera acceptée si elle reçoit une majorité simple de votes et s'il y a au moins 25 000 votes TORN au total (si la participation est trop faible, la proposition échoue automatiquement).

Une fois qu'une proposition est acceptée, elle est soumise à une période de blocage de 2 jours. Après ce délai, n'importe quel utilisateur peut exécuter la proposition (ce qui déclenche les modifications). Si la proposition n'est pas exécutée pendant 3 jours, elle est considérée comme expirée et ne peut plus être exécutée.

Tous ces paramètres initiaux sont relativement faibles, car il n'y aura pas beaucoup de jetons TORN en circulation au début. Mais à mesure que l'offre en circulation augmente, la gouvernance peut ajuster ces seuils.

Une proposition peut être de différentes natures:

* Ajouter une nouvelle pool de liquidité au proxy Tornado Cash
* Ajouter/Changer le montant des récompenses AP pour une/des pool(s)
* Mettre sur PAUSE le token TORN
* Changer certains contrats de minage comme celui des contrats `TornadoTrees`

Beaucoup plus pourrait être fait. Pour voir ce qui peut être changé à travers la gouvernance, jetez un oeil aux ofnctions avec le modificateur `onlyGovernance` dans le contrat intelligent.

Les fonctions de gouvernance sont représentés par une flèche rouge dans [le diagrame d'architecture.](https://viewer.diagrams.net/?highlight=0000ff\&edit=\_blank\&layers=1\&nav=1\&title=tornado-cash-contract-overview.drawio#Uhttps%3A%2F%2Fraw.githubusercontent.com%2FRezan-vm%2Ftornado-cash-edu%2Fmain%2Ftornado-cash-contract-overview.drawio)

### Comment voter?

Vous devez d'abord bloquer vos TORN tokens dans le contrat de gouvernance.

Allez ici: [https://tornadocash.eth.link/governance](https://tornadocash.eth.link/governance)

Cliquez sur `Manage` -> `Lock Tab`

Approuvez le contrat de gouvernance pour transférer vos tokens TORN en cliquant sur le bouton `Approve`. Une fois confirmé, choisissez le montant que vous souhaitez déposer et cliquez sur  `Lock`. Confirmez la transaction dans votre portefeuille et attendez la confirmation.

![](../.gitbook/assets/c05e5a1813edad280544b627b24002dc8d5adcf2.png)

Avant le vote, l'étape cruciale est de vérifier la proposition.

Une proposition légitime devrait avoir un post sur [Torn.community](https://torn) dans la catégorie `Proposal` .\
Le post devra expliquer de manière détaillée le contexte de cette proposition, son but et les arguments liés à sa potentielle mise en place. Faites votre propre avis sur le post et sur le code source de la proposition.

Une fois que la proposition est proposée, elle apparaît ici:\
[https://tornadocash.eth.link/governance](https://tornadocash.eth.link/governance)\


Les propositions sont implémentées sous la forme de contrats intelligents, modifiant le système. Il est extrêmemnt important de vérifier l'adresse du contrat intelligent ainsi que son code. Vous trouverez l'adresse du contrat intelligent ici:

![](../.gitbook/assets/181d612b6c57964bab59c8e5b766f5247211083d.png)

Vérifiez l'adresse du contrat sur Etherscan et soyez sûr que le code source est vérifié et lisible.

![](../.gitbook/assets/d2d37d169a94f09156e76fa522b7974cb7c9ac3f.png)

Lisez le code source et assurez-vous qu'il correspond à ce qui est décrit dans le post du forum. Si vous n'êtes pas à l'aise pour lire le code Solidity, demandez à une personne de confiance de relire le contrat pour vous.

Si vous êtes d'accord (ou non) avec le code de la proposition, il est temps de voter !&#x20;

Une proposition a une fenêtre de vote de 3 jours. Cela signifie que la proposition dispose de 3 jours pour atteindre le quorum de vote de 25,000 TORN.

Important : Une fois que vous avez voté, vos jetons seront bloqués pendant 8,25 jours à partir du moment où la proposition a été soumise (le début de la période de vote de 3 jours). Après les 8,25 jours, vous pourrez retirer vos jetons du contrat de gouvernance.

Notez que vous pouvez voter sur 2 propositions en même temps sans encourir de période de blocage supplémentaire (seule la proposition la plus récemment soumise comptera pour le blocage de 8,25).

Pour voter, cliquez simplement sur la coche verte ou la croix rouge selon que vous acceptez ou rejetez la proposition. Confirmez la transaction avec Metamask et votre vote est enregistré !

### Comment déléguer votre vote?

Si vous êtes détenteur de tokens TORN, vous pouvez déléguer votre pouvoir de vote à une autre personne sans avoir à lui envoyer les jetons.

IMPORTANT : Si vous déléguez vos jetons et que votre délégué vote ou initie une proposition, vos tokens seront bloqués pendant 8,25 jours à partir du moment où la proposition sur laquelle le délégué a voté a commencé. Notez que vous pouvez toujours annuler votre délégation à tout moment.

Pour déléguer, rendez-vous ici: [https://tornadocash.eth.link/governance](https://tornadocash.eth.link/governance)

Vous devrez d'abord bloquer vos tokens dans le contrat de gouvernance. Cliquez ici :  **`Manage`** -> **`Lock`**

Approuvez le contrat de gouvernance en transférant vos TORN en cliquant sur le bouton **`Approve`**. Une fois que c'est confirmé, choisissez le montant que vous souhaitez déléguer et cliquez sur**`Lock`**. Confirmez la transaction dans votre portefeuille et attendez la confirmation.

![](<../.gitbook/assets/c05e5a1813edad280544b627b24002dc8d5adcf2 (1).png>)

La dernière étape nécessite de déléguer. Rendez-vous encore une fois ici: [https://tornadocash.eth.link/governance](https://tornadocash.eth.link/governance)

Cliquez sur **`Manage`** -> **`Delegate`**

Remplissez l'adresse à laquelle vous souhaitez déléguer vos droits de vote et cliquez sur **`Delegate`**. Approuvez la transaction sur votre wallet.

![](../.gitbook/assets/43c05d176d7f75a336af7a865565c9b23786b98c.png)

La totalité de votre balance bloquée sera déléguée.

Vous pouvez retirer à n'importe quel moment. Pour cela, cliquez sur le bouton`Undelegate` dans `Manage` -> `Undelegate`.

_Ecrit par_ [_@rezan_](https://torn.community/u/Rezan/summary)_._

Traduit par @erikA
