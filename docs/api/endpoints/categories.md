# Categories API

The Categories API provides functionality to manage categories in the broadpeak.io platform. Categories help organize and group content.

## API Reference

::: bpkio_api.endpoints.categories.CategoriesApi
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

# List all categories
categories = client.categories.list()
for category in categories:
    print(f"Category: {category.name}")

# Get a specific category
category = client.categories.retrieve("category-id")
```

## Related Models

See the [Categories Models](../models/categories.md) documentation for details about the data models used with this API. 