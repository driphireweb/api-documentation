# Candidates API Documentation

This documentation provides details on the API endpoints for managing candidates in the Fullbound platform.

## Base URL

```
https://api.fullbound.ai/v1
```

## Authentication

All endpoints require an API key for authentication. Include the API key in the `Authorization` header of your requests.

```
Authorization: Bearer YOUR_API_KEY
```

## Endpoints

### 1. Create Candidate

**Endpoint:**

```
POST /candidates
```

**Description:**

Creates a new candidate in the system.

**Request:**

- **Headers:**
  - `Content-Type: application/json`
  - `Authorization: Bearer YOUR_API_KEY`

- **Body:**

```json
{
  "firstName": "John",
  "lastName": "Doe",
  "email": "john.doe@example.com",
  "phone": "+1234567890",
  "resume": "https://example.com/resume.pdf",
  "source": "LinkedIn"
}
```

**Response:**

- **Success (201 Created):**

```json
{
  "id": "12345",
  "firstName": "John",
  "lastName": "Doe",
  "email": "john.doe@example.com",
  "phone": "+1234567890",
  "resume": "https://example.com/resume.pdf",
  "source": "LinkedIn",
  "createdAt": "2023-10-01T12:00:00Z",
  "updatedAt": "2023-10-01T12:00:00Z"
}
```

- **Error (400 Bad Request):**

```json
{
  "error": "Invalid request data"
}
```

### 2. Update Candidate

**Endpoint:**

```
PUT /candidates/{candidateId}
```

**Description:**

Updates an existing candidate in the system.

**Request:**

- **Headers:**
  - `Content-Type: application/json`
  - `Authorization: Bearer YOUR_API_KEY`

- **Body:**

```json
{
  "firstName": "John",
  "lastName": "Doe",
  "email": "john.doe@example.com",
  "phone": "+1234567890",
  "resume": "https://example.com/resume.pdf",
  "source": "LinkedIn"
}
```

**Response:**

- **Success (200 OK):**

```json
{
  "id": "12345",
  "firstName": "John",
  "lastName": "Doe",
  "email": "john.doe@example.com",
  "phone": "+1234567890",
  "resume": "https://example.com/resume.pdf",
  "source": "LinkedIn",
  "createdAt": "2023-10-01T12:00:00Z",
  "updatedAt": "2023-10-01T12:30:00Z"
}
```

- **Error (404 Not Found):**

```json
{
  "error": "Candidate not found"
}
```

### 3. Retrieve Candidate

**Endpoint:**

```
GET /candidates/{candidateId}
```

**Description:**

Retrieves the details of a specific candidate.

**Request:**

- **Headers:**
  - `Authorization: Bearer YOUR_API_KEY`

**Response:**

- **Success (200 OK):**

```json
{
  "id": "12345",
  "firstName": "John",
  "lastName": "Doe",
  "email": "john.doe@example.com",
  "phone": "+1234567890",
  "resume": "https://example.com/resume.pdf",
  "source": "LinkedIn",
  "createdAt": "2023-10-01T12:00:00Z",
  "updatedAt": "2023-10-01T12:00:00Z"
}
```

- **Error (404 Not Found):**

```json
{
  "error": "Candidate not found"
}
```

### 4. Delete Candidate

**Endpoint:**

```
DELETE /candidates/{candidateId}
```

**Description:**

Deletes a specific candidate from the system.

**Request:**

- **Headers:**
  - `Authorization: Bearer YOUR_API_KEY`

**Response:**

- **Success (204 No Content):**

No content.

- **Error (404 Not Found):**

```json
{
  "error": "Candidate not found"
}
```

## Error Codes

- **400 Bad Request**: The request data is invalid.
- **401 Unauthorized**: The API key is missing or invalid.
- **404 Not Found**: The requested resource was not found.
- **500 Internal Server Error**: An error occurred on the server.

## Example Usage

### cURL

**Create Candidate:**

```sh
curl -X POST https://api.fullbound.ai/v1/candidates \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{
    "firstName": "John",
    "lastName": "Doe",
    "email": "john.doe@example.com",
    "phone": "+1234567890",
    "resume": "https://example.com/resume.pdf",
    "source": "LinkedIn"
  }'
```

**Update Candidate:**

```sh
curl -X PUT https://api.fullbound.ai/v1/candidates/12345 \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -d '{
    "firstName": "John",
    "lastName": "Doe",
    "email": "john.doe@example.com",
    "phone": "+1234567890",
    "resume": "https://example.com/resume.pdf",
    "source": "LinkedIn"
  }'
```

**Retrieve Candidate:**

```sh
curl -X GET https://api.fullbound.ai/v1/candidates/12345 \
  -H "Authorization: Bearer YOUR_API_KEY"
```

**Delete Candidate:**

```sh
curl -X DELETE https://api.fullbound.ai/v1/candidates/12345 \
  -H "Authorization: Bearer YOUR_API_KEY"
```

## Contact

For any questions or support, please contact [support@fullbound.ai](mailto:support@fullbound.ai).
