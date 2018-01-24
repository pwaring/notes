# Symfony

## Quick start

```
composer create-project symfony/skeleton quick_start
cd quick_start
composer require sec-checker
composer require server --dev
composer require annotations
composer require twig
composer require profiler --dev
```

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
