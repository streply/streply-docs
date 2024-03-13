---
sidebar_position: 6
---

# CRON


In the [CRON](/product/cron) tab in the Streply app, we will display all commands marked as "CRON command" divided into the selected times. It's an easy way to see which CRON jobs were executed or which jobs failed.

If you use one of our official libraries for frameworks (for example [Laravel](/php/frameworks/laravel) or [Symfony](/php/frameworks/laravel)), Streply will catch CRON commands automatically.

But of course, you can do it manually:

```php
<?php

use Streply\Enum\EventFlag;

// ...

\Streply\withScope(function (\Streply\Scope $scope): void {
    $scope->setFlag(EventFlag::COMMAND);

    \Streply\Activity('test.command');
});
```