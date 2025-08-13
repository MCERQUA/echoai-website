# Echo AI Systems - API Reference Guide
*Complete API documentation for all endpoints and services*

## 🌐 API Overview

### Base URLs
- **Production**: `https://echoaisystem.com/api`
- **Development**: `http://localhost:3000/api`
- **Staging**: `https://staging.echoaisystem.com/api`

### Authentication
All API requests require authentication via Supabase JWT tokens.

```javascript
headers: {
  'Authorization': 'Bearer YOUR_JWT_TOKEN',
  'Content-Type': 'application/json'
}
```

## 📡 Core Endpoints

### Client Management

#### GET /api/clients
Retrieve all clients for authenticated user.

**Response:**
```json
{
  "success": true,
  "data": [
    {
      "id": "uuid",
      "business_name": "Client Business",
      "status": "active",
      "created_at": "2025-01-01T00:00:00Z"
    }
  ]
}
```

#### GET /api/clients/:id
Get specific client details.

**Parameters:**
- `id` (string): Client UUID

**Response:**
```json
{
  "success": true,
  "data": {
    "id": "uuid",
    "business_name": "Client Business",
    "contact_info": {},
    "brand_info": {},
    "services": []
  }
}
```

#### POST /api/clients
Create new client.

**Request Body:**
```json
{
  "business_name": "New Client",
  "email": "client@example.com",
  "phone": "555-0100"
}
```

#### PUT /api/clients/:id
Update client information.

**Request Body:**
```json
{
  "business_name": "Updated Name",
  "status": "active"
}
```

### Task Management

#### GET /api/tasks
Retrieve all tasks.

**Query Parameters:**
- `status` (string): Filter by status (pending, in_progress, completed)
- `client_id` (string): Filter by client
- `limit` (number): Results per page
- `offset` (number): Pagination offset

#### POST /api/tasks
Create new task.

**Request Body:**
```json
{
  "client_id": "uuid",
  "title": "Task Title",
  "description": "Task details",
  "priority": "high",
  "due_date": "2025-02-01"
}
```

### Content Management

#### GET /api/content
Retrieve content library.

**Query Parameters:**
- `type` (string): Filter by type (social, blog, email)
- `client_id` (string): Filter by client
- `status` (string): draft, approved, published

#### POST /api/content/generate
Generate AI content.

**Request Body:**
```json
{
  "client_id": "uuid",
  "type": "social_post",
  "platform": "instagram",
  "prompt": "Create engaging post about...",
  "tone": "professional"
}
```

### Analytics

#### GET /api/analytics/overview
Get analytics overview.

**Query Parameters:**
- `client_id` (string): Client UUID
- `start_date` (string): ISO date
- `end_date` (string): ISO date

**Response:**
```json
{
  "success": true,
  "data": {
    "total_views": 10000,
    "engagement_rate": 5.2,
    "conversion_rate": 2.1,
    "top_content": []
  }
}
```

### Reputation Management

#### GET /api/reputation/reviews
Get all reviews for client.

**Query Parameters:**
- `client_id` (string): Client UUID
- `platform` (string): google, yelp, facebook

#### POST /api/reputation/citations
Add directory citation.

**Request Body:**
```json
{
  "client_id": "uuid",
  "directory_name": "Yelp",
  "listing_url": "https://yelp.com/biz/...",
  "status": "active"
}
```

### AI Services

#### POST /api/ai/chat
Chat with Echo AI.

**Request Body:**
```json
{
  "client_id": "uuid",
  "message": "User message",
  "context": "dashboard"
}
```

**Response:**
```json
{
  "success": true,
  "data": {
    "response": "AI response",
    "tokens_used": 150,
    "suggestions": []
  }
}
```

#### POST /api/ai/image-generate
Generate images via Hugging Face.

**Request Body:**
```json
{
  "prompt": "Professional headshot of...",
  "style": "photorealistic",
  "dimensions": "1024x1024"
}
```

## 🔐 Authentication Flow

### 1. Login
```javascript
POST /api/auth/login
{
  "email": "user@example.com",
  "password": "secure_password"
}
```

### 2. Token Refresh
```javascript
POST /api/auth/refresh
{
  "refresh_token": "YOUR_REFRESH_TOKEN"
}
```

### 3. Logout
```javascript
POST /api/auth/logout
{
  "token": "YOUR_JWT_TOKEN"
}
```

## 📊 Webhooks

### Available Webhooks
- `task.created`
- `task.completed`
- `content.approved`
- `review.received`
- `client.updated`

### Webhook Registration
```javascript
POST /api/webhooks
{
  "url": "https://your-domain.com/webhook",
  "events": ["task.created", "task.completed"]
}
```

## 🚦 Rate Limiting

### Limits
- **Standard**: 100 requests/minute
- **Authenticated**: 500 requests/minute
- **Premium**: 2000 requests/minute

### Headers
```
X-RateLimit-Limit: 500
X-RateLimit-Remaining: 499
X-RateLimit-Reset: 1640995200
```

## ❌ Error Responses

### Standard Error Format
```json
{
  "success": false,
  "error": {
    "code": "ERROR_CODE",
    "message": "Human readable message",
    "details": {}
  }
}
```

### Common Error Codes
- `AUTH_REQUIRED` - Authentication required
- `INVALID_TOKEN` - Token expired or invalid
- `RESOURCE_NOT_FOUND` - Resource doesn't exist
- `VALIDATION_ERROR` - Input validation failed
- `RATE_LIMITED` - Too many requests
- `SERVER_ERROR` - Internal server error

## 🧪 Testing

### Test Environment
- **Base URL**: `https://api-test.echoaisystem.com`
- **Test API Key**: `test_key_abc123`

### Example Requests

#### cURL
```bash
curl -X GET \
  https://echoaisystem.com/api/clients \
  -H 'Authorization: Bearer YOUR_TOKEN' \
  -H 'Content-Type: application/json'
```

#### JavaScript
```javascript
const response = await fetch('https://echoaisystem.com/api/clients', {
  headers: {
    'Authorization': 'Bearer YOUR_TOKEN',
    'Content-Type': 'application/json'
  }
});
const data = await response.json();
```

#### Python
```python
import requests

headers = {
    'Authorization': 'Bearer YOUR_TOKEN',
    'Content-Type': 'application/json'
}

response = requests.get(
    'https://echoaisystem.com/api/clients',
    headers=headers
)
data = response.json()
```

## 📱 SDK Integration

### JavaScript SDK
```javascript
import EchoAPI from '@echoai/sdk';

const echo = new EchoAPI({
  apiKey: 'YOUR_API_KEY',
  environment: 'production'
});

const clients = await echo.clients.list();
```

### Python SDK
```python
from echoai import EchoAPI

echo = EchoAPI(api_key='YOUR_API_KEY')
clients = echo.clients.list()
```

## 🔄 Versioning

Current API Version: `v1`

Version in URL:
```
https://echoaisystem.com/api/v1/clients
```

Version in Header:
```
X-API-Version: v1
```

## 📞 Support

- **Documentation**: https://docs.echoaisystem.com
- **Status Page**: https://status.echoaisystem.com
- **Support Email**: api-support@echoaisystem.com
- **Discord**: https://discord.gg/echoai

---
*Last Updated: January 2025*