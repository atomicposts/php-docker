PHP DOCKER
=====================

Dockerized web environemnt for PHP projects.

### Services:
  - Apache 2.4
  - PHP FPM 5.6
  - PHP CLI 5.6
  - Composer
  - Mysql 5.6
  - PhpMyadmin

Installing Docker
-----------------
Follow one of the installation guides below for your operating system:
* [Linux] https://docs.docker.com/linux/started/
* [Mac] http://docs.docker.com/mac/started/
* [Windows] http://docs.docker.com/windows/started/

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
```

Reload Bash

``` sh
$ source ~/.bashrc
```

Run php56 or composer command:

``` sh
$ php56 -i
$ composer --version
```