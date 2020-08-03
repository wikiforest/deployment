# Deployment
Deploy services and UI

## Initialization
```sh
git clone --recurse-submodules git@github.com:wikiforest/deployment.git
```

## Documents
### Docker hub link
https://hub.docker.com/r/hyperf/hyperf

### Version 2.0 document
https://hyperf.wiki/2.0/#/

### Evergreen UI
https://evergreen.segment.com/

## Aliyun mirror
### Composer
```sh
composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/
# cancel
composer config -g --unset repos.packagist
```

### Docker
```json
{
  "registry-mirrors": [
    "https://wbiz3je9.mirror.aliyuncs.com"
  ]
}
```

### Alpinelinux
```sh
sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories
```

## Docker Hub
https://hub.docker.com/orgs/wikiforest/

## Hosts
Change `/etc/hosts` for develop:
```
127.0.0.1       api.wikiforest.com
127.0.0.1       db.wikiforest.com
127.0.0.1       container.wikiforest.com
127.0.0.1       wikiforest.com
127.0.0.1       www.wikiforest.com
```

## Server
```sh
cd ./server
composer install --ignore-platform-reqs
```

## Deployment
First of all, See [mkcert document](https://github.com/FiloSottile/mkcert/blob/master/README.md "mkcert document") and install mkcert.

Then, install local CA certificates in your system trust store, and generate the cert and CA key (for develop).
```sh
mkcert -install
mkdir -p deploy/cert/dev
mkcert -key-file .\deploy\cert\dev\key.pem -cert-file .\deploy\cert\dev\cert.pem wikiforest.com *.wikiforest.com
```

And then, add an env file from example file, and start services.
```sh
cp .env.example .env
# then change .env for your local.
docker-compose build
docker-compose up
```

If you want to uninstall current certs, run:
```sh
mkcert -uninstall
```

## UI
First, start the [deployment service](https://github.com/wikiforest/server "deployment service"), then, start the frontend develop server:

```bash
docker-compose exec ui yarn
docker-compose exec ui yarn dev
```

UI host:   
[https://wikiforest.com/](https://wikiforest.com/ "https://api.wikiforest.com/")

Api host:   
[https://api.wikiforest.com/](https://api.wikiforest.com/ "https://api.wikiforest.com/")

## Logging Files
Fluentd Document: [https://docs.fluentd.org/](https://docs.fluentd.org/ "https://docs.fluentd.org/")

All log files are in `/deploy/fluentd/logs`

## Local Develop Tools
### Adminer
https://db.wikiforest.com

### Portainer
https://container.wikiforest.com

## Contact Alex
[omytty@126.com](mailto:omytty@126.com "omytty@126.com")
