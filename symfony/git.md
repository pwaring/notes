# Symfony and Git

**N.B.** This is a summarised version of [How to Create and store a Symfony2 Project in Git](http://symfony.com/doc/current/cookbook/workflow/new_project_git.html) and [How to remove the AcmeDemoBundle](http://symfony.com/doc/current/cookbook/bundles/remove.html). You should read those articles first to understand all the concepts, and then use these notes each time you want to quickly create a new Symfony project.

[Download](http://symfony.com/download) Symfony without vendors.

Extract file:

```
tar xzvf Symfony.tgz -C dest --strip-components=1
```

## Removing the AcmeDemoBundle

Remove reference to `Acme\DemoBundle\AcmeDemoBundle` in `app/AppKernel.php`

Remove references to `AcmeDemoBundle` in `app/config/routing_dev.yml`.

Remove references to `demo` rules in `app/config/security.yml`.

Remove `src/Acme/`.

## Set up Git

Create a `.gitignore` with the following contents:

```
web/bundles/
app/bootstrap*
app/cache/*
app/logs/*
vendor/
app/config/parameters.yml
composer.phar
UPGRADE*.md
```

Initialise git: `git init`

Add all files: `git add *`

Commit: `git commit -m "Initial commit"`

Get composer: `wget https://getcomposer.org/composer.phar`

Install vendors: `php composer.phar install`

### GitHub integration

If you want to integrate with GitHub, create a new repository through the web interface and then run the following commands in your project directory:

```
git remote add origin git@github.com:username/repository.git
git push -u origin master
```

Replace `username` with your GitHub username and `repository` with the name of the repository.

