# Quick Start Guide

This guide will help you get started with the broadpeak.io Python SDK.

It doesn't take much to work with the SDK, in particular if you're already familiar with the broadpeak.io APIs, and in particular the API reference tool in the [Knowledge Center](https://developers.broadpeak.io/docs/discover-api-reference).


```python
from bpkio_api import BroadpeakIoApi

client = BroadpeakIoApi(api_key="your-api-key")

# List all sources
sources = client.sources.list()
for source in sources:
    print(f"Source: {source.name}")

# Get a specific source
source = client.sources.retrieve('<id-of-the-source>')
```

## Next Steps

- Check out the [API Mapping](./api_mapping.md) to understand how the SDK maps the API to Python objects and methods.
- Learn about other mechanisms for authenticating with the SDK in the [Authentication](./authentication.md) guide.