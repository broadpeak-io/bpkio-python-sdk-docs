# Models Overview

The broadpeak.io Python SDK uses Pydantic models to represent various resources and ensure type safety and validation. Each model corresponds to a specific resource type in the broadpeak.io API.

## Available Models

- [Sources](sources.md)
- [Services](services.md)
- [Categories](categories.md)
- [Transcoding Profiles](transcoding_profiles.md)
- [Users](users.md)
- [Tenants](tenants.md)
- [Consumption](consumption.md)

## Common Models

The Common models define shared data structures used across different parts of the broadpeak.io platform.

::: bpkio_api.models.common
    options:
      show_root_heading: true
      show_source: true
      members: true
      show_if_no_docstring: true

## Related Documentation

These models are used throughout the SDK. See the specific endpoint and model documentation for details about how they are used in different contexts. 