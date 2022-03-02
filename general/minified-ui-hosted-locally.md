# 本地简化版UI

Tornado Cash协议可以通过核心开发团队提供的简化版用户界面在您的计算机上本地启动。

{% embed url="https://github.com/tornadocash/ui-minified" %}

### 步骤#1：在您的计算机上克隆Github存储库

通过打开命令行界面，您可以运行以下命令，首先克隆存储库，然后进入新创建的文件夹：

```
git clone https://github.com/tornadocash/ui-minified.git
cd ui-minified
```

### 步骤#2：使用您的HTTP服务器为文件夹提供服务

```
python -m SimpleHTTPServer 8080
```

您可以使用任何其他http Web服务器，例如[ npmjs.com/package/http-server](https://www.npmjs.com/package/http-server)。

### 步骤#3：在您的浏览器上的localhost上运行UI

最后，您只需在浏览器上运行 [http://localhost:8080](http://localhost:8080) 并让奇迹发生。

## 运行TOR服务

如果您希望在.onion域上提供tornado cash UI，可以使用docker-compose轻松实现。

* 您需要将以下内容粘贴到 `docker-compose.yml`

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

* 然后，只需运行以下命令：`docker-compose up -d`

享受您的Tornado Cash UI 🌪

_本教程的灵感来自Github 存储库中的_[ _README.md 文档_](https://github.com/tornadocash/ui-minified/blob/gh-pages/README.md) _。_

_编写_ [_@ayefda_](https://torn.community/u/ayefda)
