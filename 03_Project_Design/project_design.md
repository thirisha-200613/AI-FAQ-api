# Phase 3 – Project Design

## 1. Project Title

AI FAQ Assistant API

## 2. System Architecture

The AI FAQ Assistant API follows a layered backend architecture.

The major components are:

1. API Interface
2. Express Server Gateway
3. Authentication Middleware
4. Controller and Business Logic
5. Database Interface Layer
6. AI Service Integration
7. MongoDB Database

### Architecture Flow

User / API Client
        |
        v
API Request
        |
        v
Express.js Server
        |
        v
Authentication Middleware
        |
        v
Controller / Business Logic
        |
        +-------------------+
        |                   |
        v                   v
MongoDB / Mongoose       Google Gemini AI
        |                   |
        +---------+---------+
                  |
                  v
             JSON Response

## 3. API Interface

API clients such as Postman or ThunderClient send HTTP requests
to the backend API.

The API supports HTTP methods such as:

- GET
- POST
- PUT
- DELETE

The API returns responses in JSON format.

## 4. Authentication Design

JWT-based authentication is used to protect private API endpoints.

The authentication process is:

1. User registers an account.
2. User logs in using email and password.
3. The server verifies the credentials.
4. A JWT token is generated.
5. The token is sent with requests to protected endpoints.
6. Authentication middleware verifies the token.

## 5. MVC Architecture

The backend follows the Model-View-Controller architecture pattern.

### Model Layer

The Model layer defines the database structure using Mongoose schemas.

It handles:

- User data
- FAQ data
- Database validation
- MongoDB persistence

### Controller Layer

The Controller layer processes API requests and controls the
application workflow.

It:

- Receives requests
- Validates request data
- Executes business logic
- Communicates with models/services
- Returns JSON responses

### View Layer

This project is a headless REST API.

Therefore, a traditional frontend view is not used.

The API routing layer acts as the interface through which clients
communicate with the backend.

## 6. Database Design

MongoDB is used as the primary database and Mongoose is used for
data modelling and validation.

### User Entity

Fields:

- _id
- name
- email
- password
- role
- createdAt
- updatedAt

### FAQ Entity

Fields:

- _id
- question
- answer
- category
- createdBy
- createdAt
- updatedAt

### AI Generation Entity

Fields:

- topic
- generatedQuestion
- generatedAnswer
- generatedCategory
- generatedAt

### Category Entity

Fields:

- categoryName
- description
- totalFAQs

## 7. Entity Relationships

### User → FAQ

One user can create and manage multiple FAQ records.

Relationship:

One-to-Many

### Category → FAQ

One category can contain multiple FAQ documents.

Relationship:

One-to-Many

### User → AI Generated FAQ

One user can generate multiple AI-assisted FAQs.

Relationship:

One-to-Many

### FAQ → Search Results

Search queries retrieve matching FAQ documents using keyword and
semantic matching.

## 8. AI Integration Design

Google Gemini AI is integrated into the backend through the Google
Gemini SDK.

The AI service is used for:

- FAQ question generation
- FAQ answer generation
- Topic generation
- AI-assisted content creation

### AI Flow

User provides a topic
        |
        v
AI API Request
        |
        v
Google Gemini AI
        |
        v
Generated Question
        +
Generated Answer
        +
Generated Category
        |
        v
API Response

## 9. API Design

### Authentication APIs

POST /api/auth/register

POST /api/auth/login

### FAQ APIs

POST /api/faqs

GET /api/faqs

PUT /api/faqs/:id

DELETE /api/faqs/:id

### Search API

GET /api/faqs/search?q=configure

### AI API

POST /api/ai/generate-faq

Private endpoints require a valid JWT Bearer token.

## 10. Security Design

The system uses:

- JWT for authentication
- bcrypt for password hashing
- Protected routes
- Mongoose schema validation
- Centralized error handling

These mechanisms help protect private resources and maintain
database integrity.

## 11. Design Conclusion

The proposed design provides a modular REST API architecture
combining secure authentication, MongoDB data management, FAQ
operations, search functionality, and Google Gemini AI integration.
