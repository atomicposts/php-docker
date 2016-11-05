PHP DOCKER
=====================

Dockerized web environemnt for PHP projects.

### Services:
  - Apache 2.4
  - PHP FPM 5.6
  - PHP CLI 5.6
  - Composer
  - Symfony installer
  - Mysql 5.6
  - PhpMyadmin

### Containers available
  - apache (Apache 2.4)
  - php56 (PHP FPM 5.6)
  - php56-cli (PHP CLI 5.6, Composer and Symfony installer)
  - mysql (Mysql 5.6)
  - phpmyadmin (PhpMyadmin)

Directory schema
----------------
  - **apps**: Directory with working code
  - **apache**: Definition imagen with Apache 2.4
  - **apache/conf**: Apache configuration
  - **apache/logs**: Apache logs
  - **apache/conf/vhosts**: Apache virtual sites.
  - **php56/fpm**: Definition imagen with PHP-FPM 5.6
  - **php56/fpm/conf**: PHP-FPM 5.6 configuration
  - **php56/cli**: Definition imagen with  PHP-CLI 5.6, Composer and Symfony installer
  - **php56/cli/conf**: PHP-CLI 5.6 configuration

How to use
----------
### Setup docker environment

``` sh
docker-machine create -d virtualbox default
docker-machine start default
eval $(docker-machine env default)
```

### Build & Run!

```
docker-compose build
docker-compose up -d
```

### Stop

``` sh
docker-compose stop
docker-machine stop
```


Running PHP CLI commands
------------------------
### Usage

Define an bash alias in ~/.bashrc:

``` sh
alias php56='docker run --rm -it -v $(pwd):/usr/local/apache2/htdocs phpdocker_php56-cli php'
alias composer='docker run --rm -it -v $(pwd):/usr/local/apache2/htdocs phpdocker_php56-cli composer'
alias symfony='docker run --rm -it -v $(pwd):/usr/local/apache2/htdocs phpdocker_php56-cli symfony'
```

Reload Bash

``` sh
$ source ~/.bashrc
```

Run php56, composer or symfony command:

``` sh
$ php56 -i
$ composer --version
$ symfony --version
```