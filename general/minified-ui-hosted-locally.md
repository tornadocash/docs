# Минимизированный локальный пользовательский интерфейс

Протокол Tornado Cash можно запустить локально на вашем компьютере через уменьшенную версию пользовательского интерфейса, предоставленную командой разработчиков.

{% embed url="https://github.com/tornadocash/ui-minified" %}

### Шаг #1 - Клонируйте репозиторий Github на свой компьютер

Открыв интерфейс командной строки, вы можете запустить следующие команды, чтобы сначала клонировать репозиторий, а затем перейти во вновь скопированную папку:

```
git clone https://github.com/tornadocash/ui-minified.git
cd ui-minified
```

### Шаг #2 - Используйте папку с вашим HTTP-сервером

```
python -m SimpleHTTPServer 8080
```

Вы можете использовать любой другой http веб-сервер, например [npmjs.com/package/http-server](https://www.npmjs.com/package/http-server).

### Шаг #3 - Запустите UI на Localhost в своем любимом веб-браузере.

Чтобы закончить, вам просто нужно запустить [http://localhost:8080](http://localhost:8080) в вашем браузере.

## Запуск TOR

Если вы хотите использовать Tornado Cash UI в домене .onion, есть простой способ сделать это с помощью docker-compose:

* Вам нужно вставить следующее в `docker-compose.yml`

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

* Затем просто запустите команду:`docker-compose up -d`

Наслаждайтесь вашим Tornado Cash UI 🌪

__

_Автор:_ [_@ayefda_](https://torn.community/u/ayefda)
_Переведено и адаптировано:_ [**@Ghost**](https://torn.community/u/ghost)
