# Weather API Documentation

## Introduction

This API provides various endpoints to fetch weather and irradiance information for specific parks.

To access the API, you need to obtain an access token by following the authentication process outlined below.

If you dont have credentials and need help getting them please contact us.

## Authentication

All endpoints in this API require authentication using an access token. To obtain an access token please read through the Authentication guide.

## WARNING

As always with our apis the respones are base64 and JSON encoded and the requests are expected to be as well!


## Endpoints

### 1. Get Park Irradiance Information

**Endpoint:** `/api/thirdparty/getParkIrradianceInfo`

**Method:** `POST`

**Description:** Fetch irradiance information for a given park.

**Body:**

- `parkId`: (required) The ID of the park.
- `tz`: Timezone for the irradiance data.
- `date`: Date for which irradiance data is required.

**Response:**

Returns irradiance data for the given park ID, timezone, and date.

### 2. Get Full Weather Information for Park

**Endpoint:** `/api/thirdparty/getParkWeatherInfoFull`

**Method:** `POST`

**Description:** Fetch detailed weather information for a specific park.

**Body:**

- `parkId`: (required) The ID of the park.

**Response:**

Returns detailed weather information for the given park ID.

### 3. Get Park Weather Information by Timestamp

**Endpoint:** `/api/thirdparty/getParkWeatherInfoByTimestamp`

**Method:** `POST`

**Description:** Fetch weather information for a specific park at a given timestamp.

**Body:**

- `parkId`: (required) The ID of the park.
- `dt`: (required) Unix timestamp for which weather data is required.

**Response:**

Returns weather information for the given park ID at the specified timestamp.

### 4. Get Basic Weather Information for Park

**Endpoint:** `/api/thirdparty/getParkWeatherInfo`

**Method:** `POST`

**Description:** Fetch basic weather information for a specific park.

**Body:**

- `parkId`: (required) The ID of the park.

**Response:**

Returns basic weather information for the given park ID.

## Error Handling

If there's an issue with the request, the server will respond with an error in the format: `{ "error": "Error message" }`.

Common errors include:

- Missing `parkId` in the request body.
- Invalid `parkId`.
- Internal Server Error.


