# Daha Fazla Anonim Kalma İpuçları

Bu bölüm için, ilk adım olarak sizi [Anonim Kalma İpuçları ](../genel-bilgiler/tips-to-remain-anonymous.md)eğitimine yönlendiriyoruz. Bu eğitimde bahsedilen tüm noktalar Tornado Cash Nova için geçerlidir.

Hızlı bir hatırlatma olarak, bu ipuçlar şunları içerir:

* VPN kullanımı,
* Korumalı anahtarı veya bu korumalı adrese erişimi paylaşmamak
* İndirildiyse, bu korumalı anahtarı güvenli bir yerde saklamak,
* Kullanım sonrası verilerin silinmesi,
* Tüm işlemlerde aynı API kullanılmasından kaçınılması,
* Para yatırma ve çekme anları arasında sabırlı olmak,
* Para çekmek için birden fazla adres kullanmak.

Ancak yeni özellikleriyle Tornado Cash Nova, anonimliği korumak için daha fazla önlem gerektiriyor.

### Aktarıcıların Kullanımı <a href="#user-content-use-of-relayers" id="user-content-use-of-relayers"></a>

İşlemler için gaz ücreti ödemeleri gereklidir. Korumalı transferler ve para çekme işlemleri için, gas ücreti karşılığında ETH sağlamak için iki ödeme yöntemi mevcuttur. **Cüzdanınızı bağlayabilir veya bir Relayer** kullanabilirsiniz.

Bu gas ücreti için cüzdanınızı gözden geçirmek, kullanılan ETH kimliğinizle bağlantılıysa işlemin gizliliğini tehlikeye atabilir. Bu nedenle, **gizliliği korumak için Aktarıcı kullanılması önerilir**

![](https://camo.githubusercontent.com/68763eaba4494cc3ec30a84e83c0b3122c4f3fee71a6f7b26c6a20fe926e5d48/68747470733a2f2f692e696d6775722e636f6d2f50735a3839596d2e706e67)

### Para Çekme Tutarlarının Seçimi <a href="#user-content-cekilme-secimi-tutarlari" id="user-content-cekilme-secimi-tutarlari"></a>

Özelleştirilmiş miktarlar özelliği, daha fazla esneklik ve kullanım özgürlüğü sunar. Ancak dikkatsizce kullanılırsa gizliliğinizi tehlikeye atabilir.

#### Para çekme işlemleri için önceden tanımlanmış tutarları seçme <a href="#user-content-choosing-predefined-amounts-for-drawals" id="user-content-choosing-predefined-amounts-for-drawals"></a>

![](https://camo.githubusercontent.com/c78fbddd86b5cd612451b37b51e496ad2c93e723783f22488650f4af27c404ab/68747470733a2f2f692e696d6775722e636f6d2f644b59764e51542e706e67)

Önceden tanımlanmış dört miktardan birini seçmeniz, para çekme işleminizin kalabalık işlem grubuna karışmasına ve anonim kalmasına izin vereceği için şiddetle tavsiye edilir.

Seçtiğiniz özelleştirilmiş bir miktarı çekmek için "Özel ayarla" özgürlüğüne hala sahipsiniz. Ancak, seçilen miktara bağlı olarak, aşağıdaki durumlarda ilk fon işleminiz ile para çekme işleminiz arasında bir bağlantı kurulabilir:

* başlangıçta yatırılan miktar ve çekilen miktar tamamen aynıdır,
* yatırılan ve çekilen tutarlar bir meblağ aracılığıyla kolayca ilişkilendirilebilir.

Örneğin, 0,42 ETH'lik bir depozito, tam olarak 0,42 ETH'nin veya iki kez 0,21 ETH'nin çekilmesiyle ilişkilendirilebilir ve bu da anonimliği tehlikeye atabilir. Bununla birlikte, 0,391 ETH'lik bir para çekme ile, 0,42 ve 0,391 miktarları arasında belirgin bir bağlantı olmadığı için gizlilik daha iyi korunur.

Özel seçenek, yalnızca bu gerçekler hakkında tam bilgi sahibi olarak ve eylemlerinize tamamen güvenerek seçilmelidir.

Yazan [@ayefda](https://torn.community/u/ayefda) Türkçe versiyonu [armog](https://twitter.com/armogedd0n)
