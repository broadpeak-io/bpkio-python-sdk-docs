# Services API

The Services API provides functionality to manage services in the broadpeak.io platform. Services define how content is processed and delivered to end users.

## API Reference

::: bpkio_api.endpoints.services.ServicesApi
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

# List all services
services = client.services.list()
for service in services:
    print(f"Service: {service.name}")

# Get a specific service
service = client.services.retrieve("service-id")

# Create a new service
from bpkio_api.models.Services import Service
new_service = Service(
    name="my-service",
    description="My service description",
    # Add other required fields
)
created_service = client.services.create(new_service)
```

## Related Models

See the [Services Models](../models/services.md) documentation for details about the data models used with this API. 