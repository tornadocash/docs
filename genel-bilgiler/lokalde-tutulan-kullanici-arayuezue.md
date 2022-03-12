# Lokalde Tutulan Kullanıcı Arayüzü

Tornado Cash protokolü, çekirdek geliştiriciler ekibi tarafından sağlanan küçültülmüş bir Kullanıcı Arayüzü sürümü aracılığıyla bilgisayarınızda lokal olarak başlatılabilir.

{% embed url="https://github.com/tornadocash/ui-minified" %}

#### Adım 1: Bilgisayarınıza Github deposunu klonlayın

Command Line Arayüzünüzü açarak, önce depoyu klonlamak, ardından yeni kopyalanan klasörün içine girmek için aşağıdaki komutları çalıştırabilirsiniz:

```
git clone https://github.com/tornadocash/ui-minified.git
cd ui-minified
```

#### Adım 2 : Klasörü HTTP Sunucunuza Servis Edin

```
python -m SimpleHTTPServer 8080
```

Başka herhangi bir http web sunucusunu kullanabilirsiniz, örneğin [npmjs.com/package/http-server](https://www.npmjs.com/package/http-server).

#### Adım 3 : Kullanıcı Arayüzünü Web Tarayıcınızda Localhost’ta çalıştırın

Bitirmek için Web Tarayıcınızda [http://localhost:8080](http://localhost:8080) çalıştırmanız ve sihrin gerçekleşmesine izin vermeniz yeterlidir 🪄

### TOR’da çalıştırma

Bir .onion etki alanında Tornado nakit kullanıcı arabirimi sunmak istiyorsanız, bunu docker-compose kullanarak yapmanın kolay bir yolu vardır.

* Aşağıdakileri yapıştırmanız gerekir `docker-compose.yml`

```
version: '2'

services:
  tornado_ui:
    image: tornadocash/ui
    restart: always
    container_name: tornado_ui
  watchtower:
    image: v2tec/watchtower
    restart: always
    volumes:
      - /var/run/docker.sock:/var/run/docker.sock
    command: --interval 60 tornado_ui
  tor:
    image: strm/tor
    restart: always
    depends_on: [ tornado_ui ]
    environment:
      LISTEN_PORT: 80
      REDIRECT: tornado_ui:80
      # Generate a new key with
      # docker run --rm --entrypoint shallot strm/tor-hiddenservice-nginx ^torn
      PRIVATE_KEY: |
        -----BEGIN RSA PRIVATE KEY-----
        ...
        -----END RSA PRIVATE KEY-----
```

* Ardından, aşağıdaki komutu çalıştırmanız yeterlidir:`docker-compose up -d`

Tornado Cash UI’in tadını çıkarın 🌪 🌪

_Bu rehberde, Github’da bulunan_[ _README.md document_](https://github.com/tornadocash/ui-minified/blob/gh-pages/README.md) _dökümanında esinlenilmiştir.._

\_\_

[@ayefda](https://torn.community/u/ayefda) tarafından yazılmıştır. Türkçe çeviri için [@armog](https://twitter.com/armogedd0n) teşekkürler.
