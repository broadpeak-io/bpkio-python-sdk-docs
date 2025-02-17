# Caching

The Caching module provides functionality to cache API responses, improving performance by reducing unnecessary API calls.

## API Reference

::: bpkio_api.caching
    options:
      show_root_heading: true
      show_source: true
      members: true
      show_if_no_docstring: true

## Usage Examples

```python
from bpkio_api import BroadpeakIoApi
from bpkio_api.caching import init_cache

# Initialize the cache for a specific tenant
init_cache("api.broadpeak.io", "tenant-id")

# Use caching with the client
client = BroadpeakIoApi(
    api_key="your-api-key",
    use_cache=True  # Enable caching (default)
)

# First call will hit the API
sources = client.sources.list()

# Second call will use the cache
sources = client.sources.list()  # Returns cached data
```

## Cache Configuration

The cache is automatically configured when you initialize the `BroadpeakIoApi` client. You can control caching behavior through the `use_cache` parameter when creating the client. 