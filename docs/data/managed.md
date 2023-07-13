# Managed Database API

This documentation provides information on how to use the API endpoints provided by your managed database.
The API allows users to interact with a database, perform operations such as storing data, retrieving data, listing collections, and more.
# API Documentation

This documentation provides information on how to use the API endpoints defined in the provided code. The API allows users to interact with a database, perform operations such as storing data, retrieving data, listing collections, and more.

**Important: All communications with the API must be done using JSON format and Base64 encoding.**

## Authentication

Before making requests to the API, you need to obtain an access token by sending a POST request to the authentication endpoint. The following example demonstrates how to obtain an access token:

```bash
token=$(curl -X POST -d "grant_type=client_credentials&client_id=<client_id>&client_secret=<client_secret>" \
  https://sso.sexycoders.org/auth/realms/sexycoders.org/protocol/openid-connect/token | jq -r '.access_token')
```

Replace `<client_id>` and `<client_secret>` with your actual credentials.

## Storing Data

To store data in the database, send a POST request to the `/storeData` endpoint. Include the access token in the request header and the data in the request body as an object. The example below demonstrates how to store data:

```bash
body='{"database":"<database_name>","collection":"<collection_name>","data":{"<field_name>":"<value>","<field_name>":"<value>"}}'
base64_body=$(echo -n "$body" | base64)

curl https://api.sexycoders.org/mydb/storeData \
  -H "Authorization: Bearer $token" \
  -H "Content-Type: application/json" \
  -d "$base64_body"
```

Replace `<database_name>` with the name of the database, `<collection_name>` with the name of the collection, `<field_name>` with the actual field names in your data, and `<value>` with the corresponding values.

**Note: The `/store` endpoint expects the `data` field to be a single object.**

## Storing Multiple Documents

To store multiple documents in the database, send a POST request to the `/storeMultiple` endpoint. Include the access token in the request header and the data in the request body as a nested array of objects. The example below demonstrates how to store multiple documents:

```bash
body='{"database":"<database_name>","collection":"<collection_name>","data":[{"<field_name>":"<value>","<field_name>":"<value>"}, {"<field_name>":"<value>","<field_name>":"<value>"}]}'
base64_body=$(echo -n "$body" | base64)

curl https://api.sexycoders.org/storeMultiple \
  -H "Authorization: Bearer $token" \
  -H "Content-Type: application/json" \
  -d "$base64_body"
```

Replace `<database_name>` with the name of the database, `<collection_name>` with the name of the collection, `<field_name>` with the actual field names in your data, and `<value>` with the corresponding values.

**Note: The `/storeMultiple` endpoint expects the `data` field to be an array of objects.**

## Retrieving Data

To retrieve data from the database, send a POST request to the `/retrieveData` endpoint. Include the access token in the request header and specify the database, collection, and optional constraints in the request body. The example below demonstrates how to retrieve data:

```bash
body='{"database":"<database_name>","collection":"<collection_name>","constraints":{"<field_name>":"<value>"},"count":<count>}'
base64_body=$(echo -n "$body" | base64)

curl https://api.sexycoders.org/retrieveData \
  -H "Authorization: Bearer $token" \
  -H "Content-Type: application/json" \
  -d "$base64_body"
```

Replace `<database_name>` with the name of the database, `<collection_name>` with the name of the collection, `<field_name>` with the actual field names in your data, `<value>` with the corresponding values, and `<count>` with the desired number of documents to retrieve (optional).

## Listing Collections

To list collections in the database, send a POST request to the `/listCollections` endpoint. Include the access token in the request header and specify the database in the request body. The example below demonstrates how to list collections:

```bash
body='{"database":"<database_name>"}'
base64_body=$(echo -n "$body" | base64)

curl https://api.sexycoders.org/listCollections \
  -H "Authorization: Bearer $token" \
  -H "Content-Type: application/json" \
  -d "$base64_body"
```

Replace `<database_name>` with the name of the database.

---

Note: Make sure to replace the placeholders `<client_id>`, `<client_secret>`, `<database_name>`, `<collection_name>`, `<field_name>`, and `<value>` with the actual values specific to your setup.

Remember to include the access token obtained through the authentication process in the request headers when interacting with the API.

For further assistance or inquiries, please contact the API support team at support@example.com.
