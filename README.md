# Tornado.Cash'e Giriş

![](.gitbook/assets/image.png)

Tornado Cash, kripto alanında özel işlemlere olanak tanıyan **tamamen merkeziyetsiz ve sansürsüz** bir protokoldür.

Merkeziyetsiz bir protokol olan Tornado.Cash akıllı sözleşmeleri Ethereum blockchaini içinde uygulanmıştır. Sözleşmeler değiştirilemez veya düzenlenemezdir. Bu nedenle, hiç kimse - ilk geliştiriciler dahil - bunları değiştiremez veya iptal edemez. Tüm yönetişim ve madencilik akıllı sözleşmeleri, topluluk tarafından merkezi olmayan bir şekilde işletilir.

Gözetim altında olmayan bir protokol olarak, kullanıcılar Tornado.Cash'i işletirken kripto para birimlerinin gözetimini kendi ellerinde tutarlar. Her para yatırma işleminde kullanıcılara varlıkları üzerinde tam kontrol ve yatırılan fonlara erişim sağlayan özel imkan sağlanmış olur.

## Gizlilik Nasıl Uygulanıyor?

Tornado Cash, kaynak ve hedef adresler arasındaki on-chain bağlantısını keserek işlem gizliliğini sağlıyor. Bir adresten ETH ve diğer token mevduatlarını kabul eden ve farklı bir adresten çekilmelerini sağlayan akıllı bir sözleşme kullanır. Gizliliği korumak amacıyla önceden var olup bakiyesi olmayan bir adrese, para çekmek için gas ödemelerinde bir aktarıcının kullanılması gibi birkaç uygulamaya sahiptir.

Daha fazla ayrıntı için: [Tornado.Cash nasıl çalışır?](https://github.com/0xarmagan/docs/blob/6906bfbd2f1c74bcdbd4ea36a054d2824d6e7517/how-does-tornado.cash-work.md) & [Anonim kalma ipuçları](https://github.com/0xarmagan/docs/blob/6906bfbd2f1c74bcdbd4ea36a054d2824d6e7517/tips-to-remain-anonymous.md)

## TORN Hangi Platformlarda Çalışıyor?

Protokol, 2019'daki başlangıcından bu yana Ethereum blockchaininde çalışıyor. Haziran 2021'de Binance Smart Chain ve Polygon üzerinde konuşlandırıldı.

Bugün itibariyle Tornado.Cash aşağıdaki tokenlarla kullanılabilir:

* Ethereum : **ETH** _\(Ethereum\)_, **DAI** _\(Dai\)_, **cDAI** _\(Compound Dai\)_, **USDC** _\(USD Coin\)_, **USDT** _\(Tether\)_ & **WBTC** _\(Wrapped Bitcoin\)_
* Binance Smart Chain: **BNB** _\(Binance Coin\)_.
* Polygon Network: **MATIC** _\(Polygon\)_

![](.gitbook/assets/non-custodial-anonymous-transactions-on-ethereum-3-.png)

Protokol ayrıca, tokenlarının bir kısmı için, kullanıcılarının **yönetişim tokenı** kazanmalarına olanak tanıyan bir **anonim likidite madenciliği** sistemine de sahiptir. TORN tokenı sayesinde Tornado Cash kullanıcıları protokolün şekillendirilmesine aktif olarak katılır. Topluluk, Tornado Cash'in evrimi ve özelliklerinin iyileştirilmesi konusunda güçlü bir etkiye sahiptir. Aslında, protokol parametreleri ve token dağıtımı, bu yönetişim aracılığıyla tamamen topluluğun kontrolü altındadır.

[Anonim likidite madenciliği](https://github.com/0xarmagan/docs/blob/08b0a08b53c821b385a18f8cb604099e8c291d7d/anonymity-mining.md) ve [Tornado.Cash tokenı](https://github.com/0xarmagan/docs/blob/08b0a08b53c821b385a18f8cb604099e8c291d7d/torn.md) hakkında daha fazla bilgiye ulaşabilirsiniz.

## Tornado.Cash Nasıl Çalışır?

[Tornado.Cash’in işleyişinin arkasındaki kodlar](https://github.com/tornadocash) - akıllı sözleşmeler, devreler ve toolchain - **tamamen açık kaynaktır**. Bir DAO \(Merkezi Olmayan Otonom Organizasyon\) olarak çalışan Tornado.Cash’in yönetişimi ve madencilik akıllı sözleşmeleri topluluğu tarafından işletilir.

Protokol ayrıca, zero knowledge proof’a olanak tanıyan zk-SNARK ile birlikte de çalışır ve kullanıcıların, bilgilerini ifşa etmeye gerek kalmadan sahip olduklarını göstermelerine olanak tanır. Bu teknolojinin kullanımı, **Ethereum topluluğunun yardımıyla Zcash ekibi** tarafından yapılan açık kaynak araştırmasına dayanmaktadır . zk-SNARK’i kurmak için [Tornado.Cash Güvenilir Kurulum Topluluğu](https://tornado-cash.medium.com/tornado-cash-trusted-setup-ceremony-b846e1e00be1) Mayıs 2020'de başlatıldı ve [1114](https://tornado-cash.medium.com/the-biggest-trusted-setup-ceremony-in-the-world-3c6ab9c8fffa) kişi katıldı. Bu önemli sayıdaki katılımcı, zk prooflarını taklit ederek protokolün tehlikeye atılmasını imkansız hale getiriyor.

Kullanıcı arayüzü, topluluk tarafından IPFS'de bulundurularak verilerin silinme risklerini en aza indiriyor. Arayüz en az bir kullanıcı tarafından IPFS’de bulundurulduğu sürece çalışacaktır.

Bu metin [_@ayefda_](https://torn.community/u/ayefda) tarafından yazılmıştır.  
Türkçe versiyonu için [armog](https://twitter.com/arm00g)'a teşekkürler.

