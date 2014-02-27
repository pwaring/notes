# Symfony

## Concepts

*Front Controller:* A single PHP file which handles every request coming into the application, usually `/index.php`. The front controller is always executed, and then the components of the URL are routed internally to the correct code. The three step process is:

 1. Execute front controller.
 2. Route request to relevant PHP function.
 3. Execute function and return a `Response` object.

## Requirements

 * PHP 5.3.8 (effectively Debian Wheezy)

## Installation

See the Symfony and Git (`git.md`) notes for information on setting up a basic install.

## Configuration

You may need to change configuration in:

    app/config/parameters.yml

Check configuration:

    php ./app/check.php

Starting the PHP built-in web server:

    php ./app/console server:run

Check that configuration also works under the web server:

    http://localhost:8000/config.php

Access application at:

    http://localhost:8000/app_dev.php
    
## File Permissions

At the bottom of `app/console`, `web/app.php` and `web/app_dev.php`, add:

```
umask(0000);
```

**N.B.** This is not ideal, nor thread-safe, but does not require Access Control List functionality in your filesystem (not always enabled by default).

## Creating a page

Two steps are required to add a new page:

 1. Create a route
 2. Create a controller

Before doing this, we need to create a bundle:

```
php app/console generate:bundle --namespace=Acme/HelloBundle --format=yml
```

This also places an in: `app/config/routing.yml`, which tells Symfony to look in the `Resources/config/routing.yml` file of the bundle for routing information.

Add a new route to `src/Acme/HelloBundle/Resources/config/routing.yml`:

```
hello:
  path: /hello/{name}
  defaults: { _controller: AcmeHelloBundle:Hello:index }
```

To create a controller which can use templates, it must extend the `Controller` class:

```
namespace Acme\HelloBundle\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\Controller;

class HelloController extends Controller
{
  public function indexAction($name)
  {
    return $this->render('AcmeHelloBundle:Hello:index.html.twig', array('name' => $name));
  }
}
```

The Twig template file can be found in: `Acme/HelloBundle/Resources/views/Hello/index.html.twig`.

## Requests and Responses

The `Request` class abstracts a HTTP request:

    use Symfony\Component\HttpFoundation\Request;
    
    $request = Request::createFromGlobals();
    $request->getPathInfo();
    $request->getMethod();
    $request->isSecure();

The `Response` class abstract a HTTP response:

    use Symfony\Component\HttpFoundation\Response;
    
    $response = new Response();
    $response->setStatusCode(Response::HTTP_OK);
    $response->send();

The `HttpFoundation` component, which includes `Request` and `Response`, can be used as a standalone component in other projects independent of Symfony.

## Request Flow

Each request is processed as follows:

 1. Execute front controller- `/index.php`.
 1. Route request to PHP function based on parameters, method etc.
 1. Execute PHP function which creates and returns an appropriate `Response` object.


