# Інструмент відповідності

За задумом, у блокчейні все публічно, що може позбавити користувачів права на конфіденційність. Будь-хто може мати доступ до всієї історії транзакцій ,будь-кого. У відповідь на цю основну проблему протокол Tornado.Cash дозволяє власникам криптовалюти повернути свою конфіденційність і отримати анонімність. Справді, це дає змогу користувачам розірвати ланцюжковий зв’язок між адресою джерела та адресою призначення.

Однак збереження конфіденційності та фінансової свободи ніколи не повинно відбуватися за рахунок недотримання законів. Право конфіденційності полягає в можливості контролювати інформацію, яку ми надаємо, і тим, кому ми її надаємо. 

Таким чином, **Tornado.Cash Compliance Tool дозволяє користувачам підтвердити походження своїх коштів.** Завдяки нотатці (Note), яка створюється після кожного депозиту, **цей інструмент видасть криптографічно перевірений доказ історії транзакцій** за допомогою Ethereum адреси, які використовуються для внесення та виведення активів.

Ви можете відвідати публікацію Medium, пов'язану з цим інструментом, щоб дізнатися більше про його розробку та запуск: [**Tornado.Cash compliance Medium Post**](https://tornado-cash.medium.com/tornado-cash-compliance-9abbf254a370).

Тому, якщо вам коли-небудь знадобиться довести походження утримуваних активів, вилучених з одного з пулів Tornado.Cash, ми пропонуємо вам скористатися наступним [Інструментом відповідності](https://app.tornado.cash/compliance/):

![https://app.tornado.cash/compliance/](.gitbook/assets/capture-de-cran-2021-09-02-a-14.57.11.png)

## Як користуватися інструментом відповідності?

З кожним депозитом, внесеним через [додаток Tornado.Cash](https://app.tornado.cash/), протокол генерує нову примітку. Ця Нотатка (Note) необхідна для вилучення депонованих активів пізніше за будь-якою адресою виведення. Це саме та Нотатка (Note), що при необхідності дозволяє користувачам формувати Звіт про відповідність, щоб довести походження своїх активів.

_Докладніше про те, як депонувати та вилучати активи на Tornado.Cash доступно на:_ [_Депозит та зняття_](untitled.md)_._

Щоб отримати звіт про відповідність вимогам, користувачеві потрібно лише вставити Нотатку (Note), створену після депозиту, у спеціальне поле.

### Перед виведенням

Якщо Облігація ще не була витрачена \(тобто активи ще не були вилучені\),  інструмент відповідності надасть вам лише інформацію про депозит:

* Хеш операції депозиту;
* Адреса джерела;
* Хеш зобов’язань.

Зобов'язання - це хешована випадкова область байтів, створена при кожному депозиті, що надсилається на смарт-контракт Tornado.Cash для створення характеристики транзакції.

![https://app.tornado.cash/compliance/](.gitbook/assets/capture-de-cran-2021-09-02-a-15.07.01.png)

_Ви можете дізнатися більше про те, як Tornado.Cash досягає конфіденційності, прочитавши_ [_Як працює Tornado.Cash?_](how-does-tornado.cash-work.md)\_\_

### After Withdrawal

If the Note was spent \(i.e. assets were withdrawn to a given address using the Note\), the Compliance Tool will complete the information above by adding: 

* Transaction hash of the withdrawal;
* The destination address;
* The Nullifier Hash.

The nullifier hash is a public input that is sent on-chain to get checked with the smart contract & the Merkle tree data to allow the withdrawal.

![https://app.tornado.cash/compliance/](.gitbook/assets/capture-de-cran-2021-09-02-a-15.12.23.png)

Therefore, the tool allows users to re-link source & destination addresses in order to prove transaction history for assets used on Tornado.Cash.

This information can also be downloaded under a PDF format, making it is easier to get sent to any desired third part:

![https://app.tornado.cash/compliance/](.gitbook/assets/capture-de-cran-2021-09-02-a-15.12.53.png)

_Translated by_ [_**@chieftalion**_](https://torn.community/u/chieftalion/)

