# Garantir sa vie privée sur Tornado Cash Nova

Pour cette section, nous vous référons à la documentation comme première étape.

Tous les points mentionnés dans cette dernière s'appliquent à Tornado Cash Nova.

A titre de rappel, voici de quoi cette documentation parle :

* Utilisez un VPN,
* Ne partagez pas votre clé blindée,
* Si vous téléchargez la clé blindée, gardez la en lieu sûr,
* Supprimez vos données après utilisation de Tornado Cash,
* Evitez l'usage du même token API à chaque transaction,
* Soyez patients entre le moment de dépôt et le moment de retrait,
* Utilisez plusieurs adresses pour vos retraits.

Cependant, avec ces nouvelles fonctionnalités, Tornado Cash Nova requiert d'autres précautions pour préserver votre anonymat.

## Usage de Relayers <a href="#use-of-relayers" id="use-of-relayers"></a>

Le paiement de frais de gas sont nécessaires pour pouvoir effectuer des transactions. Pour les transferts et retraits blindés, deux méthodes de paiements sont disponibles pour fournir des ETH afin de payer les frais de gas. Vous pouvez, au choix, **connecter votre wallet OU utilisez les services d'un relayer**.

Utiliser votre wallet pour payer les frais peut compromettre votre anonymat si les ETH utilisés pour payer les frais peuvent être liés à votre adresse de dépôt/votre identité. De ce fait, il est **recommandé d'utiliser les services d'un relayer pour préserver votre anonymat**.

![Tips1](https://i.imgur.com/PsZ89Ym.png)

## Choix d'un montant de retrait <a href="#choice-of-withdrawal-amounts" id="choice-of-withdrawal-amounts"></a>

La fonctionnalité permettant le choix d'un montant de retrait personnalisé offre une certaine flexibilité et une liberté d'usage. Cependant, cette dernière peut compromettre anonymat si elle est utilisée n'importe comment.

### Choisir un montant prédéfini pour le retrait <a href="#choosing-predefined-amounts-for-withdrawals" id="choosing-predefined-amounts-for-withdrawals"></a>

![Tips2](https://i.imgur.com/dKYvNQT.png)

Pour assurer votre confidentitalité, choisir un des 4 montants prédéterminés est fortement recommandé étant donné que cela va permettre de fondre votre retrait dans la masse.

Vous avez toujours le choix d'utiliser un montant prédéfini grâce à l'option `Set custom` pour retirer un montant personnalisé de votre choix.



En effet, si vous utilisez un montant personnalisé, sachez qu'une connexion pourrait être faites entre votre adresse de dépôt et votre adresse de retrait dans les cas suivants:

* Les montants de dépôts et les montants de retraits sont identiques,
* Les montants des différents retraits, additionnés, donnent la même somme que le montant de dépôt initial.

_Par exemple, un dépôt de 0.42 ETH peut être lié à un retrait d'exactement 0.42 ETH ou deux fois 0.21 ETH, ce qui pourrait compromettre l'anonymat. Cependant, avec un retrait de 0.391 ETH, la confidentitalité est davantage préservée, car il n'y a pas de lien direct entre les montants 0.42 ETH et 0.391 ETH._

Le retrait personnalisé doit être utilisé en toute connaissance de cause, étant donné l'impact que cette option peut avoir sur votre confidentialité dans le cas où l'utilisateur ne fait pas attention.

_Ecrit par_ [_@ayefda_](https://torn.community/u/ayefda)

_Traduit par @erikA_
