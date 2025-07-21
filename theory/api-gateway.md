# API Gateway – Basics, JWT, Rate Limiting, Throttling

---

## What is an API Gateway?

An API Gateway is an intermediary between the client and microservices/backend that:
- accepts HTTP/HTTPS requests,
- manages traffic,
- handles security and authorization,
- applies restrictions (rate limiting, throttling),
- can transform requests and responses.

**Key functions:**
- Request routing to services
- Authentication (e.g., JWT)
- Request limiting
- Throttling
- Caching
- Logging and monitoring

---

## JWT (JSON Web Token)

JWT is a JSON-formatted token used for user authentication and authorization in APIs.

**Token structure:**
header.payload.signature

yaml
Kopiuj
Edytuj

- Header – token type and algorithm (e.g., HS256)
- Payload – data (e.g., sub, exp, role)
- Signature – signature ensuring data integrity

**Usage:**
- After login, the user receives a JWT.
- The token is sent in the Authorization header.
- The gateway verifies the signature, expiration, and permissions.

---

## Rate Limiting – Limiting the Number of Requests

A mechanism that limits the number of requests a client can send in a time period (e.g., 100/min).

**Benefits:**
- Protects the API
- Prevents abuse and attacks
- Ensures fair access

**Common techniques:**
- Fixed Window: Simple but susceptible to bursts
- Sliding Window: More precise, smoother distribution
- Token Bucket: Tokens replenished over time, allows bursts
- Leaky Bucket: Stable rate, queued requests

---

## Throttling – Slowing Down Requests

Throttling is a flexible management of request rate.

**Differences compared to rate limiting:**
- Rate limiting: hard limit
- Throttling: slows down or queues excess requests

**Example:** 50 requests immediately, subsequent requests delayed or queued.

---

## Comparison: Rate Limiting vs Throttling

| Rate Limiting             | Throttling                      |
|--------------------------|--------------------------------|
| Limits the number of requests | Slows down requests          |
| Hard limit               | Flexible approach               |
| For API protection       | For managing overload           |

---

## Common Tools Supporting JWT, Rate Limiting, Throttling

- Kong: JWT ✅ | Rate Limiting ✅ | Throttling ✅  
- Apigee: JWT ✅ | Rate Limiting ✅ | Throttling ✅  
- Traefik: JWT ✅ | Rate Limiting ✅ | Throttling 🔶 (partial)  
- Express.js: JWT ✅ | Rate Limiting 🔶 | Throttling 🔶  

---

## Summary of Key Concepts

- **API Gateway** – central gateway between client and backend.  
- **JWT** – token containing user data, used for authentication.  
- **Rate Limiting** – limits the number of requests over time.  
- **Throttling** – slows down requests to stabilize traffic.
