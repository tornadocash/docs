# Introduction à Tornado.Cash

![](.gitbook/assets/image.png)

Tornado Cash est un protocole non custodial entièrement décentralisé permettant des transactions anonymisées. En tant que protocole décentralisé, les contrats intelligents Tornado.Cash ont été mis en œuvre au sein de la blockchain Ethereum, ce qui les rend immuables. Ils ne peuvent être ni modifiés ni altérés. Par conséquent, personne - y compris les développeurs initiaux - ne peuvent les modifier ou mettre fin à leur fonctionnement. Tous les contrats intelligents de gouvernance et de minage sont déployés par la communauté de manière décentralisée. En tant que protocole sans custodial, les utilisateurs conservent la propriété de leurs crypto-monnaies lorsqu'ils utilisent Tornado.Cash. En effet, à chaque dépôt, ils reçoivent une clé privée permettant d'accéder aux fonds déposés, ce qui donne aux utilisateurs un contrôle total sur leurs actifs.

## Comment la confidentialitée est assurée?

Tornado Cash améliore la confidentialité des transactions en rompant le lien entre l'adresse de dépôt et l'adresse de retrait. Le protocole utilise un contrat intelligent qui accepte les dépôts d'ETH et d'autres tokens depuis une adresse et permet leur retrait depuis une autre adresse. Pour préserver la confidentialité, quelques bonnes pratiques sont de mise, tout comme l'utilisation d'un relais pour le paiement des _gas fee_ afin de retirer des fonds vers une adresse sans solde préexistant. Plus de détails sont disponibles ici : [Comment Tornado.Cash fonctionne? ](general/how-does-tornado.cash-work.md)& [Conseils pour rester anonyme](general/tips-to-remain-anonymous.md).

## Où en est Tornado.Cash?

Le protocole fonctionne sur la blockchain Ethereum depuis sa création en 2019. Il a récemment été déployé, en juin 2021, sur Binance Smart Chain, Polygon, xDai ainsi qu'Avalanche.

À ce jour, Tornado.Cash peut être utilisé avec les tokens suivants :

* Sur la blockchain Ethereum : **ETH** _(Ethereum)_, **DAI** _(Dai)_, **cDAI** _(Compound Dai)_, **USDC** _(USD Coin)_, **USDT** _(Tether)_ & **WBTC** _(Wrapped Bitcoin)_
* Sur la Binance Smart Chain: **BNB** _(Binance Coin)_.
* Sur Polygon Network: **MATIC** _(Polygon)_
* Sur la blockchain xDai : **XDAI** (_Stake_)
* Sur la blockchain Avalanche : **AVAX**

![](<.gitbook/assets/Non-custodial anonymous transactions on Ethereum (3) (1).png>)

Le protocole comprend également un système de minage d'anonymat pour certains de ses tokens, permettant à ses utilisateurs de gagner un token de gouvernance. Grâce aux jetons TORN, les utilisateurs de Tornado Cash participent activement à l'élaboration du protocole. La communauté a un poids important concernant l'évolution de Tornado Cash et l'amélioration des outils proposés. En effet, les paramètres du protocole et la distribution des tokens sont entièrement sous le contrôle de la communauté grâce à cette gouvernance.

Plus d'informations concernant le [minage d'anonymat ](tornado-cash-classic/anonymity-mining.md)& le [token TORN](general/torn.md) sont disponibles.

### Tornado Cash Nova

Avec la [sortie de Tornado Cash Nova (version beta) en Décembre 2021](https://tornado-cash.medium.com/tornado-cash-introduces-arbitrary-amounts-shielded-transfers-8df92d93c37c), une **pool avec de nouvelles fonctionnalités** a été ajoutée au protocole. Les utilisateurs ne sont plus contraints aux transactions à montant fixes. Avec Tornado Cash Nova, ces derniers peuvent bénéficier de l'usage des **pools à montants arbitraires et des transferts **_**shielded**_.

Tornado Cash Nova opère sur la Gnosis Chain (_Layer2_) - anciennement xDai Chain - afin d'optimiser la rapidité et les gas fee. Nova permet de **déposer et de retirer des montants personnalisés en ETH**. La pool dispose par ailleurs d'un système de transactions _shielded,_ où les utilisateurs peuvent **transférer la propriété de leur tokens sans qu'il faille les sortir de la pool**.

Tornado Cash Nova (version beta) est accessible sur [nova.tornadocash.eth.link](https://nova.tornadocash.eth.link). Vous trouverez davantage d'information relatives au fonctionnement de Tornado Cash Nova ici:

* [Se connecter à Tornado Cash Nova](tornado-cash-nova/se-connecter-a-tornado-cash-nova.md),
* [Dépôt et retrait sur Nova](tornado-cash-nova/depot-et-retrait-sur-nova.md#custom-option-for-withdrawal),
* [Transferts blindés sur Nova](tornado-cash-nova/transferts-blindes-sur-nova.md),
* [Garantir sa vie privée sur Tornado Cash Nova](tornado-cash-nova/garantir-sa-vie-privee-sur-tornado-cash-nova.md).

## Tornado.Cash - Quésaco?

[Les codes derrière le fonctionnement de Tornado.Cash](./#how-does-tornado.cash-run) - c'est-à-dire les contrats intelligents, les circuits et les outils _onchain_ sont 100% open-source. Fonctionnant comme un DAO (Organisation autonome décentralisée - Decentralized Autonomous Organization), la gouvernance Tornado.Cash et les contrats intelligents de minage d'anonymat sont déployés par la communauté Tornado.Cash.

Le protocole fonctionne avec zk-SNARK, qui permet d'établir des arguments de connaissance non interactif succinct de zéro connaissance (zero-knowledge proofs), permettant aux utilisateurs de démontrer la possession d'informations sans avoir besoin de révéler ces informations. L'utilisation de cette technologie est basée sur des ressources open source mise à disposition par l'équipe Zcash avec l'aide de la communauté Ethereum. Pour inititier les clés zk-SNARK, la communauté Tornado.Cash a effectué un [Trusted Setup Community](https://tornado-cash.medium.com/tornado-cash-trusted-setup-ceremony-b846e1e00be1) en mai 2020 et a compté [1114 contributions](https://tornado-cash.medium.com/the-biggest-trusted-setup-ceremony-in-the-world-3c6ab9c8fffa). Ce nombre important de contributeurs rend impossible la compromission du protocole en falsifiant les zero-knowledge proof. L'interface de l'outil Tornado.Cash est hébergée sur IPFS (InterPlanetary File System) par la communauté, ce qui minimise la possibilité que l'outil soit hors ligne. En effet, l'interface fonctionnera tant qu'au moins un utilisateur l'hébergera.

_Ecrit par_ [_@ayefda_](https://torn.community/u/ayefda)_._

_Traduit par @erikA_
