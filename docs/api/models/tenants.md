# Tenants Models

The Tenants models define the data structures used for managing tenants in the broadpeak.io platform.

## Models Reference

::: bpkio_api.models.Tenants
    options:
      show_root_heading: true
      show_source: true
      members: true
      show_if_no_docstring: true

## Usage Examples

```python
from bpkio_api.models.Tenants import Tenant

# Create a tenant object
tenant = Tenant(
    name="My Tenant",
    description="My tenant description",
    commercialPlan="STANDARD",
    # Add other required fields
)

# Access tenant properties
print(f"Tenant Name: {tenant.name}")
print(f"Commercial Plan: {tenant.commercialPlan}")
```

## Related Endpoints

See the [Tenants API](../endpoints/tenants.md) documentation for details about the available operations on tenants. 