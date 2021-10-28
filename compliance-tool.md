# Uyumluluk Aracı

Tasarımı gereği, blockchainde her şey herkese açıktır ve bu da kullanıcıları gizlilik hakkından mahrum bırakabilir. Herkes, herkesin tüm işlem geçmişine erişebilir. Bu temel soruna yanıt olarak Tornado.Cash protokolü, kripto para birimi sahiplerinin gizliliklerini geri kazanmalarına ve anonimlik kazanmalarına olanak tanır. Aslında, kullanıcıların bir kaynak ve bir hedef adres arasındaki on-chain bağlantısını kesmesini sağlar.

Ancak, mahremiyeti ve finansal özgürlüğü korumak asla uyumsuzluk pahasına olmamalıdır. Gizlilik hakkı, sağladığımız bilgiler ve bu bilgileri kime sağladığımız üzerinde kontrol sahibi olabilme yeteneğinde yatmaktadır.

**Bu kapsamda Tornado.Cash Uyum Aracı, kullanıcıların fonlarının kaynağını kanıtlamalarını sağlar. Her para yatırma işleminden sonra oluşturulan not sayesinde, varlıkları yatırmak ve çekmek için kullanılan Ethereum adresleri kullanılarak kriptografik olarak doğrulanmış bir işlem geçmişi kanıtı yayınlayacaktır.**

Geliştirilmesi ve piyasaya sürülmesi hakkında daha fazla bilgi edinmek için bu araçla ilgili Medium gönderisini ziyaret edebilirsiniz: [Tornado.Cash uyumluluğu Medium Gönderisi.](https://tornado-cash.medium.com/tornado-cash-compliance-9abbf254a370)

Bu nedenle, Tornado.Cash havuzlarından birinden çekilen elde tutulan varlıkların kaynağını kanıtlamanız gerekirse sizi aşağıdaki Uyumluluk Aracını kullanmaya davet ediyoruz :

[https://app.tornado.cash/compliance/](https://app.tornado.cash/compliance/)

![https://app.tornado.cash/compliance/](.gitbook/assets/capture-de-cran-2021-09-02-a-14.57.11.png)

## **Uyumluluk Aracı Nasıl Kullanılır?**

[Tornado.Cash](https://app.tornado.cash) uygulaması aracılığıyla yapılan her para yatırma işleminde protokol tarafından yeni bir not oluşturulur. Bu not, yatırılan varlıkları daha sonra herhangi bir para çekme adresinden çekmek için gereklidir. Aynı not, gerekirse, kullanıcıların varlıklarının kaynağını kanıtlamak için bir Uyumluluk Raporu oluşturmasına imkan sağlar.

_Tornado.Cash'te varlıkların nasıl yatırılacağı ve çekileceği hakkında daha fazla bilgiyi şu adreste bulabilirsiniz: _[_Yatırma ve Çekme._](untitled.md)

Bir Uyumluluk Raporu almak için kullanıcının yalnızca para yatırma işleminden sonra oluşturulan notu özel kutuya kopyalaması gerekir.

### **Çekim Yapmadan Önce**

Not henüz harcanmadıysa (yani varlıklar hala çekilmediyse), Uyumluluk aracı size yalnızca depozito hakkında bilgi sağlayacaktır:

* Mevduatın işlem hash’i
* Kaynak adresi
* Taahhüt hash

Taahhüt, işlemi karakterize etmek için Tornado.Cash akıllı sözleşmesine gönderilen her depozitoda oluşturulan hash rastgele bayt alanıdır.

![https://app.tornado.cash/compliance/](.gitbook/assets/capture-de-cran-2021-09-02-a-15.07.01.png)

[Tornado.Cash nasıl çalışır? ](https://docs.tornado.cash/v/tu/how-does-tornado.cash-work)bölümünü okuyarak Tornado.Cash'in gizliliği nasıl sağladığı hakkında daha fazla bilgi bulabilirsiniz.

**Para Çekme Sonrası**

Not harcandıysa (yani varlıklar not kullanılarak belirli bir adrese çekildiyse), Uyumluluk Aracı yukarıdaki bilgileri aşağıdakileri ekleyerek tamamlayacaktır:

* Para çekme işleminin işlem hash’i;
* Varış adresi;
* Nullifier Hash.
* Nullifier hash, akıllı sözleşme ve para çekmeye izin vermek için Merkle Tree verileriyle kontrol edilmek üzere on-chain’de gönderilen genel bir girdidir.

![https://app.tornado.cash/compliance/](.gitbook/assets/capture-de-cran-2021-09-02-a-15.12.23.png)

Bu nedenle araç, Tornado.Cash'te kullanılan varlıklarda işlem geçmişini kanıtlamak için kullanıcıların kaynak ve hedef adreslerini yeniden bağlamasına olanak tanır.

Bu bilgiler ayrıca PDF formatında indirilebilir, bu da istenen herhangi bir üçüncü bölüme gönderilmesini kolaylaştırır:

![https://app.tornado.cash/compliance/](.gitbook/assets/capture-de-cran-2021-09-02-a-15.12.53.png)

_Bu içerik _[_@ayefda_](https://torn.community/u/ayefda)_ tarafından yazılmıştır._\
_Türkçe versiyonu için _[_armog_](https://twitter.com/arm00g)_'a teşekkürler._
