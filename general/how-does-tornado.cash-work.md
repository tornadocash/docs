# Tornado.Cash Nasıl Çalışır?

Tornado.Cash’in kullanımını açıklayan ve kolaylaştıran maddelere girmeden önce protokolün küresel işleyişine genel olarak bir bakalım.

### Tornado.Cash işleyişine genel bakış

Gizliliği sağlamak için Tornado.Cash, bir adresten token mevduatlarını kabul eden ve farklı bir adresten çekilmelerini sağlayan akıllı sözleşmeler kullanır. Bu akıllı sözleşmeler, yatırılan tüm varlıkları karıştıran havuzlar olarak çalışır.

Fonlar, bu havuzlardan tamamen yeni bir adres tarafından çekildiğinde, kaynak ve hedef arasındaki on-chain bağlantısı kopar. Bu sayede çekilen kripto varlıkları anonimleştirilir.

Tokenlar bir Tornado Cash havuzundayken, saklama kullanıcıların elinde kalır. Bu nedenle, kullanıcılar tokenlar üzerinde tam kontrole sahiptir.

**Geleneksel Tornado Cash sabit tutar havuzları için:**:

* Bir kullanıcı bir havuza para yatırdığında (yani mevduat), özel bir not oluşturulur. Bu özel not, kullanıcının daha sonra bu fonlara erişmesi için özel bir anahtar olarak çalışır. Aynı kullanıcı, bunları çekmek için eski veya yeni bir adres kullanarak farklı bir adres kullanabilir ve bu özel anahtar sayesinde parasını geri alabilir.

**Tornado Cash Nova için, isteğe bağlı tutarlar ve korumalı transferler içeren yeni ETH havuzu**:

* Fonlar doğrudan belirli bir cüzdan adresine bağlıdır. Özel not veya anahtar yoktur. Kullanıcılar uygun adres ile havuza bağlanarak fonlarına ulaşabilirler.
* Saklama, ya havuza token yatırma eylemiyle ya da havuza kaydolarak ve başka bir adresten korumalı transferler alarak elde edilir.

Böyle bir protokolün gücü, doğal olarak kullanıcı sayısından ve havuzunun büyüklüğünden gelir. Ne kadar çok kullanıcı havuza yatırırsa o kadar mutlu olur. Ancak, gizliliği ve anonimliği korumak için kullanıcının aşağıdakiler gibi bazı temel kuralları akılda tutması gerekir:

* Çekerken gas ödemek için bir relayer kullanmak;
* Para yatırma ve çekme eylemi arasında bir zaman aralığı bırakmak;
* Varlıklarını kurtarmadan önce birkaç işlemi bekleyerek fonlarını başka fonlarla karıştırmak.

_Daha fazla öneri için:_ [_Anonim Kalma İpuçları_](tips-to-remain-anonymous.md)_._

### zk-SNARK ve Hash İşleminin Katkısı

Tornado.Cash, işlemleri doğrulamak ve izin vermek için zero knowledge temelli zk-SNARK teknolojisini kullanır. Tornado.Cash, bir depozitoyu işlemek için rastgele bir bayt alanı oluşturur, bunu [Pederson Hash](https://iden3-docs.readthedocs.io/en/latest/iden3\_repos/research/publications/zkproof-standards-workshop-2/pedersen-hash/pedersen.html) aracılığıyla hesaplar (zk-SNARK ile yakın olduğu için), ardından tokenı ve 20 mimc hash’i akıllı sözleşmeye gönderir. Sözleşme daha sonra onu Merkle ağacına ekleyecektir.

Para çekme işlemini gerçekleştirmek için aynı bayt alanı iki ayrı parçaya bölünür: bir tarafta secret ve diğer tarafta nullifier. Nullifier hash edilir. Bu nullifier, akıllı sözleşme ve Merkle ağacı verileriyle kontrol edilmek üzere on-chainde gönderilen genel bir girdidir. Örneğin çifte harcamayı önler.

zk-SNARK sayesinde herhangi bir bilgiyi ifşa etmeden ilk taahhüdün ve nullifier’ın 20 mimc hash’ini kanıtlamak mümkündür. Çekim işlemi herkese açık olsa bile, hash sıfırlayıcıyı ilk taahhütle ilişkilendirmenin bir yolu olmadığından gizlilik korunur. Ayrıca, işlemin Merkle kökünde mevcut olduğu bilgisi olsa bile işlemin konumu hakkındaki bilgiler gizli tutulur.

Gönderim teknolojik açıdan ucuzdur ancak 20 mimc hash’i hesaplamaları ve Merkle ağacını güncellemeleri gerektiğinden gas açısından pahalıdır. Tersine, geri çekme işlemi daha karmaşıktır. Ancak gas yalnızca sıfırlayıcı hash ve zk proof için gerekli olduğundan daha ucuzdur.

_Bu metin [_@ayefda_](https://torn.community/u/ayefda)tarafından yazılmıştır.
_Türkçe versiyonu için armog’a teşekkürler_ 
