# Symfony

## Quick start

```
composer create-project symfony/skeleton quick_start
cd quick_start
composer require server --dev
composer require annotations
composer require twig
composer require profiler
```


## Environments

Three environments: dev, prod and test.

Environment variables are loaded from `.env` if the `APP_ENV` variable isn't set.
