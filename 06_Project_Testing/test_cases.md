# Phase 6 – Project Testing

## Project Title

AI FAQ Assistant API

## 1. Testing Objective

The objective of testing is to verify that the AI FAQ Assistant API
functions correctly and that its major API operations produce the
expected results.

The following functionalities are tested:

- User registration
- User login
- JWT authentication
- FAQ creation
- FAQ search
- AI-powered FAQ generation
- API validation and error handling

## 2. Testing Tool

The API can be tested using:

- Postman
- ThunderClient
- Visual Studio Code

## 3. Test Cases

### TC-01: User Registration

**Endpoint:**

POST `/api/auth/register`

**Access:** Public

**Purpose:**

To verify that a new user can register successfully.

**Sample Request:**

```json
{
  "name": "Priya Sharma",
  "email": "priya@writeflow.com",
  "password": "securepassword123"
}
