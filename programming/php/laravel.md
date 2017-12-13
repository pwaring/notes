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

Use the `route()` helper instead of `url()` to refer to routes.

Route groups allow you to group routes together and share configuration settings
without having to repeat them for each route.

Parameterised subdomain routing can be used for multitenancy sites where each
client gets its own subdomain:

```
Route::group(['domain' => '{client}.example.org'], function() {
  Route::get('/', function($client) {

    });
  Route::get('/users/{$id}', function($client, $id) {

    });
});
```

## Routing

Simple route definitions can be implemented by using closures, e.g.

```
Route::get('/about', function() {
  return 'About';
});
```

However, this can become unwieldy for large sites. Applications using closures
also cannot take advantage of Laravel's route caching.

A common alternative to closures is to pass the name and method of a controller
as a string:

```
Route::get('/about', 'WelcomeController@about');
```

This would call the `about` method of the `App\Http\Controllers\WelcomeController`
controller.

Regular expressions can be set for parameters:

```
Route::get('users/{id}', function ($id) {
})->where('id', '[0-9]+');
```

Routes are matched top to bottom, so more specific regular expressions should
be defined first.

Routes can be grouped, which allows common configuration settings to be defined
once.

All defined routes can be listed by running:

```
php artisan route:list
```

Routes can be cached by running:

```
php artisan route:cache
```

However, from now on Laravel will only look at the cache, so you must run the
above command each time you make any changes to the routing file.

## Controllers

Create a controller by running:

```
php artisan make:controller PagesController
```

This will create a file:

```
app/Http/Controllers/PagesController.php
```

Add methods such as:

```
public function about()
{
  return view('about');
}
```

Route them:

```
Route::get('/about', 'PagesController@about')
```

Create a resource controller with:

```
php artisan make:controller TasksController --resource
```

This will add methods such as `index`, `create` etc.

You can build routes for all these resources like so:

```
Route::resource('tasks', 'TasksController');
```

`php artisan route:list` will list all of your routes.

## Views

Views are stored under: `resources/views`.

## Eloquent

Eloquent is Laravel's Active Record implementation.

### Database

Migrations define the modifications which should be run when making the migration
*up* and *down*. Migrations are run in order of date ascending, hence filenames
like `2017_01_01_00000_create_tasks_table.php`.

Modifying or dropping a column requires `doctrine/dbal`.

When using SQLite, you can only drop or modify one column per migration closure.

`php artisan migrate` runs all outstanding migrations. Laravel keeps track of
which migrations have already been run.

`php artisan migrate:reset` rolls back all database migrations.

`php artisan migrate:status` shows the status of each migration, i.e. whether it
has been run or not.

`php artisan migrate --seed` will run a seeder along with the migration.

## Artisan

`php artisan make:model Club -m` creates a model with a migration.

`php artisan make:controller ClubsController --resource`

## tinker

`php artisan tinker` is a command line tool which allows you to run queries.

## File locations

Models: `app/Club.php`

Controllers: `app/Http/Controllers/ClubsController.php`

## Templates

By default Laravel supports PHP templates and its own templating system called
Blade. For developers who prefer Twig, the [TwigBridge](https://github.com/rcrowe/TwigBridge)
component provides a bridge which allows files ending `.twig` to be loaded
automatically.

### Blade

Defaults can be provided if a variable is not set: `{{ $title or 'Default' }}`
