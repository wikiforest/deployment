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

## Deploy
```sh
docker-compose build
docker-compose up
```

## UI
First, start the [deployment service](https://github.com/wikiforest/server "deployment service"), then, start the frontend develop server:

```bash
docker-compose exec ui yarn dev
```

And visit:   
[http://wikiforest.com/](http://wikiforest.com/ "http://wikiforest.com/")

## Contact Alex
[omytty@126.com](mailto:omytty@126.com "omytty@126.com")
