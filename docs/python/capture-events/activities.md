---
sidebar_position: 3
---

# Activities

With the Activities method, you can measure any activity in the system that is critical to the functioning of the application or business.

The `activity` method consists of the following parameters:

- `(string) message` - Name of the activity
- `(object) params` - Parameters

To send an activity, e.g. a correct login to the system, simply call:

```python
from streply.capture import activity

activity('users.login')
```

For example, the ID of the logged-in user can be added as a parameter:

```python
from streply.capture import activity

activity('users.login', {
    'userId': 1
})
```
