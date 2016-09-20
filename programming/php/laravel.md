# Laravel

## Requirements

 * PHP 5.6.4
 * OpenSSL extension
 * PDO extension
 * MBstring extension
 * Tokenizer extension

## Installing Homestead

Clone from GitHub:

```bash
git clone https://github.com/laravel/homestead.git ~/dev/homestead
```

Run initialisation script:

```bash
cd ~/dev/homestead
bash ./init.sh
```

Edit `~/.homestead/Homestead.yaml`.

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

## Controllers

Create a controller by running:

```bash
php artisan make:controller StaticController
```

This will create a file:

```
app/Http/Controllers/StaticController.php
```
