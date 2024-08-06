# runapy

This project provides a Python client to interact with the [Run:ai REST API](https://app.run.ai/api/docs).

 The client offers:
- A single classs interface to perform all API actions
- Body scheme validation on compilation (with Pydantic)
- Static type checks
- Retry mechanism for resiliency on intermittent network errors
- Debug messages flag

## Requirements:
 - Run:ai control-plane version of 2.18 and above
 - Python version of 3.11 or above
 - [Run:ai Client Application](https://docs.run.ai/v2.13/developer/rest-auth/#create-a-client-application)

 #### Note on token and permissions
When creating an application, it is important to select the relevant role and scope for the required API actions.\
Some API calls may fail with 403 if the application token has no sufficient permissions.

## Installation

runapy is avaialble in PyPi and can be downloaded directly as a python package
```bash
pip3 install runapy
```

Or you can clone the repo and run it with [poetry](https://python-poetry.org/docs/):
```bash
git clone https://github.com/ofir-eldar1/runapy
poetry install
poetry run python3 main.py

```
## Client

RunaiClient is the only class required to interact with the Run:ai REST API https://app.run.ai/api/docs

```python
import runai

client = runai.RunaiClient(
            realm="myorgrealm",
            client_id="API"
            client_secret="clientsecret",
            runai_base_url="https://myorg.run.ai",
            cluster_id="513423qx-127t-4yk6-979g-5po843g37e2b",
            retries=3,
            debug=False
    )
```
| Parameter | Type     | Description                       |
| :-------- | :------- | :-------------------------------- |
| `realm`      | `string` | **Required**: Can be obtained from the UI login screen at your Run:ai domain app.run.ai -> app.run.ai/auth/realms/<realm>|
| `client_id`      | `string` | **Required**: The Run:ai application name |
| `client_secret`      | `string` | **Required**: The Run:ai application password |
| `runai_base_url`      | `string` | **Required**: The URL used to access Run:ai UI|
| `retries`      | `int` | **Required**: Number of retries to attempt on each failed API call for 5xx errors |
| `debug`      | `bool` | **Optional**: Debug mode output |

## Examples
See examples [here](examples/)

## Warranty
This package is not maintained by the Run:ai product.

For any issues and requests, please open an issue, or contact the authors of this package.

## Contributing
Contributions are welcome! Please fork the repository and submit a pull request with your changes.

## License
This project is licensed under the MIT License. 
See the LICENSE file for details.