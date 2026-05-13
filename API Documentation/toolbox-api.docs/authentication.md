# Authentication
The API uses token-based authentication.

## Obtain Access Token

Endpoint:
```
POST /oauth/token
```
### Request Body
```json
{
"client id": "your_client_id",
"client_secret": "your_secret",
"grant_type": "client_credentials"
}
```
### Response
```json
{
"access_token": "token_value",
"expires_in": 3600
}
```
## Using the Token

Include the token in the Authorization header.
```
Authorization: Bearer access_token
```
