# Tornado.Cash'e Giriş

![](https://i.imgur.com/ruCVisJ.png)

Tornado Cash, kripto alanında özel işlemlere olanak tanıyan **tamamen merkeziyetsiz ve sansürsüz** bir protokoldür.

Merkeziyetsiz bir protokol olan Tornado.Cash akıllı sözleşmeleri Ethereum blockchaini içinde uygulanmıştır. Sözleşmeler değiştirilemez veya düzenlenemezdir. Bu nedenle, hiç kimse - ilk geliştiriciler dahil - bunları değiştiremez veya iptal edemez. Tüm yönetişim ve madencilik akıllı sözleşmeleri, topluluk tarafından merkezi olmayan bir şekilde işletilir.

Gözetim altında olmayan bir protokol olarak, kullanıcılar Tornado.Cash'i işletirken kripto para birimlerinin gözetimini kendi ellerinde tutarlar. Her para yatırma işleminde kullanıcılara varlıkları üzerinde tam kontrol ve yatırılan fonlara erişim sağlayan özel imkan sağlanmış olur.

## Gizlilik Nasıl Uygulanıyor?

Tornado Cash, kaynak ve hedef adresler arasındaki on-chain bağlantısını keserek işlem gizliliğini sağlıyor. Bir adresten ETH ve diğer token mevduatlarını kabul eden ve farklı bir adresten çekilmelerini sağlayan akıllı bir sözleşme kullanır. Gizliliği korumak amacıyla önceden var olup bakiyesi olmayan bir adrese, para çekmek için gas ödemelerinde bir aktarıcının kullanılması gibi birkaç uygulamaya sahiptir.

Daha fazla ayrıntı için: [Tornado.Cash nasıl çalışır?](https://docs.tornado.cash/v/tu/how-does-tornado.cash-work) & [Anonim kalma ipuçları](https://docs.tornado.cash/v/tu/tips-to-remain-anonymous)

## TORN Hangi Platformlarda Çalışıyor?

Protokol, 2019'daki başlangıcından bu yana Ethereum blockchaininde çalışıyor. Haziran 2021'de Binance Smart Chain ve Polygon üzerinde konuşlandırıldı.

Bugün itibariyle Tornado.Cash aşağıdaki tokenlarla kullanılabilir:

* Ethereum Blockchain : ETH (Ethereum), DAI (Dai), cDAI (Compound Dai), USDC (USD Coin), USDT (Tether) & WBTC (Wrapped Bitcoin),
* Binance Smart Chain: BNB (Binance Coin),
* Polygon Network: MATIC (Polygon),
* Gnosis Chain (eski adıyla xDAI Chain): xDAI (xDai),
* Avalanche Mainnet: AVAX (Avalanche),
* Optimism, Layer-2 ETH (Ethereum),
* Arbitrum One, Layer-2 ETH (Ethereum)

![](https://i.imgur.com/eZwQzl2.png)


Aralık 2021'e kadar protokol, bu tokenların bazıları için bir anonimlik madenciliği sistemi içeriyordu ve kullanıcılarının bir yönetişim tokenı (TORN) kazanmasına olanak tanıyordu. Kullanıcılar ETH, DAI, cDAI ve WBTC havuzlarına para yatırarak Blockchain ağında TORN kazanabildiler.

[Anonim madenciliği](https://github.com/tornadocash/docs/blob/en/tornado-cash-classic/anonymity-mining.md) ve [Tornado.Cash tokenı](https://github.com/tornadocash/docs/blob/en/general/torn.md) hakkında daha fazla bilgi linklerde mevcuttur.

TORN sayesinde Tornado Cash kullanıcıları protokolün şekillendirilmesine aktif olarak katılabilirler. Topluluk, Tornado Cash'in evrimi ve özelliklerinin iyileştirilmesi konusunda güçlü bir ağırlığa sahiptir. Aslında, **protokol parametreleri ve token dağıtımı, bu yönetişim aracılığıyla tamamen topluluğun kontrolü altındadır.**

Yukarıda bahsedilen tüm havuzlara [tornadocash.eth.link](https://tornadocash.eth.link/) üzerinden erişilebilir. Sabit tutarda para yatırma ve çekme prensibi ile çalışırlar. Bu, her tokenin 2 ila 4 farklı havuza sahip olduğu ve yalnızca 2 ila 4 farklı sabit miktarda işlem yapılmasına izin verdiği anlamına gelir (örneğin, ETH'nin dört farklı havuzu vardır, bu miktarların her biri için bir tane: 0.1, 1, 10 ve 100 ETH).

**Tornado Cash Nova**

[Tornado Cash Nova'nın (beta sürümü) Aralık 2021'de piyasaya sürülmesiyle](https://tornado-cash.medium.com/tornado-cash-introduces-arbitrary-amounts-shielded-transfers-8df92d93c37c), protokole benzersiz yeni özelliklere sahip yükseltilmiş bir havuz eklendi. Kullanıcılar artık sabit tutar işlemleriyle kısıtlanmıyor. Tornado Cash Nova'nın eklenmesiyle, isteğe bağlı bir miktar havuzu ve korumalı transferlerin kullanımından yararlanabilirler.

Tornado Cash Nova, hızı ve maliyeti optimize etmek için Gnosis Zinciri (eski xDai Zinciri) üzerinde Katman2 olarak çalışır. ETH'de tamamen özelleştirilmiş tutarların yatırılmasına ve çekilmesine izin verir. Bu havuz ayrıca, kullanıcıların havuzda kalırken tokenlerinin velayetini aktarabilecekleri korumalı işlemlere de olanak tanır.

Tornado Cash Nova'ya (beta versiyonu) [nova.tornadocash.eth.link](https://nova.tornadocash.eth.link/) adresinden erişilebilir. Tornado Cash Nova'nın işleyişiyle ilgili daha fazla bilgiyi belgelerimizin özel bölümünde bulabilirsiniz.

## Tornado.Cash Nasıl Çalışır?

[Tornado.Cash’in işleyişinin arkasındaki kodlar](https://github.com/tornadocash) - akıllı sözleşmeler, devreler ve toolchain - **tamamen açık kaynaktır**. Bir DAO (Merkezi Olmayan Otonom Organizasyon) olarak çalışan Tornado.Cash’in yönetişimi ve madencilik akıllı sözleşmeleri topluluğu tarafından işletilir.

Protokol ayrıca, zero knowledge proof’a olanak tanıyan zk-SNARK ile birlikte de çalışır ve kullanıcıların, bilgilerini ifşa etmeye gerek kalmadan sahip olduklarını göstermelerine olanak tanır. Bu teknolojinin kullanımı, **Ethereum topluluğunun yardımıyla Zcash ekibi** tarafından yapılan açık kaynak araştırmasına dayanmaktadır . zk-SNARK’i kurmak için [Tornado.Cash Güvenilir Kurulum Topluluğu](https://tornado-cash.medium.com/tornado-cash-trusted-setup-ceremony-b846e1e00be1) Mayıs 2020'de başlatıldı ve [1114](https://tornado-cash.medium.com/the-biggest-trusted-setup-ceremony-in-the-world-3c6ab9c8fffa) kişi katıldı. Bu önemli sayıdaki katılımcı, zk prooflarını taklit ederek protokolün tehlikeye atılmasını imkansız hale getiriyor.

Kullanıcı arayüzü, topluluk tarafından IPFS'de bulundurularak verilerin silinme risklerini en aza indiriyor. Arayüz en az bir kullanıcı tarafından IPFS’de bulundurulduğu sürece çalışacaktır.

Bu metin [_@ayefda_](https://torn.community/u/ayefda) tarafından yazılmıştır.\
Türkçe versiyonu için [armog](https://twitter.com/armogedd0n)'a teşekkürler.
