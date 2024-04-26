---
sidebar_position: 1
---

# Quick start

Installing Streply is very easy, regardless of the structure of your project. It only takes 3 simple steps and in 5 minutes to activate Streply in your project.

## Install

```python
pip install --upgrade streply-sdk
```

- https://github.com/streply/streply-python
- https://pypi.org/project/streply-sdk/

## Initialization

Streply initialisations are performed using the `Streply` class, which should be placed at the very beginning of the code. The method receives the `(string) DSN` as the first parameter.

```python
from streply.streply import streply

streply('https://clientPublicKey@api.streply.com/projectId')
```

The second parameter is `(object) options`, which contains the optional [configuration](configuration).

```python
from streply.streply import streply

streply('https://clientPublicKey@api.streply.com/projectId', {
    'environment': 'local',
    'release': 'my-project-name@2.3.12',
})
```

:::info
You can find the DSN code of the project in the Projects tab of your [Streply account](https://app.streply.com/projects).
:::

## See more
- [Capture events](capture-events)
  - [Errors](capture-events/errors)
  - [Logs](capture-events/logs)
  - [Activities](capture-events/activities)
- [Configuration](configuration)
