Symfony
=======

Concepts
--------

*Front Controller:* A single PHP file which handles every request coming into the application, usually `/index.php`. The front controller is always executed, and then the components of the URL are routed internally to the correct code. The three step process is:

 1. Execute front controller.
 2. Route request to relevant PHP function.
 3. Execute function and return a `Response` object.

Requirements
------------

 * PHP 5.3.8 (effectively Debian Wheezy)

Installation
------------

Download Composer:

    wget http://getcomposer.org/composer.phar
    
This must not be placed in the same directory as the code.

Download and install using Composer:

    php composer.phar create-project symfony/framework-standard-edition target-dir 2.3.7

Replace `2.3.7` with the latest version of Symfony and `target-dir` with the directory you want Symfony to be installed to.

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
