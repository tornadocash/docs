# Yönetişim

Aşağıdaki yönetim kuralları, tüm Tornado Cash havuzları için geçerlidir (Tornado Cash Nova dahil).

### Teklif nasıl yapılır?

Tornado.Cash yönetimine katılmak için, kullanıcıların öncelikle yönetişim sözleşmesine tokenlarını kilitlemesi gerekir. Bir kullanıcı bir teklifi oylarsa veya oluşturursa, teklif yürütme süresi sona ermeden (teklif oluşturma tarihinden itibaren 8,25 gün) tokenların kilidi açılamaz. Kilitli tokenlar başka bir adrese de devredilebilir.

Bir teklif oluşturmak için bir kullanıcının en az `1,000 TORN`a sahip olması gerekir. Tüm teklifler, [yönetişim sözleşmesinden](https://etherscan.io/address/0x5efda50f22d34F262c29268506C5Fa42cB56A1Ce)(`delegatecall` kullanılarak) yürütülen, doğrulanmış koda sahip akıllı sözleşmeler olmalıdır. Bu şekilde, herhangi bir yönetim değişikliğini denetlemek ve test etmek kolaydır.

Bir teklif için oylama süresi 5 gündür. Bir teklif, oyların basit çoğunluğunu alırsa ve toplamda en az \`25,000 TORN TORN oy kullanılırsa başarılı olacaktır (katılım çok düşükse teklif otomatik olarak başarısız olur).

Bir teklif başarılı olduktan sonra 2 günlük bir süreye tabidir. Zaman kilidinden sonra, herhangi bir kullanıcı teklifi (değişiklikleri başlatan) yürütebilir. Bu tarihten sonra 3 gün boyunca teklif yürütülmezse _süresi dolmuş_ kabul edilir ve artık yürütülemez.

Başlangıç parametrelerinin tümü nispeten küçüktür çünkü dolaşımda erken dönemde çok fazla TORN olmayacaktır. Ancak dolaşımdaki arz arttıkça yönetim bu eşikleri ayarlayabilir.

Bir teklif aşağıdaki nitelikte olabilir::

* Proxy’ye yeni bir Tornado Cash havuzu ekleme
* AP ödül oranları parametrelerini değiştirme
* TORN tokenını durdurma/durdurmama
* `TornadoTrees` sözleşmesi gibi bazı temel madencilik sözleşmelerini değiştirme
* Yukarıdakilerin hepsinin bir kombinasyonu

Ve daha pek çok şey yapılabilir. Protokolde yönetişim yoluyla tam olarak nelerin değiştirilebileceğini öğrenmek için akıllı sözleşmelerde `onlyGovernance` değiştiricisine sahip işlevleri arayın.

Yönetim fonksiyonları kırmızı okla temsil edilir. Detaylar için Tornado.Cash [mimarisi diyagramını](https://viewer.diagrams.net/?highlight=0000ff\&edit=\_blank\&layers=1\&nav=1\&title=tornado-cash-contract-overview.drawio#Uhttps%3A%2F%2Fraw.githubusercontent.com%2FRezan-vm%2Ftornado-cash-edu%2Fmain%2Ftornado-cash-contract-overview.drawio) inceleyin.

NOT: Bu makalenin bölümleri [bu medium içeriğinden](https://tornado-cash.medium.com/tornado-cash-governance-proposal-a55c5c7d0703) alınmıştır. Alkışlar Tornado Cash ekibine!

### Nasıl oy verilir?

Önce TORN tokenları yönetişim sözleşmesine yatırmanız (veya kilitlemeniz) gerekir.

[https://app.tornado.cash/governance](https://app.tornado.cash/governance) adresine girin

`Manage` -> `Lock Tab` tıklayın

`Approve` Approve butonuna tıklayarak TORN tokenlarınızı aktarmak için yönetim sözleşmesini onaylayın. Onayladıktan sonra yatırmak istediğiniz tutarı seçin ve `Lock`’a tıklayın. Cüzdanınızdaki işlemi onaylayın ve onay için bekleyin

![](https://github.com/0xarmagan/docs/raw/tr/.gitbook/assets/c05e5a1813edad280544b627b24002dc8d5adcf2.png)

Oylamadan önce, bir sonraki önemli adım teklifi gözden geçirin. Meşru tekliflerin [Torn.community ](https://torn.community)’de “Teklif” kategorisi altında özel bir gönderisi olmalıdır. Forum gönderisi, teklifle ilgili ek bağlam ve argümanlar sağlayacaktır. Konuyu okuyun ve konu hakkında kendi kararınızı verin.

Bir teklif gönderildikten sonra şu adreste görünmelidir: [https://app.tornado.cash/governance](https://app.tornado.cash/governance)\
Teklif, sistemde değişiklik yapan akıllı bir sözleşme şeklinde uygulanır. Bu nedenle akıllı sözleşmenin adresini doğrulamak ve kodunu gözden geçirmek önemlidir. Teklif sözleşmesinin adresini burada bulabilirsiniz:

![](https://github.com/0xarmagan/docs/raw/tr/.gitbook/assets/181d612b6c57964bab59c8e5b766f5247211083d.png)

Etherscan’de sözleşme adresini aratın ve kaynak kodunun doğrulanmış ve okunabilir olduğundan emin olun.

![](https://github.com/0xarmagan/docs/raw/tr/.gitbook/assets/d2d37d169a94f09156e76fa522b7974cb7c9ac3f.png)

Kaynak kodunu okuyun ve forum gönderisinde açıklananla eşleştiğinden emin olun.

Teknik biri değilseniz veya Solidity kodunu okuyamıyorsanız güvendiğiniz birinden sözleşmeyi sizin için gözden geçirmesini isteyin.

Teklif koduna katılıyorsanız (veya katılmıyorsanız) oy verme zamanı!

Bir teklifin 3 günlük oylama aralığı vardır. Bu, 25k TORN oy yeter sayısına ulaşmak için 3 günümüz olduğu anlamına geliyor.

Önemli: Oy verdikten sonra, tokenlarınız teklifin sunulduğu andan itibaren (8,25 gün boyunca) (3 günlük oylama döneminin başlangıcı) kilitlenecektir. 8.25’ten sonra tokenlarınızı yönetim sözleşmesinden çekebilirsiniz. Ek kilitleme süresine maruz kalmadan aynı anda 2 teklife oy verebileceğinizi unutmayın (8.25 kilitleme için yalnızca en son gönderilen teklif önemli olacaktır).

Oy vermek için, teklifi kabul edip etmemenize bağlı olarak Yeşil onay işaretine veya kırmızı çarpıya tıklamanız yeterlidir. İşlemi Metamask ile onaylayın ve oyunuzu kullanın!

### Oy nasıl delege edilir?

Eğer bir TORN tokenı sahibiyseniz, tokenları göndermek zorunda kalmadan oylama gücünüzü başka birine devredebilirsiniz.

ÖNEMLİ: Tokenlarınızı devrederseniz, temsilcinizin oy kullandığı veya bir öneri başlattığı takdirde tokenlarınız, temsilcinin oy verdiği teklifin başladığı andan itibaren 8.25 gün boyunca kilitlenir. İstediğiniz zaman yetki devrini geri alabileceğinizi unutmayın.

Yetki vermek için şu adrese gidin: [https://app.tornado.cash/governance](https://app.tornado.cash/governance)

Öncelikle yönetim sözleşmesinde tokenlarınızı kilitlemeniz gerekir. Tıklayın **`Manage`** -> **`Lock`** tab

**`Approve`**'a tıklayarak TORN tokenlarınızı aktarmak için yönetim sözleşmesini onaylayın. Onayladıktan sonra, devretmek istediğiniz tutarı seçin ve `Lock`’a tıklayın. Cüzdanınızdaki işlemi onaylayın ve onay için bekleyin.

![](https://github.com/0xarmagan/docs/raw/tr/.gitbook/assets/c05e5a1813edad280544b627b24002dc8d5adcf2%20\(1\).png)

Son adım, fiili delegasyonun yapılmasıdır. [https://app.tornado.cash/governance](https://app.tornado.cash/governance) adresine tekrar gidin.

**`Manage`** -> **`Delegate`** kısmına tıklayın

Yetki vermek istediğiniz adresi girin ve `Delegate`’e tıklayın. Cüzdanınızdaki işlemi onaylayın ve onay için bekleyin

![](https://github.com/0xarmagan/docs/raw/tr/.gitbook/assets/43c05d176d7f75a336af7a865565c9b23786b98c.png)

Kilitli bakiyenizin tamamı devredilecektir.

İstediğiniz zaman yetki devrini iptal edebilirsiniz. Yetkiyi geri almak için, `Manage` -> `Undelegate` kısmına gidin ve `Undelegate`e tıklayın.

_Bu metnin yazarı_ [_@rezan_](https://torn.community/u/Rezan/summary) _güncelleyen_ [_@bt11ba_](https://torn.community/u/bt11ba/)_'dır. Türkçe versiyonu için_ [_armog_](https://twitter.com/armogedd0n)_'a teşekkürler._
