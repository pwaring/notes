# Symfony and Git

**N.B.** This is a summarised version of [How to Create and store a Symfony2 Project in Git](http://symfony.com/doc/current/cookbook/workflow/new_project_git.html). You should read that article first to understand all the concepts, and then use these notes each time you want to quickly create a new Symfony project.

[Download](http://symfony.com/download) Symfony without vendors.

Extract file:

```
tar xzvf Symfony.tgz -C dest --strip-components=1
```

Create a `.gitignore` with the following contents:

```
web/bundles/
app/bootstrap*
app/cache/*
app/logs/*
vendor/
app/config/parameters.yml
composer.phar
```

Initialise git: `git init`

Add all files: `git add`

Commit: `git commit -m "Initial commit"`

Get composer: `wget https://getcomposer.org/composer.phar`

Install vendors: `php composer.phar install`
