---
sidebar_position: 1
---

# Quick start

Installing Streply is very easy, regardless of the structure of your project. It only takes 3 simple steps and in 5 minutes to activate Streply in your project.

## Install

At the very beginning, you need to download a library for PHP. The recommended way is to download Streply using Composer. You can also download the actual zip package from our page on GitHub.

:::info
You can find the DSN code of the project in the Projects tab of your [Streply account](https://app.streply.com/projects).
:::

```bash
composer require streply/streply-php
```

- https://github.com/streply/streply-php
- https://packagist.org/packages/streply/streply-php

## Configure

Streply initialisations are performed using the `Initialize` method, which should be placed at the very beginning of the code (e.g. in the index.php file). The method receives the `(string) DSN` as the first parameter.

The second parameter is `(array) $options`, which contains the optional [configuration](configuration).

You can find the DSN code of the project in the projects tab in your Streply account.

```php
Streply\Initialize('https://clientPublicKey@api.streply.com/projectId');
```

For more configuration options, see the [**Configuration**](configuration) tab.

## First usage

Passing an exception to Streply is very simple. Simply call the `Streply\Exception` method in the catch instruction and pass the entire exception object to it.

```php {8} title="PHP"
try {
    if(true) {
        throw new \Exceptions\SomeException('Exception message here');
    }
} catch(\Throwable $exception) {
    Streply\Exception($exception);
}
```

For more information on catching errors, see the [**Capture errors**](capture-events/errors) page.

## Using a framework?
- [Monolog](frameworks/monolog)
- [Laravel](frameworks/laravel)
- [Symfony](frameworks/symfony)