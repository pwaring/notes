Symfony
=======

Concepts
--------

*Front Controller:* A single PHP file which handles every request coming into the application, usually `/index.php`. The front controller is always executed, and then the components of the URL are routed internally to the correct code. The three step process is:

 1. Execute front controller.
 2. Route request to relevant PHP function.
 3. Execute function and return a `Response` object.

Installation
------------

Download Composer:

    curl -sS https://getcomposer.org/installer | php
    
This must not be placed in the same directory as the code.

Download and install using Composer:

    php composer.phar create-project symfony/framework-standard-edition . 2.3.1

Replace `2.3.1` with the latest version of Symfony.

May need to change configuration in:

    app/config/parameters.yml

Check configuration:

    php ./app/check.php

Starting the PHP built-in web server:

    php ./app/console server:run

Access application at:

    http://localhost:8000/app_dev.php
