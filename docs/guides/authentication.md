# Authentication Guide

This guide provides detailed information about the various authentication methods available in the broadpeak.io Python SDK.

## Overview

The broadpeak.io Python SDK supports multiple authentication methods to accommodate different use cases and deployment scenarios. You can authenticate using:

1. API Keys
2. Environment Variables
3. Tenant profiles defined in a file

## Authentication Methods

### 1. Using API Keys

The most direct way to authenticate is using an API key:

```python
api = BroadpeakIoApi(api_key="your-api-key")
```

You can create an API key [in the broadpeak.io dashboard](https://app.broadpeak.io/account-settings/api-keys). For more information, check the [broadpeak.io Knowledge Center](https://developers.broadpeak.io/docs/api-pre-requisites).

If you are using a specific broadpeak.io platform, you will need to specify the specific domain name for that platform.

``` python
api = BroadpeakIoApi(
    api_key="your-api-key",
    fqdn="api.broadpeak.io"  # (1)!
)
```

1.  Replace with the specific domain name for the platform you are using

!!! tip 
    You can also provide the URL of the broadpeak.io web app, and the SDK will automatically use the correct API endpoint.

```python
api = BroadpeakIoApi(
    api_key="your-api-key",
    fqdn="https://app.broadpeak.io"  # (1)!
)
```

1.  Replace with the specific domain name for the platform you are using

### 2. Using Environment Variables

The SDK can automatically pick up credentials from environment variables:

```bash
# Set environment variables before initializing
export BPKIO_API_KEY="your-api-key"
export BPKIO_FQDN="api.broadpeak.io"  # (1)! 
```

1. Optional, replace with the specific domain name for the platform you are using

```python
# Initialize without parameters
api = BroadpeakIoApi()
```

### 3. Using the `tenants` file

This option is useful if you have multiple tenants and want to switch between them easily. You can keep credentials for each tenant in a file and simply use the tenant label.

To do this, create (or modify) the file in ~/.bpkio/tenants, and add a section within it:

```ini
[my_tenant]
api_key = "your-api-key"
```

Then, you can initialize the SDK with the tenant profile:

```python
api = BroadpeakIoApi(tenant="my_tenant")
```

!!! note
    This file is also used by the `bic` CLI tool to switch between tenants. So you can also simply add a tenant with the `bic config tenant add` command, and then use it with the SDK.

!!! warning
    You cannot specify both a tenant and an API key simultaneously - this will raise an exception.

You can also set the `BPKIO_TENANT` environment variable to the tenant label, and the SDK will use it automatically.

```bash
export BPKIO_TENANT="my_tenant"
```

```python
api = BroadpeakIoApi()
```

Finally, as a fallback, you can also define a default tenant in the `tenants` file, and then use it with the SDK without specifying the tenant label.

```ini
[default]
api_key = "your-api-key"
```

Then, you can initialize the SDK without specifying the tenant label:

```python
api = BroadpeakIoApi()
```

### 4. Using a TenantProfile object

For more complex scenarios, you can use a TenantProfile object:

```python
from bpkio_api.credential_provider import TenantProfile

# Create a tenant profile
profile = TenantProfile(
    label="mytenant",
    id="your-tenant-id",
    api_key="your-api-key",
    fqdn="api.broadpeak.io"  # (1)!
)

# Initialize with the tenant profile
api = BroadpeakIoApi(tenant=profile)
```

1. Optional, replace with the specific domain name for the platform you are using

## Order of Precedence

The order of precedence for authentication is:

1. explicitly provided Tenant Profile (with the `tenant` parameter)
2. explicitly provided API Key (with the `api_key` parameter)
3. Environment Variable `BPKIO_TENANT`
4. Environment Variable `BPKIO_API_KEY`
5. Default Tenant Profile from the `tenants` file


## Verifying Authentication

After initializing the SDK, you can verify your authentication by getting the current tenant information:

```python
# Get current tenant information
tenant = api.get_self_tenant()
print(f"Connected as tenant: {tenant.name}")
print(f"Tenant ID: {tenant.id}")
```


## Error Handling

The SDK includes several authentication-related exceptions:

```python
from bpkio_api.exceptions import (
    AccessForbiddenError,
    InvalidApiKeyFormat,
    BroadpeakIoHelperError
)

try:
    api = BroadpeakIoApi(api_key="invalid-key")
    api.sources.list()
except InvalidApiKeyFormat as e:
    print("The API key format is invalid")
except AccessForbiddenError as e:
    print(f"Access forbidden: {e.status_code}")
except BroadpeakIoHelperError as e:
    print("An error occurred with the API helper")
```

## Best Practices

1. **Environment Variables**: For production deployments, in particular for automation, using environment variables is recommended as it keeps credentials out of your code.
2. **API Keys**: Keep your API keys secure and never commit them to version control.
3. **Custom FQDN**: If you're using a dedicated broadpeak.io platform, make sure to set it during initialization rather than using the default.
4. **Error Handling**: Always implement proper error handling for authentication-related exceptions.

## Next Steps

- Check out the [Quickstart Guide](./quickstart.md) for basic usage examples
- Learn about the available [API Endpoints](../api/index.md)
