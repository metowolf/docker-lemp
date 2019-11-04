# Docker LEMP

|name|pulls|version|layers|image size|
|:---:|:---:|:---:|:---:|:---:|
|[metowolf/php](https://hub.docker.com/r/metowolf/php)|![Pulls Count](https://img.shields.io/docker/pulls/metowolf/php.svg?style=flat-square)|![GitHub release (latest by date)](https://img.shields.io/github/v/tag/metowolf/docker-php?style=flat-square)|![Layers](https://shields.beevelop.com/docker/image/layers/metowolf/php/latest.svg?style=flat-square)|![image size](https://shields.beevelop.com/docker/image/image-size/metowolf/php/latest.svg?style=flat-square)|
|[metowolf/nginx](https://hub.docker.com/r/metowolf/nginx)|![Pulls Count](https://img.shields.io/docker/pulls/metowolf/nginx.svg?style=flat-square)|![GitHub release (latest by date)](https://img.shields.io/github/v/tag/metowolf/docker-nginx?style=flat-square)|![](https://shields.beevelop.com/docker/image/layers/metowolf/nginx/latest.svg?style=flat-square)|![](https://shields.beevelop.com/docker/image/image-size/metowolf/nginx/latest.svg?style=flat-square)|
|[mysql/mysql-server](https://hub.docker.com/r/mysql/mysql-server)|![Pulls Count](https://img.shields.io/docker/pulls/mysql/mysql-server.svg?style=flat-square)||![](https://shields.beevelop.com/docker/image/layers/mysql/mysql-server/latest.svg?style=flat-square)|![](https://shields.beevelop.com/docker/image/image-size/mysql/mysql-server/latest.svg?style=flat-square)|
|[metowolf/redis](https://hub.docker.com/r/metowolf/redis)|![Pulls Count](https://img.shields.io/docker/pulls/metowolf/redis.svg?style=flat-square)|![GitHub release (latest by date)](https://img.shields.io/github/v/tag/metowolf/docker-redis?style=flat-square)|![](https://shields.beevelop.com/docker/image/layers/metowolf/redis/latest.svg?style=flat-square)|![](https://shields.beevelop.com/docker/image/image-size/metowolf/redis/latest.svg?style=flat-square)|
|[phpmyadmin/phpmyadmin](https://hub.docker.com/r/phpmyadmin/phpmyadmin)|![Pulls Count](https://img.shields.io/docker/pulls/phpmyadmin/phpmyadmin.svg?style=flat-square)||![](https://shields.beevelop.com/docker/image/layers/phpmyadmin/phpmyadmin/latest.svg?style=flat-square)|![](https://shields.beevelop.com/docker/image/image-size/phpmyadmin/phpmyadmin/latest.svg?style=flat-square)|

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
