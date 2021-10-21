# Управління проектом

### Як запропонувати пропозицію ?

Для участі в управлінні Tornado.Cash користувачам спочатку потрібно заблокувати токени в контракті управління. Якщо користувач голосує або створює пропозицію, токени не можна розблокувати до закінчення періоду виконання пропозиції \(8,25 днів з моменту створення пропозиції\). Заблоковані токени також можна делегувати на іншу адресу.

Щоб створити пропозицію, користувачеві необхідно мати принаймні `1000 TORN`. Усі пропозиції мають бути смарт-контрактами з перевіреним кодом, які виконуються з [контратку управління](https://etherscan.io/address/0x5efda50f22d34F262c29268506C5Fa42cB56A1Ce) \ (за допомогою `delegatecall`\). Таким чином, легко перевірити та перевірити будь-які зміни в контрактах.

Період голосування за пропозицію - 3 дні. Пропозиція буде успішною, якщо вона набере більшість голосів і загальна кількість голосів не менше 25 000 токенів TORN \(якщо явка надто низька, пропозиція автоматично провалиться\).

Після приняття пропозиції, на неї почне поширюватися часове блокування в 2 дні. Після спливання цього часу будь-який користувач може імплементувати пропозицію \(яка ініціює зміни\). Якщо пропозиція не виконується протягом 3 днів після цього, вона вважається _просроченним_ і більше не може бути виконана.

Усі ці початкові параметри відносно прості, оскільки на початковому етапі не буде багато токенів TORN в обігу. Але зі зростанням пропозиції в обігу токенів TORN, керівництво може коригувати ці порогові значення.

Пропозиція може мати такий характер:

* Додавання нового пулу Tornado Cash у проксі
* Зміна параметрів ставок винагород AP
* Поновити/призупинити токен TORN
* Зміна деяких основних майнінг-контрактів, таких як контракт `TornadoTrees`
* Поєднання всього перерахованого вище

І ще багато чого можна зробити. Щоб точно дізнатися, що можна змінити за допомогою управління в протоколі, шукайте функції з модифікатором `onlyGovernance` у смарт-контрактах.

Функції управління представлені червоною стрілкою на [цій схемі архітектури.](https://viewer.diagrams.net/?highlight=0000ff&edit=_blank&layers=1&nav=1&title=tornado-cash-contract-overview.drawio#Uhttps%3A%2F%2Fraw.githubusercontent.com%2FRezan-vm%2Ftornado-cash-edu%2Fmain%2Ftornado-cash-contract-overview.drawio)

ПРИМІТКА: Частини цієї статті були взяті з [цього засобу масової інформації.](https://tornado-cash.medium.com/tornado-cash-governance-proposal-a55c5c7d0703).

### Як голосувати?

Спочатку вам потрібно внести \(або заблокувати\) токени TORN в контракт управління.

Йдіть до: [https://app.tornado.cash/governance](https://app.tornado.cash/governance)

Натисніть `Manage` -&gt; `Lock Tab`

Підтвердіть контракт управління щоб передати ваші токени TORN, натиснувши кнопку «Затвердити». Як тільки підтвердження буде схвалене виберіть суму, яку ви хочете внести, і натисніть «Заблокувати». Підтвердьте транзакцію в гаманці та дочекайтеся підтвердження.

![](.gitbook/assets/c05e5a1813edad280544b627b24002dc8d5adcf2.png)

Before the vote, the next crucial step is to review the proposal.  
 Legitimate proposals should have a dedicated post on [Torn.community ](https://torn.community/)under the category “Proposal”. The forum post will provide additional context and arguments on the proposal. Read the thread and make your own mind on the issue.

Once a proposal was submitted it should appear on:  
[https://app.tornado.cash/governance](https://app.tornado.cash/governance)  
 Proposal are implemented in the form of a smart contract making changes to the system. It is therefore important to verify the address of the smart-contract and review its code. Find the address of the proposal contract here:

![](.gitbook/assets/181d612b6c57964bab59c8e5b766f5247211083d.png)

Look for the contract address on Etherscan and make sure that the source code is verified and readable.

![](.gitbook/assets/d2d37d169a94f09156e76fa522b7974cb7c9ac3f.png)

Read the source code and make sure that it matches what is described in the forum post.

If you are not technical or not comfortable to read Solidity code, get someone you trust to review the contract for you.

If you agree \(or disagree\) with the proposal code, it time to vote!

A proposal have a voting windows of 3 days. This means that we have 3 days to reach the vote quorum of 25k TORN.

Important: Once you voted, your tokens will be locked for 8.25 days from the moment the proposal was submitted \(the start of the 3 days voting period\). After the 8.25 you can withdraw your tokens from the governance contract. Note that you can vote on 2 proposal at the same time without incurring additional lockup period \(Only the most recently submitted proposal will matter for the 8.25 lockup\).

To vote, simply click on the Green check mark or the the red cross depending whether you accept or reject the proposal. Confirm the transaction with Metamask and your vote is in!

### How to delegate the vote ?

If you are a TORN token holder, you can delegate your voting power to someone else without having to send him the tokens.

IMPORTANT: If you delegate your tokens and that your delegate votes or initiate a proposal, your tokens will be locked for 8.25 days from the moment the proposal that the delegate voted on started. Note that that you can always undelegate at any time.

To achieve delegation, go to: [https://app.tornado.cash/governance](https://app.tornado.cash/governance)

You first need to lock your tokens in the governance contract. Click **`Manage`** -&gt; **`Lock`** tab

Approve the governance contract to transfer your TORN tokens by clicking on the **`Approve`** button. Once the approve is confirmed, chose the amount you want to delegate and click **`Lock`**. Confirm the transaction in your wallet and wait for the confirmation.

![](.gitbook/assets/c05e5a1813edad280544b627b24002dc8d5adcf2%20%281%29.png)

The last step, is to make the actual delegation. Go again to [https://app.tornado.cash/governance](https://app.tornado.cash/governance)

Click **`Manage`** -&gt; **`Delegate`** tab

Fill-in the address to which you want to delegate and click **`Delegate`**. Approve the transaction in your wallet and wait for confirmation.

![](.gitbook/assets/43c05d176d7f75a336af7a865565c9b23786b98c.png)

The totality of your locked balance will be delegated.

You can undelegate at anytime. To undelegate simply use the `Undelegate` Button in `Manage` -&gt; `Undelegate` Tab.



_Translated by_ [_**@chieftalion**_](https://torn.community/u/chieftalion/)

