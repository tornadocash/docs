# Interfaz de usuario reducida alojada localmente

El protocolo de Tornado Cash se puede iniciar localmente en tu computadora a través de una versión reducida de la interfaz de usuario puesta a disposición por el equipo central de desarrolladores.

{% embed url="https://github.com/tornadocash/ui-minified" %}

### Paso #1: Clona el repositorio de Github en tu computadora

Al abrir tu interfaz de comandos, puedes ejecutar los siguientes comandos para, primero, clonar el repositorio y luego ingresar a la carpeta recién copiada:

```
git clone https://github.com/tornadocash/ui-minified.git
cd ui-minified
```

### Paso #2: Configura la carpeta con tu servidor HTTP favorito

```
python -m SimpleHTTPServer 8080
```

Obviamente, puedes utilizar cualquier otro servidor web http, como[ npmjs.com/package/http-server](https://www.npmjs.com/package/http-server).

### Paso #3: Ejecuta la interfaz de usuario en Localhost en tu navegador web favorito

Para finalizar, solo necesitas ejecutar [http://localhost:8080](http://localhost:8080) en tu navegador web y deja que suceda la magia 🪄

## Ejecutar un servicio TOR

Si deseas ejecutar la interfaz de usuario de tornado cash en un dominio .onion, hay una manera fácil de hacerlo usando docker-compose.

* Necesitas pegar lo siguiente en `docker-compose.yml`

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

* Luego, simplemente tienes que ejecutar el siguiente comando:`docker-compose up -d`

Y disfruta de tu interfaz de usuario de Tornado Cash 🌪



_Este tutorial está inspirado en el_[ _documento README.md _](https://github.com/tornadocash/ui-minified/blob/gh-pages/README.md) _presente en el repositorio de Github._

__

_Escrito por_ [_@ayefda_](https://torn.community/u/ayefda)
