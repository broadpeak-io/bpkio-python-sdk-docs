# Exceptions

The Exceptions module defines custom exceptions used throughout the broadpeak.io SDK for error handling.

## API Reference

::: bpkio_api.exceptions
    options:
      show_root_heading: true
      show_source: true
      members: true
      show_if_no_docstring: true

## Usage Examples

```python
from bpkio_api import BroadpeakIoApi
from bpkio_api.exceptions import (
    BroadpeakIoApiError,
    InvalidApiKeyFormat,
    InvalidTenantError,
    InvalidEndpointError
)

try:
    # Initialize with invalid API key
    client = BroadpeakIoApi(api_key="invalid-key")
    client.test_access()
except InvalidApiKeyFormat as e:
    print(f"Invalid API key format: {e}")
except BroadpeakIoApiError as e:
    print(f"API Error: {e}")
except InvalidTenantError as e:
    print(f"Tenant Error: {e}")
except InvalidEndpointError as e:
    print(f"Endpoint Error: {e}")
```

## Exception Hierarchy

- `BroadpeakIoApiError`: Base exception for all API-related errors
  - `InvalidApiKeyFormat`: Raised when the API key format is invalid
  - `InvalidTenantError`: Raised when there are issues with tenant configuration
  - `InvalidEndpointError`: Raised when trying to access an invalid or restricted endpoint 