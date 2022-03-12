# Nova’da Yatırma ve Çekim

Tornado Cash, kaynak ve hedef adresler arasındaki zincir üstü bağlantıyı keserek çalışır. Bunu yapmak için, protokolün tokenlarını bir adresten bir havuza yatırılması ve ardından başka bir adres aracılığıyla geri çekilmesi gerekir.

Bu ilke Tornado Cash Nova için aynı kalır. Geleneksel sabit miktar havuzlarına gelince, bu iki eylem, aracın verimliliğinin temelini oluşturur:

* “Fon Yatırma” süreci
* “Fon Çekme” süreci

## Fon Yatırma Süreci <a href="#fon-yatirma-suereci" id="fon-yatirma-suereci"></a>

Geleneksel Tornado Cash havuzlarına kıyasla en büyük yenilik, yatırılan tutarların artık önceden tanımlanmamasıdır. Kullanıcılar, cüzdan bakiyelerinin kapasitesi dahilinde kendi seçtikleri bir miktar yatırmayı seçebilirler.

Dolayısıyla havuza 0,4 ETH koymak istiyorsanız, geleneksel 0.1 ETH havuzu ile dört ayrı işlem yapmak yerine hepsini tek seferde yapabilirsiniz.

![](https://i.imgur.com/8HZYuJB.gif)

**Nasıl Çalışır?**

İlk Para Yatırma 💰

* İlk adım, bir Metamask hesabı aracılığıyla Tornado Cash Nova’da oturum açmaktır.
*   Hesabınız ayarları henüz uygun değilse (sağ üst köşede `Set Up Account` seçeneği mevcuttur). Hesabınızı kurmak için şunları yapabilirsiniz:

    `Set Up Account`’a tıklayın: oturum açmış olduğunuz adres, herhangi bir token yatırmanıza gerek kalmadan Nova’ya kaydedilecektir. Bu işlem, başka bir adresten havuz içindeki transferleri veya mevduatları almanızı sağlayacaktır.
* Alıcı adresi olarak oturum açtığınız adresinizi seçin: havuza token yatırarak hesabınız (korumalı adresi ve korumalı anahtarıyla) otomatik olarak oluşturulur. Yatırılan fonlar, korumalı bakiyenizi tamamlayacaktır.

Başka bir kayıtlı adres seçin: Tokenlar, seçilen alıcı adresinin korumalı bakiyesine eklenecektir. Bu alıcı adresinin, önceden havuza kayıtlı, korumalı bir adres olması gerekir.

Hesaba giriş yaptığınızda, `Recipient address` olarak giriş yaptığınız adresle işlem yaparsınız. Aracı nasıl kullanmak istediğinize bağlı olarak değiştirebilirsiniz.

Yeni bir hesap açarsanız, havuza daha sonra giriş yapabilir, Tornado korumalı bakiyenizi kontrol edebilir veya korumalı adresinizi veya korumalı anahtarınızı kullanarak korumalı transferler alabilirsiniz.

_Bu öğeleri oturum açmak için nasıl kullanacağınız veya korumalı anahtarınızı nerede bulacağınızla ilgili tüm bilgiler_ [_Tornado Cash Nova'da Oturum Açma_](tornado-cash-novada-oturum-acma.md) _sayfasında mevcuttur._

**Takip Eden Yatırma İşlemleri** 💸\
Tekrar para yatırma işlemi yaptığınızda, hesabın önceden ayarlanmış olması dışında, ilki ile aynı kurallara cevap verir.

Korumalı adresiniz/anahtarınız ile havuza giriş yaparak, seçtiğiniz korumalı adrese seçtiğiniz tutarları dilediğiniz gibi yatırabilirsiniz.

⚠️ Beta sürümü olduğu için şu anda para yatırma işlemi 1 ETH/işlem ile sınırlıdır.\
Ancak topluluk bu limiti artırmak isterse, 1 ETH üst sınırı her zaman bir yönetim teklifi yoluyla değiştirilebilir.

### Fon Çekme Süreci <a href="#fon-cekme-suereci" id="fon-cekme-suereci"></a>

![](https://i.imgur.com/6dnc9bg.gif)

Nova havuzundan para çekmek için şunları yapabilirsiniz:

* önceden belirlenmiş dört miktardan (0,1, 0,3, 0,5 ve 1 ETH) birini seçin,
* `Set custom` seçeneği ile tamamen özelleştirilmiş bir miktar belirleyin.

### Para Çekme için Özel Seçenekler <a href="#para-cekme-icin-oezel-secenekler" id="para-cekme-icin-oezel-secenekler"></a>

**Özel seçenek, yalnızca aşağıdaki gerçekler hakkında tam bilgi sahibi olarak ve eylemlerinize tamamen güvenerek seçilmelidir.**

Gizliliğinizi korumak için, para çekme işleminizin diğer işlemlere karışmasını sağlayacağından önerilen dört miktardan birini seçmeniz şiddetle tavsiye edilir.

Seçilen miktara bağlı olarak, aşağıdaki durumlarda ilk yatırma işleminiz ile para çekme işleminiz arasında bir bağlantı kurulabilir:

* başlangıçta yatırılan miktar ve çekilen miktar tamamen aynıdır,
* yatırılan ve çekilen miktarlar toplam miktar aracılığıyla kolayca ilişkilendirilebilir.

Örneğin, 0,42 ETH’lik bir yatırma işlemi tam olarak 0,42 ETH’nin veya iki kez 0,21 ETH’nin çekilmesiyle ilişkilendirilebilir ve bu da anonimliği tehlikeye atabilir. Bununla birlikte, 0,391 ETH’lik bir para çekme ile, 0,42 ve 0,391 miktarları arasında belirgin bir bağlantı olmadığı için gizlilik daha iyi korunur.

**Gnosis Zinciri Üzerinden Geçişler (L2)**\
Daha ucuz işlemler için, Layer-2 olarak Gnosis Zinciri (eski xDAI Zinciri) kullanılır. Bu amaçla, Mainnet’ten ETH ile Gnosis Zincirinden WETH arasında bir köprü kullanılır.

Köprüde aşırı yüklenmeye neden olacak spam saldırılarını önlemek için para çekme miktarının 0,05 ETH’den büyük olması gerekir.

[@ayefda\_\_ ](https://torn.community/u/ayefda)tarafından yazıldı. Türkçe versiyonu için Armog'a teşekkürler.
