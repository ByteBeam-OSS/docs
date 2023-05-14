# Authentication and API Usage

## Token Verification 

```bash
curl -X POST \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "client_id=<your_client_id>" \
  -d "client_secret=<your_client_secret>"\
  -d "token=<token_value>" \
  https://sso.sexycoders.org/auth/realms/<your_realm>/protocol/openid-connect/token/introspect
```

This will verify if the token is active or not by returning:

```bash
HUGE PILE OF JSON SHIT
```
or 

```bash
{"active":false}
```

You can then procceed to the execution or not of the rest of the code.

## Formatted response

As you might notice by running the above,it returns a lot of pretty much useless 💩.

We can get a formatted and usable return by posting the userinfo endpoint

```bash
https://sso.sexycoders.org/auth/realms/<your_realm>/protocol/openid-connect/userinfo
```

The response for an active token will then look like this:

```bash
{
  "sub":"...",
  "email_verified":true,
  "preferred_username":"username",
  "email":"email"
}
```

A lot better aint it ?

This will also include fields like Name or Last Name if present in the users profile.

## Endpoint listing

We can find the list of available endpoints by using

```bash
https://sso.sexycoders.org/auth/realms/<your_realm>/.well-known/openid-configuration
```

Response should be a json file with the openid config of the server.
It will also contain the available endpoints.
