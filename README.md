
## MyLocker Installation Guide
<p align="center"><a href="https://gotipath.com" target="_blank"><img src="./logos/myocker.png" width="200"></a></p>

## Server Requirements
- PHP >= 8.1
- BCMath PHP Extension
- Ctype PHP Extension
- Fileinfo PHP Extension
- JSON PHP Extension
- Mbstring PHP Extension
- OpenSSL PHP Extension
- PDO PHP Extension
- Tokenizer PHP Extension
- XML PHP Extension
- Php-curl PHP Extension
- Imagick PHP Extension
- Ghostscript
- Redis
- Nginx
- Mysql 8.0
- Supervisor


### Before Getting Started

- Run `git clone https://gitlab.com/gotipath-gitlab/mylocker/mylockermvp.git mylocker`
- Run `cd mylocker`

## Production Installation

- Setup database configurations on `.env` file
- Setup redis configuration on `.env` file
- Change `APP_DEBUG` to `false` on `.env` file
- Change `APP_ENV` to `production` on `.env` file
- Change `CACHE_DRIVER` to `redis` on `.env` file
- Change `QUEUE_CONNECTION` to `redis` on `.env` file
- Change `SESSION_DRIVER` to `redis` on `.env` file
- Run `composer install --optimize-autoloader --no-dev`
- Run `cp .env.example .env`
- Run `php artisan key:generate`
- Run `php artisan app:install`
- Run `php artisan migrate`
- Run `php artisan optimize`

## Configuring Supervisor
- Supervisor configuration files are typically stored in the `/etc/supervisor/conf.d` directory. Within this directory,
  you may create any number of configuration files that instruct supervisor how your processes should be monitored. For
  example, let's create a `mylocker-worker.conf` file that starts and monitors `queue:work` processes:

```bash
[program:mylocker-worker.conf]
process_name=%(program_name)s_%(process_num)02d
command=php /var/www/mylocker/artisan queue:work redis --sleep=3 --tries=3 --max-time=3600
autostart=true
autorestart=true
stopasgroup=true
killasgroup=true
user=root
numprocs=8
redirect_stderr=true
stdout_logfile=/var/log/mylocker/worker.log
stopwaitsecs=3600
 ```

## Local Installation

- Install [laravel valet](https://cpriego.github.io/valet-linux/) for local development.
- Setup database configurations on `.env` file
- Setup redis configuration on `.env` file
- Run `composer update`
- Run `php artisan migrate:fresh`
- Run `php artisan optimize:clear`
- Run `valet link` to serve the application on `mylocker.test` domain

## Git Etiquette's

#### General guidelines

* Try not to push anything without a work item (or issue)
* Never ever push code directly to `main`
* Always create a `feature branch` for your task
* Your branch name, Pull/Merge Request title should be meaningful, very, very meaningful
* Make sure you tested your code well before creating a Pull/Merge Request
* Don't do `git pull`. Do `rebase`. First do `git fetch origin` and then `git rebase origin/master` (or maybe `main`
  instead of `master`). The thing is, `git pull` adds so many garbages. We need to keep our git history cleaner. Do this
  when you think there are some changes in master branch. And let's say you got a `merge conflict`. Then do the above
  mentioned stuff and don't forget to add your files (which had merge conflicts) manually (i.e. `git add file_name`). Do
  not use `git add .`. Such things don't work.

#### Branch naming convention:

- `dev/your_username/branchName` (branch name in **camelCase**) or
- `dev/your_username/branch_name` (branch name with underscore)
  So here are the steps:

* Check out your work item (or issue)
* Create a feature branch
* Write your code
* Test locally
* Push your code
* Create a Merge Request and assign it to someone
* Attend to Pull/Merge Request comments
* If `approved`, update(increment) `web-version` in `composer.json` file. Then push the changes and merge it to master

## Clean Code Guideline (minimal)

* Spaces, not tabs, are the white space character of choice in our projects. Tabs should consist of 4 spaces.
* Comma, colon, and semicolon characters always get a single space after them and never before them.

```php
// bad
[1,2,3]

// good
[1, 2, 3]
```

* Binary arithmetic operators, equals sign, arrows always get a single space before and after them.
  Rationale: less dense is easier on the eyes/brain, less strain mean lower likelihood of bugs.

```php
// bad
1+2/3
1*(2/3)
if (i=4)

// good
1 + 2 / 3
1 * (2 / 3)
if (i = 4)
```

* Align grouped variables.
  Note that, we don't need to align all the variales, some variables will be of different group or, too long to align.
  Leave them. Or align them as another `block`

```php
// bad
$first = 1;
$firstFirstFirt = 2;
$second = 3;

// good
$first          = 1;
$firstFirstFirt = 2;
$second         = 3;
```

* Try to group variables within brackets. Not mandatory always.

```php
// Not recommended
return x + y

// Better
return (x + y)
```

* Class name should be PascalCased

```php
// Good
class DemoClass {
  // ....
}
```

* Function/Method name should be camelCased

```php
// Good
function myFunction () {
  // ....
}
```

* Avoid `single letter` variable name as much as possible
* Remember, good code hardly needs comments. So all the variable and function names should convey a clear message
