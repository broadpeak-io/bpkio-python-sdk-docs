# Mapping the API

The broadpeak.io Python SDK maps the broadpeak.io API to Python objects and methods.

This page describes the principles used to define that mapping.

## Endpoint path mapping

The bpkio_api object is the main object in the SDK. It provides access to all the resources and operations available in the broadpeak.io platform.

It maps all broadpeak.io API endpoint paths to chains of sub-objects. For example, for top-level endpoints, you will do:

```python

# API: /sources
sources = client.sources.list()

# API: /services
services = client.services.list()

# API: /transcoding-profiles
transcoding_profiles = client.transcoding_profiles.list()
```

And as you navigate deeper into the API, the same continues to apply:

```python

# API: /sources/live
live_sources = client.sources.live.list()

# API: /services/virtual-channel
virtual_channels = client.services.virtual_channel.list()
```

!!! tip
    The object names follow the Python "snake_case" naming conventions. So, dashes (`-`) are converted to underscores (`_`). For example, the `virtual-channel` endpoint is mapped to the `virtual_channel` sub-object.

When a resource identifier has to be passed in the path to get access to sub-resources, you will pass it as a keyword argument to the sub-object:

```python
# API: /services/virtual-channel/{serviceId}/slots
virtual_channel_slots = client.services.virtual_channel.slots.list(service_id='<id-of-the-service>")
```

!!! tip
    Here again, the snake_case naming convention is respected, so the `serviceId` needs to be passed as `service_id` in the parameter list.

## Endpoint method mapping

### Basic methods

When working with broadpeak.io resources, the SDK provides a 1:1 mapping of the HTTP methods to Python methods.

| HTTP Method | Description | Python Method |
|-------------|-------------|---------------|
| `GET` | retrieve a list of resources | `list` |
| `GET` | retrieve a single resource | `retrieve` |
| `POST` | create a resource | `create` |
| `PUT` | update a resource | `update` |
| `DELETE` | delete a resource | `delete` |

```python
api = BroadpeakIoApi()

# List all sources
sources = api.sources.list()

# Create a new source
new_source = LiveSourceIn(name="My new source", url="https://example.com/stream.m3u8")
new_source = api.sources.live.create(new_source)

# Get a specific source
old_source = api.sources.live.retrieve('<id-of-the-source>')

# Delete a source
api.sources.live.delete(old_source.id)
```

### List

Note that the `list` method does automatically handle pagination, so you don't need to worry about it.
If you need to work with the raw pagination data, you can access it via the `_get_page` method.

### Retrieve

To retrieve a particular resource (source or service) with the broadpeak.io API requires knowing the particular type of resource. 

To make life easier, the SDK does allow you to perform the `retrieve` method on the top-level resource. The object returned will be the appropriate model.

```python
source = api.sources.retrieve('<id-of-the-source>')
```
is equivalent (assuming that the source is a live source) to:

```python
source = api.sources.live.retrieve('<id-of-the-live-source>')
```


### High-order methods

The SDK also provides high-order methods that can be used to work with resources, providing convenience mechanisms for a number of common operations where multiple API calls are required.

| Method | Description |
|--------|-------------|
| `count` | Count the number of resources |
| `search` | Filter the list of resources matching specific criteria |
| `search_by_type` | Filter the list of resources for a particular type |
| `upsert` | Create, retrieve or update a resource |

#### Search / Filter

The `search` method can be used to filter the list of resources:

It takes the following parameters:

- `value`: The value to search for.
- `field`: The field to search in.
- `method`: The method to use for the search.
    - `STRICT`: Strict match.
    - `STRING_MATCH`: Exact string match, but also works with enum values.
    - `STRING_SUB`: Partial string match.


```python
# Search for services with a name containing "My"
sources = api.services.search(
    value="My", 
    field="name", 
    method=SearchMethod.STRING_CONTAINS)

# Search for sources with a URL containing "example.com"
sources = api.sources.search(
    value="example.com", 
    field="url", 
    method=SearchMethod.STRING_CONTAINS)
```

If you need to apply multiple filters, you can do so by passing a list of tuples to the `filters` parameter.

```python
# Search for all enabled services with a name containing "AVOD"
services = api.services.search(filters=[
    ("AVOD", "name", SearchMethod.STRING_CONTAINS),
    ("enabled", "state", SearchMethod.STRICT)
])
```

Finally, since it's a fairly common operation, the SDK provides a helper method to search for resources by type.

```python
# Search for all live sources
live_sources = api.sources.search_by_type(type=SourceType.LIVE)
```

#### Upsert

The `upsert` method is a convenience method that can be used to create, retrieve or update a resource, based on its existence in the platform.

- If the resource does not exist, it will be created.
- If the resource exists, the behaviour depends on the `if_exists` parameter.
    - If set to `error`: Raises an error if the resource already exists.
    - If set to `retrieve`: Retrieves the resource unchanged if it exists.
    - If set to `update`: Updates the resource if it exists then returns the updated resource.

Unlike other methods, the `upsert` method returns a tuple with the resource and the operation performed.

```python
# Create a new source
new_source = LiveSourceIn(name="My new source", url="https://example.com/stream.m3u8")
new_source, operation = api.sources.live.upsert(new_source)
```

The `operation` will be an enum value from the `UpsertOperationType` enum.

- `CREATED`: The resource was created.
- `RETRIEVED`: The resource was retrieved.
- `UPDATED`: The resource was updated.
- `ERROR`: An error occurred.

### Resource-specific methods

There are some methods that are specific to a particular resource type. For example, the `services` resource provides a `pause` and `unpause` methods.

```python
# Pause a service
api.services.pause('<id-of-the-service>')

# Unpause a service
api.services.unpause('<id-of-the-service>')
```

Check the [API reference](../../api/endpoints/#endpoints-overview) for the list of resource-specific methods.


## Models

The SDK provides a model for each of the resources available in the broadpeak.io API.

Every method that returns a resource or list of resource will parse the response JSON into the appropriate model.

```python
# Get a specific source
source = api.sources.live.retrieve('<id-of-the-source>')

print(f"Source Name: {source.name}")
print(f"Source ID: {source.id}")
print(f"Source URL: {source.url}")
```

The list of models can be found in [the API reference](../../api/models/#models-overview).





