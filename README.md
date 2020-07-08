# python-saxo
Python OpenAPI wrapper for Saxo Bank

### You'll need  
* Python 3.4 or above
* [requests](https://requests.readthedocs.io/en/master/) for Python
* [Saxo Developer Account](https://www.developer.saxo/)

### Usage

Create an app on your developer account (for either DEMO or LIVE) using the following settings:

* Redirect URL: http://gttkeith.github.io/python-saxo/authcode
* Grant Type: Code
* Access control: ☑ Allow this app to be enabled for trading

An example main.py has been provided in the repo, where app details are stored in a params.json file.

pysaxo negotiates the authentication procedure using the complete OAuth2 authorisation flow. Sessions are proactively refreshed to prevent unexpected logouts.

Creating a new session:

```python
from pysaxo import Session
access = Session(app_key, auth_endpoint, token_endpoint, secret)
```

Performing requests:

```python
# get information about authorised user
access.get('port/v1/users/me')

# retrieve a list of FX spot instruments containing SGD
access.get('ref/v1/instruments', KeyWords='SGD', AssetTypes='FxSpot')
```

Query parameters are case-sensitive.

For a comprehensive overview of available endpoints, please refer to the [Saxo OpenAPI documentation](https://www.developer.saxo/openapi/learn).
