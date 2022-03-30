# UI Local & Minifié

Le protocole Tornado Cash peut être lancé localement sur votre ordinateur grâce à un interface minifié publié par l'équipe de développeurs de Tornado Cash.

{% embed url="https://github.com/tornadocash/ui-minified" %}

### Etape #1: Clonez la _repository_ Github sur votre ordinateur

En ouvrant l'interface de lignes de commandes, vous pouvez lancer les commandes suivantes pour cloner la _repository,_ puis aller à l'intérieur du dossier nouvellement copié:

```
git clone https://github.com/tornadocash/ui-minified.git
cd ui-minified
```

### Etape #2: Utilisez votre serveur HTTP préféré

```
python -m SimpleHTTPServer 8080
```

Vous pouvez bien évidemment utiliser n'importe quel autre serveur web http, tel que [ npmjs.com/package/http-server](https://www.npmjs.com/package/http-server).

### Etape #3: Lancez l'UI en local sur votre navigateur préféré

Pour finir, vous avez simplement besoin de lancer [http://localhost:8080](http://localhost:8080) avec votre navigateur web et laissez la magie opérer 🪄

## Lancer un UI minifié avec TOR

Si vous souhaitez lancer un UI minifié avec un domaine .onion, il y a un moyen simple de le faire grâce à _docker-compose_.

* Vous devez coller cela dans `docker-compose.yml`:

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

* Ensuite, vous avez simplement à lancer cette commande: `docker-compose up -d`

Finiii ! Bravo. 🌪

_Ce tutoriel est inspiré du_ [ _README.md_](https://github.com/tornadocash/ui-minified/blob/gh-pages/README.md) _présent sur la repository Github._

__

_Ecrit par_ [_@ayefda_](https://torn.community/u/ayefda)

Traduit par @erikA
