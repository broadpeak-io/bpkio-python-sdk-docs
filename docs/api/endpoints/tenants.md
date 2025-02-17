# Tenants API

The Tenants API provides functionality to manage tenants in the broadpeak.io platform. This includes tenant information retrieval and management.

## API Reference

::: bpkio_api.endpoints.tenants.TenantsApi
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

# Get current tenant information
tenant = client.tenants.retrieve_self()
print(f"Tenant: {tenant.name}")
print(f"Commercial Plan: {tenant.commercialPlan}")
```

## Related Models

See the [Tenants Models](../models/tenants.md) documentation for details about the data models used with this API. 