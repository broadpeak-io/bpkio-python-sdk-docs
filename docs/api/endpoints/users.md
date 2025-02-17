# Users API

The Users API provides functionality to manage users in the broadpeak.io platform. This includes user creation, retrieval, and management operations.

## API Reference

::: bpkio_api.endpoints.users.UsersApi
    options:
      show_root_heading: true
      show_source: true
      members: true
      show_if_no_docstring: true

## Examples

```python
from bpkio_api import BroadpeakIoApi

# Initialize the client
client = BroadpeakIoApi(api_key="your-api-key")

# List all users
users = client.users.list()
for user in users:
    print(f"User: {user.email}")

# Get a specific user
user = client.users.retrieve("user-id")
```

## Related Models

See the [Users Models](../models/users.md) documentation for details about the data models used with this API. 