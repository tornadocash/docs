# Nasıl Relayer - Aktarıcı Olunur?

{% hint style="warning" %}
25 Şubat 2022 - Bilgi\
Bu özellik henüz Tornado Cash UI'da mevcut değil\
\
(Sadece birkaç gün bekleyin.. :cloud\_tornado:)
{% endhint %}

[Tornado Cash 10. yönetişim teklifinin](https://tornadocash.eth.link/governance/10) yürütülmesinin ardından, herkes Tornado Cash kullanıcıları için aktarıcı olabilir.

{% hint style="success" %}
Tornado Cash UI'ye dahil olmak için tek koşul bir min. `300 TORN` yatırmaktır. Bu minimum pay her zaman bir yönetim oyu ile değiştirilebilir.
{% endhint %}

Aktarıcılar, Tornado Cash ekosisteminin önemli ve gerekli bir parçasını oluşturur. Kötü şöhretli “ücret ödeme ikilemini” çözdükleri için kullanımları gizliliği garanti eder: anonimliği korurken bir havuzdan token çekme ücretleri nasıl ödenir?

Bu nedenle, aktarıcılar üçüncü taraf olarak hareket eder ve tüm geri çekme işlemlerini halleder. İşlem ücretlerini doğrudan aktarılan tutardan düşülerek öderler. Ayrıca hizmetleri için ek bir ücret alırlar.

[Relayer Registry teklifi](https://tornadocash.eth.link/governance/10) olduğundan, protokol her para çekme için `StakingReward` sözleşmesi aracılığıyla doğrudan aktarıcının stake bakiyesinden bir ücret alacaktır. Bu ücret yüzdesi bir havuzdan diğerine değişebilir ve ayrıca zincir içi yönetişim yoluyla değişebilir.

Şimdilik `%0.3` olarak sabitlendi. Örnek bir ücret atamak için çok küçük olduğu için (0.1 ETH, 100 DAI/USDT, 1000 DAI/USDT) veya Uni v3'te (tüm cDAI örnekleri) yeterli likidite olmadığı için bazı havuzlar ücretsiz kalır.

## Nasıl Relayer- Aktarıcı Olunur?

Herkes, bir Relayer Registry Kullanıcı Arayüzü (UI) aracılığıyla **6 basit adımda** protokol için bir aktarıcı olabilir.

Aktarıcılar kulübümüze katılmak ve Tornado Cash merkeziyetsiz aktarıcı kaydında listelenmek için ihtiyacınız olan her şeyi aşağıda bulacaksınız.

### 1. Gereksinimler: Farkında Olun ve Potansiyel Riskleri Kabul Edin

Yolculuğunuzun bir kısmını aktarıcı olarak Tornado Cash kullanıcılarıyla paylaşmayı taahhüt etmeden önce, protokol için aktarıcı olmanın tüm potansiyel risklerinin farkında olmanız ve bunları kabul etmeniz gerekir.

### 2. Relayer'ı kurun

İlk somut adım, bilgisayarınızda Ethereum Mainnet için Tornado Cash Relayer yazılımını çalıştırmaktır. Tüm adımlar protokolün github'ında açıklanmıştır. Bu görevi başarıyla tamamlamak için [bu talimatları](https://github.com/tornadocash/tornado-relayer#deploy-with-docker-compose) dikkatli bir şekilde uygulamanız gerekecek.

{% embed url="https://github.com/tornadocash/tornado-relayer#deploy-with-docker-compose" %}

İşiniz bittiğinde, url'nizi giriş kutusuna eklemeniz gerekecektir.

![image](https://user-images.githubusercontent.com/75987728/155971835-4ee13bfc-8891-417a-a2c4-8bc2daa1129e.png)

### 3. ENS Subdomain Adını Ayarlayın

Bir sonraki adım şunlardan oluşur:

* Aktarıcınız için bir ENS alanı oluşturma,
* Ana ağ alt etki alanını kurma,
* Bu belirli biçime göre ana ağ alt etki alanına Aktarıcı URL'si ile bir TXT kaydı ekleme:

#### Ethereum Aktarıcıları (Zorunlu)

| TXT record              |
| ----------------------- |
| mainnet-tornado.xxx.eth |
| goerli-tornado.xxx.eth  |

#### **Yan Zincir Relayer'ları (Opsiyonel)**

Ayrıca, Ethereum dışındaki zincirleri desteklemek için ilgili TXT kayıtlarıyla birlikte alt alan adları ekleme olanağına da sahipsiniz. Yan zincir aktarıcıları, Relayer yazılımının farklı bir sürümünü kullanır. Bunu yapmak için gerekli tüm talimatlara [burada](https://github.com/tornadocash/tornado-relayer/blob/light/README.md) sahipsiniz.

| TXT record                |
| ------------------------- |
| bsc-tornado.xxx.eth       |
| gnosis-tornado.xxx.eth    |
| polygon-tornado.xxx.eth   |
| optimism-tornado.xxx.eth  |
| arbitrum-tornado.xxx.eth  |
| avalanche-tornado.xxx.eth |

#### Nova Relayer (Opsiyonel)

Tornado Cash Nova, yazılımın kendi sürümünü kullanır. Tornado Cash Nova için aktarıcı olmak istiyorsanız, izlemeniz gereken talimatları [burada](https://github.com/tornadocash/tornado-pool-relayer#deploy-with-docker-compose) bulacaksınız.

| TXT record          |
| ------------------- |
| gnosis-nova.xxx.eth |

![image](https://user-images.githubusercontent.com/75987728/155971873-68b0022d-f4f7-40cc-9e3b-1f18dd9870de.png)

#### 4. Çalışanları Ayarlayın

İşçiler, aktarıcınızın kullanıcılara ZK kanıtları göndermesine izin verecek adreslerdir. Varsayılan olarak, ilk çalışan ENS etki alanı sahibinin adresidir.

Ekstra bir güvenlik seviyesi sağlamak için birden fazla işçi kurmanızı tavsiye ederiz.

Yalnızca ana ağ, işçileri kaydetmenizi gerektirir. Diğer tüm ağlar kayıtlı çalışanların kullanımını gerektirmez.

![image](https://user-images.githubusercontent.com/75987728/155971902-a4c33b19-9eee-40eb-ac67-ae6dc4436894.png)

#### 5. Stake

Merkezi olmayan bir geçiş kaydının uygulanmasıyla, Tornado Cash UI'de listelenmek için bir stake koşulu getirildi. Gerçekten de, **Torn'u stake etmek artık önerilen aktarıcılar listesine eklenmek için gereklidir.**

Minimum yığın miktarı şu anda Tornado Cash yönetimi tarafından **`300 TORN`** olarak belirlenmiştir. Bu eşik, Tornado Cash yönetimi tarafından her zaman değiştirilebilir.

Tornado Cash havuzunda bir aktarıcı kullanıldığında, `StakingReward` sözleşmesi ile bu stake edilen bakiyeden otomatik olarak küçük bir miktar TORN tahsil edilir. Aktarıcıların stake bakiyelerini her zaman 300 TORN'un üzerinde tutmaları gerekeceğinden, bu unsurun akılda tutulması önemlidir.

Toplanan bu ücretler daha sonra TORN tokenleri kilitli olan DAO üyeleri arasında dağıtılır. TORN genellikle zincir üstü yönetişime katılmak için kilitlenir (teklifler için öneri ve oylama). Hem bu [forum gönderisinde](https://torn.community/t/proposal-relayer-registry-setting-parameters-after-audit/2134) hem de [Staking TORN dokümantasyon sayfasında](stake etme) daha fazla bilgi bulabilirsiniz. .md).

{% hint style="warning" %}
Stake ettiğiniz TORN miktarı talep edilemez ve iade edilemez.
{% endhint %}

![image](https://user-images.githubusercontent.com/75987728/155972254-7f3d3df9-ad2c-4d36-a7c0-9e69d6a5dbc1.png)

#### 6. Özet: Son Doğrulama ve Kayıt

Son olarak, ancak en az değil, kaydolmadan önce Özette bulunan **tüm bilgileri iki kez kontrol etmenizi** tavsiye ederiz.

![image](https://user-images.githubusercontent.com/75987728/155972275-6be6512e-a422-4f09-93f8-a3d11b4d800e.png)

_Relayer ekibine hoş geldiniz! Sizin sayenizde mahremiyete daha fazla saygı duyulabilir_ 💚



Yazan[**@bt11ba**](https://torn.community/u/bt11ba/) **** &[**@ayefda**](https://torn.community /u/ayefda)**** Türkçesi için [Armog](https://twitter.com/armogedd0n)'a teşekkür ederiz.
