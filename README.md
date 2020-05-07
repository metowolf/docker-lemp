# Docker LEMP

|name|pulls|version|layers|image size|
|:---:|:---:|:---:|:---:|:---:|
|[metowolf/php](https://hub.docker.com/r/metowolf/php)|![Pulls Count](https://img.shields.io/docker/pulls/metowolf/php.svg?style=flat-square)|![GitHub release (latest by date)](https://img.shields.io/github/v/tag/metowolf/docker-php?style=flat-square)|![Layers](https://shields.beevelop.com/docker/image/layers/metowolf/php/latest.svg?style=flat-square)|![image size](https://shields.beevelop.com/docker/image/image-size/metowolf/php/latest.svg?style=flat-square)|
|[metowolf/nginx](https://hub.docker.com/r/metowolf/nginx)|![Pulls Count](https://img.shields.io/docker/pulls/metowolf/nginx.svg?style=flat-square)|![GitHub release (latest by date)](https://img.shields.io/github/v/tag/metowolf/docker-nginx?style=flat-square)|![](https://shields.beevelop.com/docker/image/layers/metowolf/nginx/latest.svg?style=flat-square)|![](https://shields.beevelop.com/docker/image/image-size/metowolf/nginx/latest.svg?style=flat-square)|
|[mysql/mysql-server](https://hub.docker.com/r/mysql/mysql-server)|![Pulls Count](https://img.shields.io/docker/pulls/mysql/mysql-server.svg?style=flat-square)||![](https://shields.beevelop.com/docker/image/layers/mysql/mysql-server/latest.svg?style=flat-square)|![](https://shields.beevelop.com/docker/image/image-size/mysql/mysql-server/latest.svg?style=flat-square)|
|[library/redis](https://hub.docker.com/_/redis)|![Pulls Count](https://img.shields.io/docker/pulls/library/redis.svg?style=flat-square)||![](https://shields.beevelop.com/docker/image/layers/library/redis/alpine.svg?style=flat-square)|![](https://shields.beevelop.com/docker/image/image-size/library/redis/alpine.svg?style=flat-square)|
|[phpmyadmin/phpmyadmin](https://hub.docker.com/r/phpmyadmin/phpmyadmin)|![Pulls Count](https://img.shields.io/docker/pulls/phpmyadmin/phpmyadmin.svg?style=flat-square)||![](https://shields.beevelop.com/docker/image/layers/phpmyadmin/phpmyadmin/latest.svg?style=flat-square)|![](https://shields.beevelop.com/docker/image/image-size/phpmyadmin/phpmyadmin/latest.svg?style=flat-square)|

## Requirements

Install [Docker](https://get.docker.com/) and [Compose](https://docs.docker.com/compose/install/)

## Usage

 1. Clone docker-lemp inside your project
```bash
git clone https://github.com/metowolf/docker-lemp.git
```
 2. Enter the docker-lemp folder and rename .env.example to .env.
```bash
cd docker-lemp
cp .env.example .env
cp docker-compose.example.yml docker-compose.yml
```
 3. Open your project’s .env file and set the following:
```ini
MYSQL_ROOT_PASSWORD=your_password
```
 4. Run your containers:
```bash
docker-compose up -d
```

### Running `QUIC`

The following configuration file can be used as a starting point to enable HTTP/3 support:
```nginx
http {
    server {
        # Enable QUIC, HTTP/3 and HTTP/2 on both IPv4 and IPv6.
        listen 443 ssl http2;
        listen 443 quic;
        listen [::]:443 ssl http2;
        listen [::]:443 quic;

        ssl_certificate      cert.crt;
        ssl_certificate_key  cert.key;

        # Add HSTS header
        add_header Strict-Transport-Security "max-age=31536000; includeSubDomains; preload" always;

        # Add Alt-Svc header to negotiate HTTP/3.
        add_header alt-svc 'h3-23=":443"; ma=86400';

        # Enable specific TLS versions (TLSv1 and TLSv1.1 are not longer saft, TLSv1.3 is required for QUIC).
        ssl_protocols TLSv1.2 TLSv1.3;
        ssl_ciphers TLS-CHACHA20-POLY1305-SHA256:TLS-AES-256-GCM-SHA384:TLS-AES-128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-RSA-AES128-SHA256;
        ssl_prefer_server_ciphers on;
        ssl_early_data on;
    }
}
```

## Running `brotli`

 1. Add the following lines into the configuration file of your sites to enable `brotli` feature:
```nginx
brotli on;
brotli_comp_level 6;
brotli_types text/plain text/css application/json application/x-javascript text/xml application/xml application/xml+rss text/javascript application/javascript image/svg+xml;
```

## Generally Upgrade

 1. Modify project’s .env file.
```bash
vim .env
```

 2. Rebuild containers:
```bash
docker-compose up -d --no-deps --build
```

## Upgrade to `Caddyless` version

### Before `git pull`

 1. Rename conflicted file if exists:
```bash
mv etc/nginx/nginx.conf etc/nginx/nginx.conf.bak
```

### After `git pull`

 1. Modify project’s .env file.
```bash
vim .env
```

 2. Move Nginx/MySQL/SSL configuration to new directory:
```bash
# move nginx configuration
mv etc/nginx/config/* etc/nginx/conf.d/

# move MySQL configuration
rm -fr etc/mysql && mkdir etc/mysql && mkdir etc/mysql/my.cnf.d
mv etc/database/data etc/mysql && mv etc/database/config/* etc/mysql/my.cnf.d

# move SSL configuration
mv etc/ssl etc/nginx
```

 3. Rebuild containers and remove the `Caddy` container:
```bash
docker-compose up -d --no-deps --build --remove-orphans
```
