# Uyumluluk Aracı

Tasarımı gereği, blockchainde her şey herkese açıktır ve bu da kullanıcıları gizlilik hakkından mahrum bırakabilir. Herkes, herkesin tüm işlem geçmişine erişebilir. Bu temel soruna yanıt olarak Tornado.Cash protokolü, kripto para birimi sahiplerinin gizliliklerini geri kazanmalarına ve anonimlik kazanmalarına olanak tanır. Aslında, kullanıcıların bir kaynak ve bir hedef adres arasındaki on-chain bağlantısını kesmesini sağlar.

Ancak, mahremiyeti ve finansal özgürlüğü korumak asla uyumsuzluk pahasına olmamalıdır. Gizlilik hakkı, sağladığımız bilgiler ve bu bilgileri kime sağladığımız üzerinde kontrol sahibi olabilme yeteneğinde yatmaktadır.

Bu kapsamda Tornado.Cash Uyum Aracı, kullanıcıların fonlarının kaynağını kanıtlamalarını sağlar. Her para yatırma işleminden sonra oluşturulan not sayesinde, varlıkları yatırmak ve çekmek için kullanılan Ethereum adresleri kullanılarak kriptografik olarak doğrulanmış bir işlem geçmişi kanıtı yayınlayacaktır.

Geliştirilmesi ve piyasaya sürülmesi hakkında daha fazla bilgi edinmek için bu araçla ilgili Medium gönderisini ziyaret edebilirsiniz: [Tornado.Cash uyumluluğu Medium Gönderisi.](https://tornado-cash.medium.com/tornado-cash-compliance-9abbf254a370)

Bu nedenle, Tornado.Cash havuzlarından birinden çekilen elde tutulan varlıkların kaynağını kanıtlamanız gerekirse sizi aşağıdaki Uyumluluk Aracını kullanmaya davet ediyoruz :

[https://app.tornado.cash/compliance/](https://app.tornado.cash/compliance/)

![](https://camo.githubusercontent.com/789d7bb233dac4435dcda067e8f9fc4cc89485a5251c28a0e8474e8e6fe7c394/68747470733a2f2f692e696d6775722e636f6d2f6c73646161574c2e706e67)

**Uyumluluk Aracı Nasıl Kullanılır?**

[Tornado.Cash](https://app.tornado.cash) uygulaması aracılığıyla yapılan her para yatırma işleminde protokol tarafından yeni bir not oluşturulur. Bu not, yatırılan varlıkları daha sonra herhangi bir para çekme adresinden çekmek için gereklidir. Aynı not, gerekirse, kullanıcıların varlıklarının kaynağını kanıtlamak için bir Uyumluluk Raporu oluşturmasına imkan sağlar.

_Tornado.Cash'te varlıkların nasıl yatırılacağı ve çekileceği hakkında daha fazla bilgiyi şu adreste bulabilirsiniz:_ [_Yatırma ve Çekme._](para-yatirma-ve-cekme.md)__

Bir Uyumluluk Raporu almak için kullanıcının yalnızca para yatırma işleminden sonra oluşturulan notu özel kutuya kopyalaması gerekir.

**Çekim Yapmadan Önce**

Not henüz harcanmadıysa (yani varlıklar hala çekilmediyse), Uyumluluk aracı size yalnızca depozito hakkında bilgi sağlayacaktır:

* Mevduatın işlem hash’i
* Kaynak adresi
* Taahhüt hash

Taahhüt, işlemi karakterize etmek için Tornado.Cash akıllı sözleşmesine gönderilen her depozitoda oluşturulan hash rastgele bayt alanıdır.

![](https://camo.githubusercontent.com/6e5655d8f440b6891d9413e92bf15970bb04313d0aaf380ad1d41ced279008c7/68747470733a2f2f692e696d6775722e636f6d2f395a416b4367472e706e67)

[Tornado.Cash nasıl çalışır?](../genel-bilgiler/how-does-tornado.cash-work.md) bölümünü okuyarak Tornado.Cash'in gizliliği nasıl sağladığı hakkında daha fazla bilgi bulabilirsiniz.

**Para Çekme Sonrası**

Not harcandıysa (yani varlıklar not kullanılarak belirli bir adrese çekildiyse), Uyumluluk Aracı yukarıdaki bilgileri aşağıdakileri ekleyerek tamamlayacaktır:

* Para çekme işleminin işlem hash’i;
* Varış adresi;
* Nullifier Hash.
* Nullifier hash, akıllı sözleşme ve para çekmeye izin vermek için Merkle Tree verileriyle kontrol edilmek üzere on-chain’de gönderilen genel bir girdidir.

![](https://camo.githubusercontent.com/24cd1dcd8ff45490821863b64d8e783c0c6c899b70f3f69beaf39341d2ac4704/68747470733a2f2f692e696d6775722e636f6d2f387031314f6e432e706e67)

Bu nedenle araç, Tornado.Cash'te kullanılan varlıklarda işlem geçmişini kanıtlamak için kullanıcıların kaynak ve hedef adreslerini yeniden bağlamasına olanak tanır.

Bu bilgiler ayrıca PDF formatında indirilebilir, bu da istenen herhangi bir üçüncü bölüme gönderilmesini kolaylaştırır:

![](https://camo.githubusercontent.com/e1c003b7a1db7cd3e4a947879478b6c0fb3e2259a1e280c852db1304b978fc0d/68747470733a2f2f692e696d6775722e636f6d2f494e506f676f632e706e67)

_Bu içerik_ [_@ayefda_](https://torn.community/u/ayefda) _tarafından yazılmıştır._

_Türkçe versiyonu için_ [_armog_](https://twitter.com/armogedd0n)_'a teşekkürler._
