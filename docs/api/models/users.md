# Users Models

The Users models define the data structures used for managing users in the broadpeak.io platform.

## Models Reference

::: bpkio_api.models.Users
    options:
      show_root_heading: true
      show_source: true
      members: true
      show_if_no_docstring: true

## Usage Examples

```python
from bpkio_api.models.Users import User

# Create a new user object
user = User(
    email="user@example.com",
    # Add other required fields
)

# Access user properties
print(f"User Email: {user.email}")
```

## Related Endpoints

See the [Users API](../endpoints/users.md) documentation for details about the available operations on users. 