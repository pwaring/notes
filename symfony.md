Symfony
=======

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
