# Symfony

## Quick start

```
composer create-project symfony/skeleton quick_start
cd quick_start
composer require sec-checker
composer require server --dev
composer require annotations
composer require twig
composer require asset
composer require form
composer require profiler --dev
```

## Directory structure

The default directory structure is:

 * `public`: Equivalent of `public_html` or `htdocs`. Contains the single front controller by default as `index.php`.
 * `config`: Configuration files.
 * `src`: All your PHP code.

## Routes

Although routes can be specified in various places, annotations are the recommended
way in 4.0.

Routes can be given a name and requirements:

```
/**
 * @Route("/data/{id}", name="data_show", requirements={"page"="\d+"})
 */
```

Route placeholder names (e.g. `id`) cannot start with a digit and have a maximum
length of 32 characters.

## Environments

Three environments: dev, prod and test.

Environment variables are loaded from `.env` if the `APP_ENV` variable isn't set.

## Debugging

`php bin/console debug:router`: List all routes.

## Basic controller

Note: `AbstractController` is preferred over `Controller` as the former is more
restrictive and does not allow you to call services directly.

```php
<?php

namespace App\Controller;

use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Annotation\Route;
use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;

class DefaultController extends AbstractController
{
  /**
   * @Route("/")
   */
  public function index()
  {
    return new Response('Hello World');
  }

  /**
   * @Route("/hello/{name}")
   */
  public function hello($name)
  {
    return $this->render("default/hello.html.twig", ['name' => $name]);
  }
}
```

## Query parameters

Query parameters can be accessed via the `Request` class:

```php
public function index(Request $request)
{
  // use $request
}
```

## Errors

For 404 responses, throw a `createNotFoundException`:

```php
throw $this->createNotFoundException('No such ID');
```

Throwing any `Exception` class will return a 500 response.
