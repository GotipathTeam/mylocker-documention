<p align="center"><a href="https://gotipath.com" target="_blank"><img src="https://mycdn.gotipath.com/wp-content/uploads/2021/04/gotipath-logo-web.png" width="200"></a></p>

<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="200"></a></p>


## Server Requirements

- PHP >= 8.0
- BCMath PHP Extension
- Ctype PHP Extension
- Fileinfo PHP Extension
- JSON PHP Extension
- Mbstring PHP Extension
- OpenSSL PHP Extension
- PDO PHP Extension
- Tokenizer PHP Extension
- XML PHP Extension

### Before Getting Started
- Run `git clone git@github.com:GotipathTeam/goplay.git`
- Run `cd goplay`

## Production Installation
- Setup database configurations on `.env` file
- Setup redis configuration on `.env` file
- Change `APP_DEBUG` to `false` on `.env` file
- Change `APP_ENV` to `production` on `.env` file
- Run `composer install --optimize-autoloader --no-dev`
- Run `php artisan migrate`
- Run `php artisan optimize`

## Local Installation
- Install [laravel valet](https://cpriego.github.io/valet-linux/) for local development.
- Setup database configurations on `.env` file
- Setup redis configuration on `.env` file
- Run `composer update`
- Run `php artisan migrate:fresh`
- Run `php artisan optimize:clear`
- Run `valet link` to serve the application on `goplay.test` domain

