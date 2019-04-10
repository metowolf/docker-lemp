# Docker LEMP

|name|version|status|layers|image size|
|:---:|:---:|:---:|:---:|:---:|
|[metowolf/php](https://hub.docker.com/r/metowolf/php)|![](https://images.microbadger.com/badges/version/metowolf/php.svg)|[![](https://img.shields.io/travis/com/metowolf/docker-php/master.svg?style=flat-square)](https://travis-ci.com/metowolf/docker-php)|![](https://img.shields.io/microbadger/layers/metowolf/php.svg?style=flat-square)|![](https://img.shields.io/microbadger/image-size/metowolf/php.svg?style=flat-square)|
|[metowolf/nginx](https://hub.docker.com/r/metowolf/nginx)|![](https://images.microbadger.com/badges/version/metowolf/nginx.svg)|[![](https://img.shields.io/travis/com/metowolf/docker-nginx/master.svg?style=flat-square)](https://travis-ci.com/metowolf/docker-nginx)|![](https://img.shields.io/microbadger/layers/metowolf/nginx.svg?style=flat-square&r)|![](https://img.shields.io/microbadger/image-size/metowolf/nginx.svg?style=flat-square&r)|
|[mysql/mysql-server](https://hub.docker.com/r/mysql/mysql-server)|![](https://images.microbadger.com/badges/version/mysql/mysql-server.svg)||![](https://img.shields.io/microbadger/layers/mysql/mysql-server.svg?style=flat-square)|![](https://img.shields.io/microbadger/image-size/mysql/mysql-server.svg?style=flat-square)|
|[metowolf/redis](https://hub.docker.com/r/metowolf/redis)|![](https://images.microbadger.com/badges/version/metowolf/redis.svg)|[![](https://img.shields.io/travis/com/metowolf/docker-redis/master.svg?style=flat-square)](https://travis-ci.com/metowolf/docker-redis)|![](https://img.shields.io/microbadger/layers/metowolf/redis.svg?style=flat-square&r)|![](https://img.shields.io/microbadger/image-size/metowolf/redis.svg?style=flat-square&r)|
|[phpmyadmin/phpmyadmin](https://hub.docker.com/r/phpmyadmin/phpmyadmin)|![](https://images.microbadger.com/badges/version/phpmyadmin/phpmyadmin.svg)||![](https://img.shields.io/microbadger/layers/phpmyadmin/phpmyadmin.svg?style=flat-square)|![](https://img.shields.io/microbadger/image-size/phpmyadmin/phpmyadmin.svg?style=flat-square)|
|[abiosoft/caddy](https://hub.docker.com/r/abiosoft/caddy)|![](https://images.microbadger.com/badges/version/abiosoft/caddy.svg)||![](https://img.shields.io/microbadger/layers/abiosoft/caddy.svg?style=flat-square)|![](https://img.shields.io/microbadger/image-size/abiosoft/caddy.svg?style=flat-square)|

## Requirements

Install [Docker](https://get.docker.com/) and [Compose](https://docs.docker.com/compose/install/)

## Usage

 1. Clone docker-lemp inside your project
```
git clone https://github.com/metowolf/docker-lemp.git
```
 2. Enter the docker-lemp folder and rename .env.example to .env.
```
cd docker-lemp
cp .env.example .env
cp docker-compose.example.yml docker-compose.yml
```
 3. Open your project’s .env file and set the following:
```
MYSQL_ROOT_PASSWORD=your_password
```
 4. Run your containers:
```
docker-compose up -d
```

## Upgrade

 1. Modify project’s .env file.
```
vim .env
```

 2. Rebuild containers:
```
docker-compose up -d --no-deps --build
```
