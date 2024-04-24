---
sidebar_position: 2
---

# Logs

The Logs method allows all information that is neither an error, not an activity to be logged.

The `log` method consists of 2 parameters:

- `(string) message` - Name of the activity
- `(object) params` - Parameters

```python
from streply.capture import log

log('A log message')
```

If you want, you can use `logging` module:

```python
from streply.utils import logger

logger.debug("A debug message")
logger.info("An info message")
logger.warning("A warning message")
logger.error("An error message")
logger.critical("A critical message")
```

As a second parameter, we can add additional information that is important to us and not present in the error object (e.g. user ID).

For example, a failure message can be added as a parameter:

```python {4}
from streply.utils import logger

logger.info("A info message", {
    'message': message
})
```

## Logs formatting

:::tip See how to [format logs](/logs-formatting). 