# Services Models

The Services models define the data structures used for managing services in the broadpeak.io platform.

## Models Reference

::: bpkio_api.models.Services
    options:
      show_root_heading: true
      show_source: true
      members: true
      show_if_no_docstring: true

## Usage Examples

```python
from bpkio_api.models.Services import Service

# Create a new service
service = Service(
    name="my-service",
    description="My service description",
    # Add other required fields
)

# Access service properties
print(f"Service Name: {service.name}")
print(f"Service Description: {service.description}")
```

## Related Endpoints

See the [Services API](../endpoints/services.md) documentation for details about the available operations on services. 