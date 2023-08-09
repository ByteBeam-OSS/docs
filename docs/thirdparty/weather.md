# Weather API Documentation

## Introduction

This API provides various endpoints to fetch weather and irradiance information for specific parks.

To access the API, you need to obtain an access token by following the authentication process outlined below.

If you don't have credentials and need help getting them, please contact us.

## Authentication

All endpoints in this API require authentication using an access token. To obtain an access token, please read through the Authentication guide.

## WARNING

As always with our APIs, the responses are base64 and JSON encoded, and the requests are expected to be as well!

## Endpoints

### 1. Get Park Irradiance Information

**Endpoint:** `/api/thirdparty/getParkIrradianceInfo`

**Method:** `POST`

**Description:** Fetch irradiance information for a given park.

**Body:**

- `parkId`: (required) The ID of the park.
- `tz`: (required) Timezone for the irradiance data.
- `date`: (required) Date for which irradiance data is required.

**Example:**

```bash
body='{"parkId":"7", "tz": "+03:00", "date": "2023-08-09"}'
base64_body=$(echo -n "$body" | base64)

curl https://viki.sexycoders.org/api/thirdparty/getParkIrradianceInfo \
  -H "Authorization: Bearer $token" \
  -d "$base64_body"
```

### 2. Get Full Weather Information for Park

**Endpoint:** `/api/thirdparty/getParkWeatherInfoFull`

**Method:** `POST`

**Description:** Fetch detailed weather information for a specific park.

**Body:**

- `parkId`: (required) The ID of the park.

**Example:**

```bash
body='{"parkId":"7"}'
base64_body=$(echo -n "$body" | base64)

curl https://viki.sexycoders.org/api/thirdparty/getParkWeatherInfoFull \
  -H "Authorization: Bearer $token" \
  -d "$base64_body"
```

### 3. Get Park Weather Information by Timestamp

**Endpoint:** `/api/thirdparty/getParkWeatherInfoByTimestamp`

**Method:** `POST`

**Description:** Fetch weather information for a specific park at a given timestamp.

**Body:**

- `parkId`: (required) The ID of the park.
- `dt`: (required) Unix timestamp for which weather data is required.

**Example:**

```bash
body='{"parkId":"7", "dt": "1677897600"}'  # Replace with desired timestamp
base64_body=$(echo -n "$body" | base64)

curl https://viki.sexycoders.org/api/thirdparty/getParkWeatherInfoByTimestamp \
  -H "Authorization: Bearer $token" \
  -d "$base64_body"
```

### 4. Get Basic Weather Information for Park

**Endpoint:** `/api/thirdparty/getParkWeatherInfo`

**Method:** `POST`

**Description:** Fetch basic weather information for a specific park.

**Body:**

- `parkId`: (required) The ID of the park.

**Example:**

```bash
body='{"parkId":"7"}'
base64_body=$(echo -n "$body" | base64)

curl https://viki.sexycoders.org/api/thirdparty/getParkWeatherInfo \
  -H "Authorization: Bearer $token" \
  -d "$base64_body"
```

## Error Handling

If there's an issue with the request, the server will respond with an error in the format: `{ "error": "Error message" }`.

Common errors include:

- Missing `parkId` in the request body.
- Invalid `parkId`.
- Internal Server Error.


