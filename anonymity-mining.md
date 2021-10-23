# Майнінг анонімності

Видобуток анонімності-це стимул для підвищення рівня конфіденційності в будь-яких протоколах приєднання або змішування монет, винагороджуючи учасників балами анонімності \(AP\) залежно від того, як довго вони тримають свої активи в пулі.

_Цей інструмент почав діяти 18 грудня 2020 року і закінчить свою дію 18 грудня 2021 року._

Учасники вносять депозит у будь-який із підтримуваних пулів анонімності (ETH, WBTC, DAI або cDAI) і отримують фіксовану кількість очків AP для кожного блоку протягом усього періоду, поки їх депозит залишається в пуле. Ці бали можна обміняти на токени TORN.

### Очки анонімності \(AP\)

_Читачі повинні знати, що деякі депозити нижчого номіналу на момент написання статті не приносять позитивного прибутку через витрати на газ, необхідні для вилучення, викупу та обміну балів анонімності_

Один із членів спільноти створив ресурс у вигляді [електронна майнінг таблиця 13](https://torn.community/t/anonymity-mining-spreadsheet/720) який допоможе розрахувати річну процентну доходність \(APY’s\) для кожного пула та кожного номінального засобу, встановленого в них, шляхом отримання комісійних, необхідних для визнання. **Настійно рекомендується переглянути цей ресурс і спланувати свої дії,перш ніж розраховувати доходність.** У нижній частині електронної таблиці можна переглянути кожен пул, вибравши відповідну вкладку.

### Як заробити AP

1. Вирішіть, яку суму та актив покласти на депозит, вибравши їх у спадному меню, перш ніж натискати "Connect" та "Deposit".

![](.gitbook/assets/m3fh0gl.png)

2. Запишіть свою депозитну нотатку (Note) та зебережіть її в безпечному місці,**не повідомляйте її нікому,в іншому випадку ви ризикуєте втратити свій депозит та винагороду.**

![](.gitbook/assets/vhustru.png)

3. Створіть доказ та відправьте транзакцію.

4. Тепер ваш депозит повинен відображатись у нижній частині сторінки, тут ви можете відстежувати, скільки AP він заробляє; пам’ятайте, чим довше ваш депозит залишається активним, тим більше AP ви заробляєте.

![](.gitbook/assets/k6juetp.png)

_Активні нотатки (Note) \(не вилучені\) відомі як "unspent" (невитрачені) нотатки (Note)._

### Як отримати AP

1. Спочатку ви повинні створити початковий запис для майнинга та зберегти ці початкові дані в мережі блокчейн для легкого відновлення \(потрібно провести транзакцію\), **Як і в разі отримання приватної записки при внесенні депозиту - ви ніколи і никому не повинні передавати свій ключ для відновлення майнінг-аккаунта** і обов'язково зберігати його в надійному місці. Ця функція не підтримує аппаратними кошельками, тому рекомендується зберігати інформацію у представленому вигляді_._

![](.gitbook/assets/lskzkgk.png)

2. Введіть активний депозит, надавши невитрачену нотатку (Note) та виводьте засоби на бажану адресу гаманця та вирішивши, використовувати ретранслятор чи ні\(_для збереження анонімності депозиту завжди рекомендується використовувати ретранслятор_\), після цього записка стане "витраченою".

![](.gitbook/assets/aid86cj.png)

**Не забувайте зберігати в таємниці свої депозитні нотатки (Note) навіть після зняття, оскільки вони все ще зберігають можливість викупити AP.**

![](.gitbook/assets/bpsqxxr.png)

3. Visit the mining route of the application and enter your spent note, you may be faced with one of the following situations.

* **The ability to claim your spent note**: click the “Claim reward” button and submitting the transaction either by using a relayer or not, once confirmed your AP balance should update to reflect the action.

![](.gitbook/assets/e9jyqhu.png)

 

* **The inability to claim a spent note:** _“Warning: The note is not yet ready for anonymity mining. You can wait few days before trying again”_ - This means the Merkle trees are out of sync and require a transaction to be updated.

![](.gitbook/assets/i6qtr0f.png)

Updating the trees can be an expensive process, **it is recommended that users with small deposits wait for the larger miners to update the trees, this could take anywhere from a few days to a week**. If you want to view your event relative to the current pending batches. Click the _“Show mining note information”_ hyperlink, here you can also pay the transaction fees to sync the tree relative to your withdrawal through the “Update trees” button.

![](.gitbook/assets/d8dmxjj.png)

### How to exchange AP

1. Navigate over to the “Swap” tab on the mining page which can be accessed through the second navigation bar from the top of the page.

![](.gitbook/assets/ahrjxbq.png)

2. Enter the amount of AP requested to exchange or select the “Maximum” option to convert your active balance. Below this input, information regarding the current AP/TORN rate and reward output will be displayed. Provide an address of preference to receive the reward, finalise by generating the proof and submitting the transaction through a relayer or not.

![](.gitbook/assets/wo55lao.png)

3. If all steps were followed correctly, TORN will be transferred to the address of preference provided in step 2 of this section.

### Closing remarks

Congratulations, you have successfully participated in anonymity mining!

It is always recommended to plan when deciding to mine any of the anonymity sets, users should also be aware that the [AP/TORN rate](https://duneanalytics.com/luckyallocator/Daily-AP-TORN-Rate-v2) is dependent on supply and demand, therefore, **the more people that claim the higher the rate becomes, and the less people that claim the lower it becomes**.

For more information on anonymity mining, seek the following resources:

* [Tornado.Cash governance proposal article](https://tornado-cash.medium.com/tornado-cash-governance-proposal-a55c5c7d0703)
* [Tornado.Cash anonymity mining optimisation article](https://tornado-cash.medium.com/gas-price-claimed-anonymity-mining-a-victim-but-now-everyone-can-claim-ap-5441aaa32a1a) 
* [Anonymity mining explained \(technical\)](https://torn.community/t/anonymity-mining-technical-overview/15)

_Regards to_ [_@sockawoo_](https://torn.community/u/sockawoo) _and_ [_@ethdev_](https://torn.community/u/ethdev) _for assisting in peer-reviewing_

_Translated by_ [_**@chieftalion**_](https://torn.community/u/chieftalion/)

