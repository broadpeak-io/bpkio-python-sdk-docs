# Sources Models

The Sources models define the data structures used for managing sources in the broadpeak.io platform.

## Source Types

::: bpkio_api.models.Sources
    options:
      members:
        - AdServerSource
        - AssetCatalogSource
        - AssetSource
        - LiveSource
        - OriginSource
        - SlateSource

## Source Input Models

::: bpkio_api.models.Sources
    options:
      members:
        - AdServerSourceIn
        - AssetCatalogSourceIn
        - AssetSourceIn
        - LiveSourceIn
        - SlateSourceIn
        - SourceIn

## Enums and Supporting Models

::: bpkio_api.models.Sources
    options:
      members:
        - SourceType
        - SourceSparse
        - SourceStatusCheckResult
        - AdServerQueryParameter
        - AdServerQueryParameterType
        - NamedModel

## Usage Examples

```python
from bpkio_api.models.Sources import (
    LiveSource,
    LiveSourceIn,
    SourceType,
    SourceStatusCheckResult
)

# Create a new live source
source = LiveSourceIn(
    name="Live Stream",
    description="Main live stream source",
    type=SourceType.HLS,
    url="https://example.com/stream.m3u8",
    tags=["live", "main"]
)

# The API will return a full LiveSource object
live_source = LiveSource(
    id="source-123",
    name=source.name,
    description=source.description,
    type=source.type,
    url=source.url,
    tags=source.tags,
    status=SourceStatusCheckResult.ACTIVE
)

# Access source properties
print(f"Source Name: {live_source.name}")
print(f"Source Type: {live_source.type}")
print(f"Source Status: {live_source.status}")
print(f"Source Tags: {', '.join(live_source.tags)}")
```

## Related Endpoints

See the [Sources API](../endpoints/sources.md) documentation for details about the available operations on sources. 