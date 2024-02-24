---
sidebar_position: 3
---


# Symfony

The official Streply library for the Symfony framework.

## Install

The first step is to download the `streply/streply-symfony` package using the composer.

```bash
composer require streply/streply-symfony
```

- https://github.com/streply/streply-symfony
- https://packagist.org/packages/streply/streply-symfony

## Enable the bundle

Add the bundle to the list of registered bundles in `config/bundles.php`.

```php title="PHP" {3}
return [
    ...
    Streply\StreplyBundle\StreplyBundle::class => ['all' => true]
];
```

## Configuration

Add default configuration in `config/packages/streply.yaml`.

```bash
streply:
    dsn: '%env(STREPLY_DSN)%'
```

Then add your DSN to `.env` file.

```bash
###> streply/streply-bundle ###
STREPLY_DSN="https://clientPublicKey@api.streply.com/projectId"
###< streply/streply-bundle ###
```

:::info
You can find the DSN code of the project in the Projects tab of your [Streply account](https://app.streply.com/projects).
:::

## Optional configuration

If you want to set some additional configuration, you need to create an event listener and use the `Streply\Configuration::filterBeforeSend();` method in the `onKernelException` method in `ExceptionListener`.

:::info
Read more about events in symfony [here](https://symfony.com/doc/current/event_dispatcher.html) and about Streply configuration [here](/php/configuration).
:::



```php title="src/EventListener/ExceptionListener.php"
<?php
namespace App\EventListener;

use Symfony\Component\HttpKernel\Event\ExceptionEvent;

class ExceptionListener
{
    public function onKernelException(ExceptionEvent $event)
    {
        \Streply\Configuration::filterBeforeSend(function(\Streply\Entity\Event $event) {
            if($event->getMessage() === 'someMessage') {
                return false;
            }

            return true;
        });
    }
}
```
