# Credential Provider

The Credential Provider module handles tenant profiles and API key management in the broadpeak.io SDK.

## API Reference

::: bpkio_api.credential_provider
    options:
      show_root_heading: true
      show_source: true
      members: true
      show_if_no_docstring: true

## Usage Examples

```python
from bpkio_api.credential_provider import TenantProfileProvider

# Create a tenant profile provider
provider = TenantProfileProvider()

# Check if there's a default tenant
if provider.has_default_tenant():
    # Get the default tenant profile
    default_tenant = provider.get_tenant_profile("default")
    print(f"Default Tenant API Key: {default_tenant.api_key}")

# Get a specific tenant profile
tenant = provider.get_tenant_profile("my-tenant")
``` 