# Tornado Cash ile TOR nasıl kullanılır?

Zincir içi gizlilik, [Tornado Cash](https://tornado.cash) aracıyla sağlanır.

Ancak işlemleriniz gerçekleştirilmeden önce ve sonra gizliliğiniz sağlanamayabilir. Bu yüzden Tornado Cash kullanırken TOR kullanmanızı tavsiye ediyoruz.

İşte anonimliğinizi sağlamak için hızlı ve kolay bir eğitim.

### #1. Adım - TOR'u yükleyin

Önce şuraya gidin: [https://www.torproject.org/download/](https://www.torproject.org/download/)

Uygun operatör sistemini seçin ve İndir'e tıklayın.

Sonra çalıştırın.

### **#2. Adım - TOR'u yapılandırın**

İlk olarak, URL gezinme çubuğunuzda `about:config` ifadesini arayın.

[![image](https://user-images.githubusercontent.com/75987728/155968282-69afa75b-4005-44b4-9f22-aef7a572e013.png)](https://user-images.githubusercontent.com/75987728/155968282-69afa75b-4005-44b4-9f22-aef7a572e013.png)

Ardından, `Accept the Risk and Continue`e tıklayarak uyarı mesajını kabul edin.

![](https://user-images.githubusercontent.com/75987728/155968302-10685c1f-bf41-40e5-b3f8-23e51131c7dd.png)

"Wasm" ifadesini arayın ve `javascript.options.wasm` öğesini true olarak açın.

![](https://user-images.githubusercontent.com/75987728/155968323-f102f797-01d2-4b7f-9aa6-0ec3ebe863b0.png)

`indexedDB`yi arayın ve `dom.indexedDB.logging.details` ve `dom.indexedDB.logging.enabled` öğelerini true olarak çevirin

![](https://user-images.githubusercontent.com/75987728/155968352-25718fe5-a7a5-453d-a865-fe99dab85e53.png)

### **#3. Adım -** Metamask'ı yükleyin

Şuraya gidin: [https://metamask.io/download/](https://metamask.io/download/)

İlk olarak, `Install Metamask for Firefox` seçeneğine tıklayın.

![](https://user-images.githubusercontent.com/75987728/155968375-846a76f6-324c-4143-872d-80c7ee11e726.png)

`Add` üzerine tıklayın.

![](https://user-images.githubusercontent.com/75987728/155968392-de36b5e0-37c9-4af4-b69a-c4dd4c662f52.png)

Addons.mozilla.org'un `Continue to Installation`e tıklayarak bir eklenti yüklemesine izin verin.

![](https://user-images.githubusercontent.com/75987728/155968420-20b64e64-7a59-4ea4-9255-33a3284d3ee6.png)

Bu uzantının Özel Windows'ta çalışmasına izin verdiğinizi onaylayın ve ardından `Okay`e tıklayın.

![](https://user-images.githubusercontent.com/75987728/155968440-d7d48f4b-6f8f-4112-8872-faa6391ce632.png)

Ardından, sağ tıklayıp Metamask simgesini araç çubuğunuza sürükleyerek Metamask'ı araç çubuğunuza ekleyebilirsiniz.

![](https://github.com/tornadocash/docs/raw/en/.gitbook/assets/metamaskicon\(1\).gif)

#### Adım [**tornadocash#4**](https://github.com/tornadocash/docs/pull/4) **- Gizliliğinizin keyfini çıkarın** 😎

Artık TOR ile [Tornado Cash Classic](https://tornadocash.eth.link) veya [Tornado Cash Nova](https://nova.tornadocash.eth.link) kullanabilirsiniz.

_Yazan_ [_**@bt11ba**_](https://torn.community/u/bt11ba/) Türkçesi için [Armog](https://twitter.com/armogedd0n) teşekkür ederiz.
