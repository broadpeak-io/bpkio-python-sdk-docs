# Transcoding Profiles Models

The Transcoding Profiles models define the data structures used for managing transcoding profiles in the broadpeak.io platform.

## Models Reference

::: bpkio_api.models.TranscodingProfiles
    options:
      show_root_heading: true
      show_source: true
      members: true
      show_if_no_docstring: true

## Usage Examples

```python
from bpkio_api.models.TranscodingProfiles import TranscodingProfile

# Create a new transcoding profile
profile = TranscodingProfile(
    name="my-profile",
    description="My transcoding profile",
    # Add other required fields
)

# Access profile properties
print(f"Profile Name: {profile.name}")
print(f"Profile Description: {profile.description}")
```

## Related Endpoints

See the [Transcoding Profiles API](../endpoints/transcoding_profiles.md) documentation for details about the available operations on transcoding profiles. 