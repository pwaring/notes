# Laravel

## Requirements

 * PHP 7.0.0 (as of Laravel 5.5)
 * OpenSSL extension
 * PDO extension
 * MBstring extension
 * Tokenizer extension
 * XML extension

## Installation

You must use an up to date version of Composer otherwise the installation may
fail.

```
composer global require "laravel/installer"
```

Then add to `~/.bashrc` or equivalent:

```
export PATH="${HOME}/.config/composer/vendor/bin:${PATH}"
```

Remember to run `composer self-update && composer global update` on a regular
basis.

## Projects

Create a new project by running:

```bash
laravel new projectName
```

## General

`./vendor/bin/phpunit` runs all unit tests (`tests/*Test.php`).

Database credentials and other configuration goes in `.env`.

All variables set in `.env` will be loaded into the `$_ENV` superglobal and are
also available via the `env` helper: `env('APP_DEBUG', false)`. The second
parameter is the default, which will be returned if no environment variable exists
for the given key.

Run `php artisan config:cache` as part of production deployment.

`php artisan migrate` will turn PHP schema into a database.

Default text field sizes will break on MariaDB <= 10.2.1 and MySQL <= 5.7.6 due
to the number of bytes used for each character. Upgrade to a supported version
or add the following to `app/Providers/AppServiceProviders.php`:

```
<?php

 use Illuminate\Support\Facades\Schema;

 public function boot()
 {
    Schema::defaultStringLength(191);
 }
```

The default character set used by Laravel from 5.4 onwards is `utf8mb4`. Basically
the maximum length of a key is 767 bytes, and if 4 bytes are used per character
then this effectively limits key strings to 191 characters.

Returning a database query from a route casts it to JSON.

`dd($var)` dumps `$var` and then calls `die()`.

## Routing

Simple route definitions can be implemented by using closures, e.g.

```php
Route::get('/about', function() {
  return 'About';
});
```

However, this can become unwieldy for large sites. Applications using closures
also cannot take advantage of Laravel's route caching.

A common alternative to closures is to pass the name and method of a controller
as a string:

```php
Route::get('/about', 'WelcomeController@about');
```

This would call the `about` method of the `App\Http\Controllers\WelcomeController`
controller.

Regular expressions can be set for parameters:

```php
Route::get('users/{id}', function ($id) {
})->where('id', '[0-9]+');
```

Routes are matched top to bottom, so more specific regular expressions should
be defined first.

Routes can be grouped, which allows common configuration settings to be defined
once.

All defined routes can be listed by running:

```bash
php artisan route:list
```

Routes can be cached by running:

```bash
php artisan route:cache
```

However, from now on Laravel will only look at the cache, so you must run the
above command each time you make any changes to the routing file.

## Controllers

Create a controller by running:

```bash
php artisan make:controller StaticController
```

This will create a file:

```
app/Http/Controllers/StaticController.php
```

## Views

Views are stored under: `resources/views`.

### Templates

By default Laravel supports PHP templates and its own templating system called
Blade. For developers who prefer Twig, the [TwigBridge](https://github.com/rcrowe/TwigBridge)
component provides a bridge which allows files ending `.twig` to be loaded
automatically.
