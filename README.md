# 💻PHPUnit Environment for WordPress Plugin🌐

[![docker build automated?](https://img.shields.io/docker/cloud/automated/futureys/phpunit-wordpress-plugin.svg)](https://hub.docker.com/r/futureys/phpunit-wordpress-plugin/builds)
[![docker build passing?](https://img.shields.io/docker/cloud/build/futureys/phpunit-wordpress-plugin.svg)](https://hub.docker.com/r/futureys/phpunit-wordpress-plugin/builds)
[![image size and number of layers](https://images.microbadger.com/badges/image/futureys/phpunit-wordpress-plugin.svg)](https://hub.docker.com/r/futureys/phpunit-wordpress-plugin/dockerfile)
[![Twitter URL](https://img.shields.io/twitter/url?style=social&url=https%3A%2F%2Fgithub.com%2Fyukihiko-shinoda%2Fdocker-compose-phpunit-wordpress-plugin)](http://twitter.com/share?text=%F0%9F%92%BBPHPUnit%20Environment%20for%20WordPress%20Plugin%F0%9F%8C%90&url=https://github.com/yukihiko-shinoda/docker-compose-phpunit-wordpress-plugin&hashtags=wordpress,phpunit,vscode)

Supplies PHPUnit environment built acording to
[official document on WordPress.org](https://make.wordpress.org/cli/handbook/plugin-unit-tests/#running-tests-locally).

Contents:

- [Benefit](#benefit)
- [Requirement](#requirement)
- [Quickstart](#quickstart)
- [Out of scope](#out-of-scopde)

## Benefit

- [🛠️Use for backend development](#use-for-backend-development)
- [🎈Easy to prepare](#easy-to-prepare)
- [✨Clean for PC](#clean-for-pc)

### 🛠️Use for backend development

This environment provides following tools:

- PHPUnit
- Mockery
- PHP_CodeSniffer

And also can work with Visual Studio Code.
You can lint your code on editor in real time.

### 🎈Easy to prepare

You can skip much steps to prepare environment.
And you will be able to start Unit Test for WordPres plugin with [only few steps](#Quickstart).

### ✨Clean for PC

You don't need to install any SDKs in your PC without [only few requirements](#requirement). You will be free from regular maintenance for development environment.

## Requirement

- Docker
- Docker Compose

### Optional

- Visual Studio Code (Recommend)
  - [In case when Windows, only Windows 10 Pro/Enterprise is supported.](https://code.visualstudio.com/docs/remote/containers#_system-requirements)

## Quickstart

### With Visual Studio Code (Recommend)

[Tutorial with screenshot are available on the Wiki](https://github.com/yukihiko-shinoda/docker-compose-phpunit-wordpress-plugin/wiki).

### Without Visual Studio Code

If you want to use other editor or IDE,
you also can use this environment only for running PHPUnit or PHP_CodeSniffer.

#### 1. Clone or download

```console
git clone https://github.com/yukihiko-shinoda/docker-compose-phpunit-wordpress-plugin.git
```

#### 2. Set environment variables

Copy ```.env.dist``` to ```.env```.

```console
copy .env.dist .env
```

Edit ```.env``` to set ```PATH_TO_INDIVIDUAL_PLUGIN_DIRECTORY```.

Ex:

```ini
PATH_TO_INDIVIDUAL_PLUGIN_DIRECTORY=../plugins/staticpress2019
# DOCKER_IMAGE_PHPUNIT=futureys/phpunit-wordpress-plugin:4.3.22-php7.1.33-apache-buster
# MYSQL_VERSION=5.6
```

#### 3. Execute Docker Compose run

```console
docker-compose run phpunit
```

And then, you can execute PHPUnit and PHP_CodeSniffer.

```console
phpunit
```

```console
phpcs
```

## Out of scope

UI test is not available by this environment.
