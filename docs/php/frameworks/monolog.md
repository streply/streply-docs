---
sidebar_position: 1
---

# Monolog

Streply Monolog Handler.

## Install

The first step is to download the `streply/streply-monolog` package using the composer.

```bash 
composer require streply/streply-monolog
```

- https://github.com/streply/streply-monolog
- https://packagist.org/packages/streply/streply-monolog

## Setup

Set up Monolog logger with Streply.

```php title="PHP" {8-10}
require __DIR__ . "/vendor/autoload.php";

use Monolog\Logger;
use Streply\Monolog\StreplyMonologHandler;

$logger = new Logger("example-app");
$logger->pushHandler(
    new StreplyMonologHandler(
        "https://clientPublicKey@api.streply.com/projectId"
    )
);
```

As a second parameter, you can set an array with optional parameters.

```php title="PHP" {5-6}
$logger->pushHandler(
    new StreplyMonologHandler(
        "https://clientPublicKey@api.streply.com/projectId",
        [
            'environment' => 'production',
            'release' => 'my-project-name@2.3.12',
        ]
    )
);
```

For more configuration options, see the [Configuration](/php/configuration) tab.

:::info
You can find the DSN code of the project in the Projects tab of your [Streply account](https://app.streply.com/projects).
:::

## Start logging

Use Monolog as always :)

```php title="PHP" 
$logger->error("Some error here");
$logger->info("Some user logged in", [
    'userName' => 'Joey'
]);
$logger->debug($sqlQuery);
```
