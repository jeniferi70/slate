## Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "https://login.authxpo.com/connect/token"
  -d "grant_type=client_credentials&client_id=<CLIENT_ID>&client_secret=<CLIENT_SECRET>&scope=connect-orders"
```

> JSON Response:

```json
{
  "access_token":"ACCESS_TOKEN",
  "expires_in":3600,
  "token_type":"Bearer"
}
```

The XPO API is JSON based. In order to make an authenticated call to the API, you must include your access token with the call.

### Registering the Application

To use the XPO API, you must be a current XPO partner. To request access to the API please contact your XPO represenative.

Your XPO representative, will provide you with two keys:

* `CLIENT_ID`
* `CLIENT_SECRET`