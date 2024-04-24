---
sidebar_position: 2
---

# Configuration

Configuration of the library is very simple, check out the options.

## Initialisation

Initialisation of Streply is performed using the `streply` class, which should be placed at the very beginning of the code. The method receives the `(string) dsn` as the first parameter.

:::info
You can find the DSN code of the project in the Projects tab of your [Streply account](https://app.streply.com/projects).
:::

```python
from streply.streply import streply

streply('https://clientPublicKey@api.streply.com/projectId')
```

The second, optional parameter of the `streply` constructor method is the `(object) options` in which optional settings can be defined.

Available options:

- `(string) environment` - Application environment
- `(string) release` - Project version

Example of the option's usage:

```python
from streply.streply import streply

streply('https://clientPublicKey@api.streply.com/projectId', {
    'environment': 'local',
    'release': 'my-project-name@2.3.12',
})
```

Also, you can change all options later:

```python
from streply.streply import streply

streply = streply('https://clientPublicKey@api.streply.com/projectId')

streply.set_option('environment', 'local')
streply.set_option('release', 'my-project-name@2.3.12')
```

## Adding user data

```python
from streply.streply import streply

streply = streply('https://clientPublicKey@api.streply.com/projectId')
streply.set_user('ID')

# with username
streply.set_user('ID', 'Joey')
```

or with parameters and name

```python
from streply.streply import streply

streply = streply('https://clientPublicKey@api.streply.com/projectId')
streply.set_user('ID', 'Joey', {
    'createdAt': '2022-11-10 15:10:32'
})
```