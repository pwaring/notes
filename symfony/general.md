# Symfony

## Concepts

*Front Controller:* A single PHP file which handles every request coming into the application, usually `/index.php`. The front controller is always executed, and then the components of the URL are routed internally to the correct code. The three step process is:

 1. Execute front controller.
 2. Route request to relevant PHP function.
 3. Execute function and return a `Response` object.

## Requirements

 * PHP 5.3.8 (effectively Debian Wheezy)

## Installation

Download Composer:

    wget http://getcomposer.org/composer.phar
    
This must not be placed in the same directory as the code.

Download and install using Composer:

    php composer.phar create-project symfony/framework-standard-edition target-dir 2.4.*

Replace `2.4.*` with the latest version of Symfony and `target-dir` with the directory you want Symfony to be installed to.

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


