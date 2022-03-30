# Dépôt et retrait sur Nova

Tornado Cash fonctionne en cassant le lien entre l'adresse source et l'adresse de destination. Pour cela, le protocole a besoin qu'une adresse dépose ses tokens dans une pool, puis qu'il les retire vers une autre adresse.

C'est le même principe pour Tornado Cash Nova. Comme pour les pools à montants fixes (Tornado Cash Classic), ce sont les deux actions principales permises par le protocole:

* Le processus de dépôt
* Le processus de retrait

## Processus de Dépôt <a href="#funding-process" id="funding-process"></a>

La nouveauté vis-à-vis des pools traditionnelles Tornado Cash Classic, est que Tornado Cash Nova permet de déposer des montants personnalisés. Les utilisateurs peuvent désormais choisir un montant arbitraire, dépendant des tokens disponibles dans leur wallet.

De ce fait, si vous souhaitez déposer 0.4 ETH dans la pool, vous pouvez le faire en une fois, au lieu de le faire 4 fois avec la traditionnelle pool de 0.1 ETH.

![](https://i.imgur.com/rqmzdgG.gif)

### Comment ça marche? <a href="#how-does-it-work" id="how-does-it-work"></a>

#### **Premier dépôt 💰**

* La première étape est de se connecter sur [Tornado Cash Nova](https://nova.tornadocash.eth.link) à travers un compte Metamask,
* Ensuite, il convient de mettre en place votre compte, grâce au bouton `Set up account` disponible en haut à droite. Pour le mettre en place, vous pouvez, au choix:&#x20;
  * **Cliquez sur `Set up account`**: votre adresse de wallet sera directement enregistrée sur Nova sans avoir besoin de déposer des tokens. Cette action va vous permettre de recevoir des transfert ou des dépôts d'une autre adresse.
  * **Choisir votre adresse comme adresse de reception:** en déposant des tokens dans la pool, votre compte (avec son adresse blindée et sa clé blindée) sera automatiquement créé. Les fonds déposés vont donc ajouter des fonds sur votre balance blindée.
  * **Choisir une autre adresse enregistrée:** les tokens seront ajouté à la balance blindée de cette adresse de réception. L'adresse de réception doit être une adresse blindée précédemment enregistrée à la pool.

Quand vous vous connectez, la `Recipient address` (adresse de réception) est remplie par défaut par votre adresse de connexion. Vous pouvez la changer si vous le souhaitez.

Si vous crééez un nouveau compte, vous serez capable de vous connecter à la pool plus tard, vérifier votre balance blindée ou recevoir des transferts blindés, soit en utilisant votre adresse blindée ou votre clé blindée.

Toutes les informations concernant la connexion ou comment disposer d'une clé blindée sont disponibles [**ici**](depot-et-retrait-sur-nova.md).

#### **Les dépôts suivants 💸**

Les dépôts suivants répondent aux mêmes règles que pour le premier dépôt, sauf pour un compte déjà créé.

En vous connectant à la pool avec votre adresse blindée/votre clé blindée, vous pouvez déposer le montant de votre choix.

⚠️ Tornado Cash Nova étant en version beta, les dépôts sont en ce moment limités à 1 ETH par transaction. Cependant, si la communauté souhaite augmenter la limite, le montant de 1 ETH peut être changé par une proposition de gouvernance.

## Processus de Retrait <a href="#withdrawing-process" id="withdrawing-process"></a>

![](https://i.imgur.com/qn9eJXS.gif)

Pour retirer les fonds de la pool Nova, vous pouvez au choix:

* Choisir un montant prédeterminé (0.1, 0.3, 0.5 ou 1 ETH),
* Choisir un montant arbitraire en utilisant le bouton `Set custom`.

### Options personnalissées pour les retraits <a href="#custom-option-for-withdrawal" id="custom-option-for-withdrawal"></a>

**L'option personnalisée doit être utilisée en comprenant ce que cela implique.**

Pour assurer votre confidentitalité, choisir un montant prédéterminé est fortement recommandé étant donné que cela va permettre de fondre votre retrait dans la masse.

En effet, si vous utilisez un montant personnalisé, sachez qu'une connexion pourrait être faites entre votre adresse de dépôt et votre adresse de retrait dans les cas suivants:

* Les montants de dépôts et les montants de retraits sont identiques,
* Les montants des différents retraits, additionnés, donnent la même somme que le montant de dépôt initial.

_Par exemple, un dépôt de 0.42 ETH peut être lié à un retrait d'exactement 0.42 ETH ou deux fois 0.21 ETH, ce qui pourrait compromettre l'anonymat. Cependant, avec un retrait de 0.391 ETH, la confidentitalité est davantage préservée, car il n'y a pas de lien direct entre les montants 0.42 ETH et 0.391 ETH._

### Transactions à travers la Gnosis Chain (L2) <a href="#transctions-through-gnosis-chain-l2" id="transctions-through-gnosis-chain-l2"></a>

Pour des transactions plus économiques, la chaîne Gnosis (anciennement xDAI Chain) est utilisé en Layer2. Pour cela, un pont est utilisé entre l'ETH original et les WETH de la chaîne Gnosis.

Pour éviter les attaques de spam risquant de mettre le pont en difficulté, le montant de retrait doit être supérieur à 0.05 ETH.

_Ecrit par_ [_@ayefda_](https://torn.community/u/ayefda)

_Traduit par @erikA_
