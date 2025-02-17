# Consumption API

The Consumption API provides functionality to retrieve and analyze content consumption data in the broadpeak.io platform.

## API Reference

::: bpkio_api.endpoints.consumption.ConsumptionApi
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

# Get consumption data
consumption_data = client.consumption.list()
for data in consumption_data:
    print(f"Consumption: {data}")
```

## Related Models

See the [Consumption Models](../models/consumption.md) documentation for details about the data models used with this API. 