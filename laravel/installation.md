# [Getting Started](https://laravel.com/docs/8.x/installation)

## Docker

```shell
$ curl -s "https://laravel.build/example-app" | bash
$ cd example-app
$ ./vendor/bin/sail up
```

## Composer

```shell
$ composer create-project laravel/laravel example-app
$ cd example-app
$ php artisan serve
```

## Global Laravel Installer

```shell
$ composer global require laravel/installer
$ laravel new example-app
$ cd example-app
$ php artisan serve
```
