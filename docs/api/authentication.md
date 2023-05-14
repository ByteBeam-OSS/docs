# Token retrieval and Parsing

## Getting a Token

Request a token from the authentication server. The following CURL command can be used, but any equivalent in another language will work as well:

```bash
curl -X POST "https://sso.sexycoders.org/auth/realms/sexycoders.org/protocol/openid-connect/token" \
     -H "Content-Type: application/x-www-form-urlencoded" \
     -d "client_id=your_client_id" \
     -d "client_secret=your_client_secret" \
     -d "grant_type=client_credentials"
```

This is a client grant; passwords or usernames are not required. However, the client secret must be kept absolutely safe. Never share it and always use HTTPS when posting. The server should refuse non-HTTPS requests, but it is essential to ensure this.

Dont forget to replace placeholders with your actual credentials!

## Expected Response

The server will respond with something like the following:

```bash
{
  "access_token": "...",
  "expires_in": 300,
  "refresh_expires_in": 0,
  "token_type": "Bearer",
  "not-before-policy": 0,
  "scope": "email profile"
}
```

The 'access_token' field is the token you need.

## Posting to the API

With the token, you can post to the API using the following command:

```bash
curl -X POST -H "Content-Type: application/json" \
     -d '{"token": "your_token_here"}' \
     https://your_api/path_to_endpoint
```

Replace "your_api/path_to_endpoint" with the actual api endpoint location and "your_token_here" 
with the token you obtained use the correct endpoint path.


