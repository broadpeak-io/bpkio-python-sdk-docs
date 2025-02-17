# Transcoding Profiles API

The Transcoding Profiles API provides functionality to manage transcoding profiles in the broadpeak.io platform. These profiles define how content is transcoded for different delivery scenarios.

## API Reference

::: bpkio_api.endpoints.transcoding_profiles.TranscodingProfilesApi
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

# List all transcoding profiles
profiles = client.transcoding_profiles.list()
for profile in profiles:
    print(f"Profile: {profile.name}")

# Get a specific profile
profile = client.transcoding_profiles.retrieve("profile-id")
```

## Related Models

See the [Transcoding Profiles Models](../models/transcoding_profiles.md) documentation for details about the data models used with this API. 