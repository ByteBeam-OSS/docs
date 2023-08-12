## API Documentation

### Introduction

Welcome to the documentation for the Microsun Solar API. This API allows authorized third-party applications to access and retrieve data related to inverters. 
To access the API, you need to obtain an access token by following the authentication process outlined below.

If you dont have credentials and need help getting them please contact us.

### Authentication

All endpoints in this API require authentication using an access token. To obtain an access token please read through the Authentication guide.

## WARNING

As always with our apis the respones are base64 and JSON encoded and the requests are expected to be as well!

## Endpoints

### 1. Get Park Inverter Logs

**Endpoint:** `/api/thirdparty/getParkInverterLogs`

**Method:** `POST`

**Authorization:** Required (Bearer token)

**Request Body:**
The request body must be a JSON object containing the following parameter:

- `parkId` (string, required): The unique identifier of the park for which you want to retrieve inverter logs.

Example using `curl`:
```bash
body='{"parkId":"8"}'
base64_body=$(echo -n "$body" | base64)

curl https://viki.sexycoders.org/api/thirdparty/getParkInverterLogs \
  -H "Authorization: Bearer $token" \
  -d "$base64_body"
```

**Response:**
If successful, the response will be a JSON object containing the data for all inverters belonging to the specified park.

- `200 OK` with the response data on success.
- `400 Bad Request` if `parkId` is missing in the request body.
- `404 Not Found` if no inverters are found for the specified park.
- `500 Internal Server Error` on server errors.

### 2. Get Inverter Data by ID

**Endpoint:** `/api/thirdparty/getInverterDataById`

**Method:** `POST`

**Authorization:** Required (Bearer token)

**Request Body:**
The request body must be a JSON object containing the following parameter:

- `inverterId` (string, required): The unique identifier of the inverter for which you want to retrieve data.

Example using `curl`:
```bash
body='{"inverterId":"xyz123"}'
base64_body=$(echo -n "$body" | base64)

curl https://viki.sexycoders.org/api/thirdparty/getInverterDataById \
  -H "Authorization: Bearer $token" \
  -d "$base64_body"
```

**Response:**
If successful, the response will be a JSON object containing the data for the specified inverter.

- `200 OK` with the response data on success.
- `404 Not Found` if the specified inverter is not found.
- `500 Internal Server Error` on server errors.

### 3. Get Combined Inverter Data

**Endpoint:** `/api/thirdparty/getCombinedInverterData`

**Method:** `POST`

**Authorization:** Required (Bearer token)

**Request Body:** This endpoint does not require any request body.

Example using `curl`:
```bash
curl https://viki.sexycoders.org/api/thirdparty/getCombinedInverterData \
  -H "Authorization: Bearer $token"
```

**Response:**
If successful, the response will be a JSON object containing the combined data for all available inverters.

- `200 OK` with the response data on success.
- `500 Internal Server Error` on server errors.

## Error Handling

In case of errors, the API will return appropriate HTTP status codes along with JSON error messages in the response body. Make sure to handle these error responses in your application.

## Rate Limiting

This API does not have rate limiting implemented at this time. However, it is recommended to avoid excessive requests to ensure fair usage and optimal performance for all users and encourage us to keep it free.

Happy coding!

Solar Plant Data provided by [microsun energy systems](https://microsun.gr/)
