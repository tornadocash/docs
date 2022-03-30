# Registre de relayer

Depuis l'exécution de la [10ème proposition de gouvernance](https://tornadocash.eth.link/governance/10), n'importe qui peut devenir un relayer pour les utilisateurs de Tornado Cash.

{% hint style="success" %}
La seule condition pour être inclus sur l'UI en tant que relayer est de détenir au minimum 300 TORN. Ce montant minimum peut à tout moment être changé par un vote de gouvernance.
{% endhint %}

Les relayers font partie intégrante de l'écosystème Tornado Cash. Ils permettent de régler le "dilemme du paiement de frais" : comment payer les frais d'un retrait de token venant d'une pool tout en gardant son anonymat ?

Les relayers paient donc les frais de transaction en ponctionnant directement une part du montant retiré par l'utilisateur. De plus, ils prennent un frais supplémentaire pour leur service.

Depuis la [10ème proposition de gouvernance](https://tornadocash.eth.link/governance/10), à chaque retrait utilisant les services d'un relayer, le protocole va collecter un frais directement sur la balance de tokens TORN verrouillés par le relayer sur le contrat `StakingReward`. Ce pourcentage de frais peut varier d'une pool à une autre et pourra se voir être modifié par un vote de gouvernance.

Il est fixé à 0.3% pour le moment. Certaines pools restent sans frais supplémentaires, soit car leurs montants sont trop bas pour y assigner un frais (0.1 ETH, 100 DAI/USDT, 1000 DAI/USDT), ou parce qu'il n'y a pas assez de liquidité sur Uni v3 (toutes les instances cDAI).

## Comment devenir un Relayer ?

N'importe qui peut devenir un relayer Tornado Cash en 6 étapes simples.

Vous trouverez ci-dessous toutes les informations nécessaires pour rejoindre le club des relayers.

### 1. Requis: Accepter les potentiels risques

Avant que vous proposiez vos services de relayer aux utilisateurs de Tornado Cash, vous devez comprendre et accepter les potentiels risques de devenir un relayer du protocole Tornado Cash.

### 2. Mettre en place le Relayer

La première étape est de lancer le logiciel de relayer Tornado Cash sur votre ordinateur. Chaque étape est [expliquée sur le github du protocole](https://github.com/tornadocash/tornado-relayer#deploy-with-docker-compose).

{% embed url="https://github.com/tornadocash/tornado-relayer#deploy-with-docker-compose" %}

Ensuite, vous allez devoir insérer votre URL dans l'emplacement dédié:

![](../.gitbook/assets/2.png)

### 3. Set Up ENS Subdomain

La prochaine étape consiste à:

* Créer un domaine ENS pour votre relayer,
* Mettre en place un sous-domain pour le mainnet,
* Ajouter un enregistrement TXT avec l'URL du Relayer pour le sous-domaine mainnet en respectant ce format ci-après:

#### Relayers Ethereum (Obligatoire)

| Enregistrement TXT      |
| ----------------------- |
| mainnet-tornado.xxx.eth |
| goerli-tornado.xxx.eth  |

#### **Relayers sur chaînes secondaires (Optionnel)**

Vous avez aussi la possibilité d'ajouter des sous-domaines avec un enregistrement TXT correspondant pour supporter d'autres chaînes qu'Ethereum. Les relayers de chaînes secondaires utilise une version différente du logiciel de Relayer. Toutes les instructions sont [ici](https://github.com/tornadocash/tornado-relayer/blob/light/README.md).

| Enregistrement TXT        |
| ------------------------- |
| bsc-tornado.xxx.eth       |
| gnosis-tornado.xxx.eth    |
| polygon-tornado.xxx.eth   |
| optimism-tornado.xxx.eth  |
| arbitrum-tornado.xxx.eth  |
| avalanche-tornado.xxx.eth |

#### Relayer Nova (Optionnel)

Tornado Cash Nova utilise sa propre version de logiciel de relayer. Si vous souhaitez devenir un relayer pour Tornado Cash Nova, vous trouverez les instructions [ici](https://github.com/tornadocash/tornado-pool-relayer#deploy-with-docker-compose).

| Enregistrement TXT  |
| ------------------- |
| gnosis-nova.xxx.eth |

![](../.gitbook/assets/3.png)

#### 4. Mise en place des Workers

Les _Workers_ sont des adresses qui vont permettre à votre relayer d'envoyer des preuves ZK -_ZK-proofs_- aux utilisateurs. Par défaut, le premier _Worker_ est l'adresse détentrice du domaine ENS.

Pour assurer un niveau supérieur de sécurité, nous vous conseillons de mettre en place plus d'un _Worker_.

Seul le mainnet requiert un enregistrement de _Workers_. Les autres chaînes ne le requièrent pas.

![](../.gitbook/assets/4.png)

#### 5. Stake

Avec l'implémentation d'un registre décentralisé de relayer, une condition de staking a été introduite pour être affiché sur l'UI Tornado Cash en tant que relayer.

En effet, **staker du TORN est maintenant obligatoire pour être listé sur la liste recommandée de relayers.**

Le montant minimum à stacker -verrouiller- est en ce moment fixé à **`300 TORN`**. Ce montant peut être changé par un vote de gouvernance à n'importe quel moment.

Quand un relayer est utilisé sur une pool Tornado Cash, un petit montant de TORN est automatiquement collecté de cette balance stakée par le relayer par le contrat `StakingReward`. Cet élément essentiel est à prendre en compte car les relayers devront garder une balance stakée supérieure ou égale à **`300 TORN`** s'ils souhaitent continuer à être listé sur l'UI Tornado Cash.

Ces frais sont par la suite distribués aux membres du DAO (les détenteurs de TORN qui ont verrouillés leurs TORN). Vous trouverez davantage d'informations sur la documentation [Staking](staking.md) et sur ce [post de forum](https://torn.community/t/proposal-relayer-registry-setting-parameters-after-audit/2134).

{% hint style="warning" %}
Votre balance de TORN n'est ni réclamable, ni remboursable.
{% endhint %}

![](../.gitbook/assets/5.png)

#### 6. Résumé: Dernières vérifications et enregistrements

Dernière étape et non des moindres: nous vous conseillons de **vérifier toutes les informations** présentes sur le résumé avant de cliquer sur `Register`.

![](../.gitbook/assets/6.png)

_Bienvenue dans la team des relayers! Grâce à vous, la vie privée est un peu plus respectée..._ 💚



Écrit par [_@bt11ba_](https://torn.community/u/bt11ba/) _&_ [_@ayefda_](https://torn.community/u/ayefda)

_Traduit par @erikA_
