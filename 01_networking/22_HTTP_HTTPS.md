# HTTP and HTTPS

HTTP (HyperText Transfer Protocol) is an Application Layer protocol used for communication between clients (browsers) and servers.

HTTP operates over TCP (usually port 80).

HTTPS is HTTP over TLS encryption (usually port 443).

---

## HTTP Characteristics

- Stateless
- Request–Response based
- Text-based protocol
- Runs over TCP

Stateless means the server does not remember previous requests automatically.

---

## HTTP Request Structure

Basic format:

```
METHOD /path HTTP/version
Header: value
Header: value

[optional body]
```

Example:

```
GET /index.html HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0
Accept: text/html
```

---

## Common HTTP Methods

### GET
Retrieve data.
Should not modify server state.
Idempotent.

### POST
Submit data to server.
Often used to create new resources.
Not idempotent.

### PUT
Replace entire resource.
Idempotent.

### PATCH
Modify part of a resource.
Usually not idempotent.

### DELETE
Remove a resource.
Idempotent.

---

## HTTP Response Structure

```
HTTP/version Status-Code Reason
Header: value
Header: value

[optional body]
```

Example:

```
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 1234

<html>...</html>
```

---

## Important Status Codes

2xx → Success  
3xx → Redirection  
4xx → Client error  
5xx → Server error  

Common codes:

- 200 OK
- 301 Moved Permanently
- 302 Found
- 400 Bad Request
- 401 Unauthorized
- 403 Forbidden
- 404 Not Found
- 500 Internal Server Error
- 503 Service Unavailable

---

## Idempotency

A method is idempotent if repeating the same request produces the same final server state.

- GET → Idempotent
- PUT → Idempotent
- DELETE → Idempotent
- POST → Not idempotent

This matters for preventing replay attacks and duplicate transactions.

---

## Session Management

Because HTTP is stateless, websites maintain sessions using:

- Cookies
- Session IDs
- Tokens (e.g., JWT)

Typical login flow:

1. Client sends credentials via POST.
2. Server validates and creates a session.
3. Server sends `Set-Cookie` header with session ID.
4. Browser stores cookie.
5. Browser sends cookie in future requests.

Server uses session ID to identify the user.

---

## Security Considerations

Common HTTP-based attacks:

- SQL Injection
- Cross-Site Scripting (XSS)
- Cross-Site Request Forgery (CSRF)
- Directory traversal
- File upload abuse

Session hijacking occurs when attacker steals a valid session cookie.

---

## HTTPS (HTTP Secure)

HTTPS is HTTP over TLS encryption.

Provides:

- Confidentiality (encryption)
- Integrity (no tampering)
- Authentication (server identity via certificate)

Without HTTPS:
- Credentials can be intercepted.
- Session cookies can be stolen.

Modern web applications must use HTTPS.
