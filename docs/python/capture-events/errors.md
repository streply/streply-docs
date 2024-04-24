---
sidebar_position: 1
---

# Errors

The most important function of Streply is to catch errors and exceptions from the application. 
The integration is very simple, just calling one method in the except instruction.

## Exceptions

Forwarding an exception to Streply is very easy, just call the `exception` method from `streply.capture` in the `except` condition and pass the entire exception object to it.

```python {6}
from streply.capture import exception

try:
    raise NotImplementedError("Not implemented error")
except Exception as e:
    exception(e)
```

Streply will also capture unhandled exception:

```python {6}
raise ValueError("Sorry, no numbers below zero")
```

As a second parameter, we can add additional information that is important to us and not present in the error object (e.g. user ID).

```python {7}
from streply.capture import exception
from streply.enum.level import level

try:
    raise NotImplementedError("Not implemented error")
except Exception as e:
    exception(e, {"paramName": "paramValue"}, level.CRITICAL)
```

The third parameter is the error level, which means how important it is. By default, each error takes the value `level.NORMAL`.

## Errors

If you need, you can send the error event manually:

```python 
from streply.capture import error

error('Custom error')
```

## Errors levels

Available error levels:

```python
from streply.enum.level import level

level.LOW
level.NORMAL
level.HIGH
level.CRITICAL
```

:::tip
Based on the error level, we can set notifications and search criteria (e.g. show errors with a critical level).
:::

