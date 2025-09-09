# How-The-Web-Works

# Understanding HTTP Requests and Responses

**HTTP requests and responses**, including headers, parameters, preferences, and body contents.  

---

## What Happens in a Web Request?

When a **browser (client)** communicates with a **server**, two main messages are exchanged:

1. **HTTP Request** → sent from client to server  
2. **HTTP Response** → sent from server back to client  

Both carry:
- **Metadata** → headers, parameters, preferences  
- **Content** → body (HTML, JSON, files, etc.)  

---
# HTTP Request Methods

HTTP defines several **request methods** that indicate the action a client wants the server to perform on a resource.

### 1. **GET**
- **Purpose:** Retrieve data from the server.
```http
  GET /products?category=shoes&page=2 HTTP/1.1
```
### 2. **POST**
**Purpose:** Create new resources or submit data.
```POST /api/users HTTP/1.1
Content-Type: application/json

{
  "name": "Shirley",
  "email": "shirley@example.com"
}
```
### 3. **PUT**
**Purpose:** Replace a resource with new data.

```PUT /api/users/123 HTTP/1.1
Content-Type: application/json

{
  "name": "Shirley",
  "email": "shirley.new@example.com"
}
```

### 4. **PATCH**
**Purpose:** Partially update a resource.

``` PATCH /api/users/123 HTTP/1.1
Content-Type: application/json

{
  "email": "shirley.updated@example.com"
}
```

### 5. **DELETE**
**Purpose:** Remove a resource.

``` DELETE /api/users/123 HTTP/1.1 ```

### 6. **HEAD**
**Purpose:** Same as GET but only retrieves the head, no body. Used to check if a resource exits or get metadata.

``` HEAD /products HTTP/1.1 ```

---

## HTTP Request (Client → Server)

### Request Line
Defines what the client wants:
```http
GET /products?category=shoes&page=2 HTTP/1.1
```

- GET → method (action to perform)
- /products → path (resource location)
- ?category=shoes&page=2 → query parameters (filters, pagination)

---

Headers

Metadata describing the request and client preferences:

``` Host: example.com
User-Agent: Mozilla/5.0
Accept: text/html,application/json
Accept-Language: en-KE
Cookie: session=abc123
Authorization: Bearer <token>
```
Examples of preferences:
- Format (Accept)
- Language (Accept-Language)
- Encoding (Accept-Encoding)

---
Body (Optional)

Present with some methods (POST, PUT, PATCH):
``` POST /api/login HTTP/1.1
Content-Type: application/json

{
  "email": "shirley@example.com",
  "password": "securePass"
}
```
---
## HTTP Response (Server → Client)
 Status Line

Communicates the result:
```HTTP/1.1 200 OK```
- 200 → success
- Other codes: 301 (redirect), 404 (not found), 500 (server error)

---
Headers

Metadata about the response:
``` Content-Type: text/html; charset=UTF-8
Content-Encoding: gzip
Cache-Control: max-age=600
Set-Cookie: session=abc123; HttpOnly; Secure
Access-Control-Allow-Origin: *
```
---
Body
The actual content (HTML, JSON, image, etc.):

``` {
  "status": "success",
  "products": [
    {"id": 1, "name": "Running Shoes"},
    {"id": 2, "name": "Sneakers"}
  ]
}
```

---
Analogy: Ordering in a Restaurant

- Request line: what you order → GET /menu?category=drinks
- Headers: preferences → "less spicy, vegetarian"
- Body: special instructions → "extra sugar"
- Response headers: notes from chef → "served hot, ready in 5 mins"
- Response body: the actual dish

---
Key Takeaways

- Parameters → extra data in URL or body (?category=shoes)
- Headers → metadata (preferences, security, instructions)
- Preferences → often expressed in headers (Accept, Accept-Language)
- Body → the main content (HTML, JSON, files)
