# Minified UI Hosted Locally

Tornado Cash protocol can be launched locally on your computer through a minified User Interface version made available by the core developers team.

{% embed url="https://github.com/tornadocash/ui-minified" %}

### Step #1: Clone the Github repository on your computer

By opening your Command Line Interface, you can run the following commands to, first, clone the repository, then go inside the newly copied folder:

```
git clone https://github.com/tornadocash/ui-minified.git
cd ui-minified
```

### Step #2: Serve the Folder with Your Favorite HTTP Server

```
python -m SimpleHTTPServer 8080
```

You can obviously use any other http web server, such as[ npmjs.com/package/http-server](https://www.npmjs.com/package/http-server).

### Step #3: Run the UI on Localhost on your Favorite Web Browser

To finish, you just need to run [http://localhost:8080](http://localhost:8080) on your Web Browser & let the magic happens 🪄

## Running a TOR service

If you wish to serve tornado cash UI on an .onion domain, there is an easy way to do it using docker-compose.

* You need to paste the following into `docker-compose.yml`

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

* Then, just run the following command:`docker-compose up -d`

Enjoy your Tornado Cash UI 🌪

_This tutorial is inspired from the_[ _README.md document_](https://github.com/tornadocash/ui-minified/blob/gh-pages/README.md) _present in the Github repository._

__

_Written by_ [_@ayefda_](https://torn.community/u/ayefda)
