---
sidebar_position: 6
---

# CRON


In the [CRON](/product/cron) tab in the Streply app, we will display all commands marked as "CRON command" divided into the selected times. It's an easy way to see which CRON jobs were executed or which jobs failed.

If you use one of our official libraries for frameworks, Streply will catch CRON commands automatically.

But of course, you can do it manually:

```python
from streply.capture import log
from streply.streply import streply
from streply.enum.flags import flag
from streply.scope import configure_scope

# ...

with configure_scope() as scope:
    scope.set_flag(flag.COMMAND)
    log('test-command')
```