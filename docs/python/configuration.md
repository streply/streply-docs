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

## Scopes

The scope helper will set up the scope for all events captured by the Streply SDK.

```python
from streply.capture import log
from streply.streply import streply
from streply.scope import configure_scope

# ...

with configure_scope() as scope:
    scope.set_channel('my-chanel')
    log('test-command')
```

If you want to change the scope for a all events, you can mark scope as global:

```python
from streply.capture import log
from streply.streply import streply
from streply.scope import configure_scope

# ...

with configure_scope() as scope:
    scope.set_global_scope(True)
    scope.set_channel('my-chanel')
    
log('test-command')

# ...

error('test-command')
```

Available methods in scope:

- `scope.set_global_scope(bool)` - Setting is global scope
- `scope.set_channel(string channel)` - Setting event channel
- `scope.set_flag(string flag)` - Setting event flag
- `scope.set_release(string release)` - Setting project release
- `scope.set_environment(string environment)` - Setting project environment
- `scope.set_url(string url)` - Setting project URL

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