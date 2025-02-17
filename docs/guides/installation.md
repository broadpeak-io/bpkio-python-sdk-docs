# Installation Guide

## Using Poetry (Recommended)

The recommended way to install the SDK is using Poetry:

```bash
poetry add bpkio-python-sdk
```

## Using pip

You can also install the package using pip:

```bash
pip install bpkio-python-sdk
```

## Development Installation

If you want to contribute to the SDK or install it for development:

1. Clone the repository:
   ```bash
   git clone https://github.com/broadpeak/bpkio-python-tools.git
   cd bpkio-python-tools
   ```

2. Install dependencies using Poetry:
   ```bash
   cd bpkio-python-sdk
   poetry install
   ```

3. Activate the virtual environment:
   ```bash
   poetry shell
   ```

## Verifying Installation

You can verify the installation by running Python and importing the package:

```python
from bpkio_api import BpkioClient

# Create a client instance
client = BpkioClient(api_key="your-api-key")
```

If no errors occur, the installation was successful. 