# Sources API

The Sources API provides functionality to manage sources in the broadpeak.io platform. Sources represent the input content that can be processed and delivered through the platform.

::: bpkio_api.endpoints.sources.SourcesApi

## Methods

### list

List all available sources.

**Parameters:**

| Name | Type | Required | Description |
|------|------|----------|-------------|
| filter | str | No | Filter string to apply to the list |
| offset | int | No | Number of items to skip |
| limit | int | No | Maximum number of items to return |

**Returns:**

| Type | Description |
|------|-------------|
| List[Source] | List of Source objects |

### retrieve

Retrieve a specific source by ID.

**Parameters:**

| Name | Type | Required | Description |
|------|------|----------|-------------|
| source_id | str | Yes | ID of the source to retrieve |

**Returns:**

| Type | Description |
|------|-------------|
| Source | The requested Source object |

### create

Create a new source.

**Parameters:**

| Name | Type | Required | Description |
|------|------|----------|-------------|
| source | Source | Yes | Source object containing the source details |

**Returns:**

| Type | Description |
|------|-------------|
| Source | The created Source object |

### update

Update an existing source.

**Parameters:**

| Name | Type | Required | Description |
|------|------|----------|-------------|
| source_id | str | Yes | ID of the source to update |
| source | Source | Yes | Source object containing the updated details |

**Returns:**

| Type | Description |
|------|-------------|
| Source | The updated Source object |

### delete

Delete a source.

**Parameters:**

| Name | Type | Required | Description |
|------|------|----------|-------------|
| source_id | str | Yes | ID of the source to delete |

**Returns:**

| Type | Description |
|------|-------------|
| None | - |

## Examples

```python
from bpkio_api import BroadpeakIoApi

# Initialize the client
client = BroadpeakIoApi(api_key="your-api-key")

# List all sources with pagination
sources = client.sources.list(
    limit=10,
    offset=0,
    filter="name:test*"
)
for source in sources:
    print(f"Source: {source.name}")

# Get a specific source
source = client.sources.retrieve("source-id")

# Create a new source
from bpkio_api.models.Sources import Source, SourceType
new_source = Source(
    name="my-source",
    description="My source description",
    type=SourceType.HLS,
    url="https://example.com/stream.m3u8"
)
created_source = client.sources.create(new_source)

# Update a source
source.description = "Updated description"
updated_source = client.sources.update(source.id, source)

# Delete a source
client.sources.delete("source-id")
```

## Related Models

See the [Sources Models](../models/sources.md) documentation for details about the data models used with this API. 