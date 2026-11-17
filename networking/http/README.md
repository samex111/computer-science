# HTTP Learning Roadmap — Checklist

A first-principles checklist for understanding **HTTP from the wire level to real applications**.

The goal is not just to memorize methods and status codes. By the end, you should be able to trace an HTTP exchange, inspect it with tools, and build a small HTTP/1.1 server using a raw TCP socket.

> **Learning rule:** For every topic, understand the problem it solves, inspect a real example, experiment with it, and explain it in your own words. Tick a box only when you can do that — not just after watching a video.

## How to use this checklist

- [ ] Work through the stages in order. Revisit earlier topics whenever a project exposes a gap.
- [ ] Keep notes in your own words, with diagrams, commands, captures, experiments, and open questions.
- [ ] Complete the practical labs; reading about a request is not the same as inspecting one.
- [ ] Complete each stage's "prove your understanding" tasks before moving on.
- [ ] Mark an item complete only when you can explain or demonstrate it without copying a tutorial.

---

## Stage 0 — Prerequisites: the network beneath HTTP

HTTP is an application-layer protocol. It depends on lower layers to move data between programs. Learn enough networking to understand what HTTP is built on.

- [ ] Understand what a computer network is and why protocols are needed.
- [ ] Understand client, server, host, network interface, and socket.
- [ ] Learn the difference between an IP address and a MAC address.
- [ ] Understand what a port identifies and why a server listens on a port.
- [ ] Learn the basic jobs of switches and routers.
- [ ] Understand packets and encapsulation.
- [ ] Learn what TCP provides: connection-oriented, ordered, reliable byte-stream delivery.
- [ ] Understand the TCP connection lifecycle, including the three-way handshake and connection close.
- [ ] Learn what UDP provides and how it differs from TCP.
- [ ] Understand what DNS does and how a domain name can resolve to an IP address.
- [ ] Understand the difference between a TCP connection and an HTTP request.

**Prove your understanding**

- [ ] Draw a laptop → router → server diagram and label IP addresses, ports, and the transport protocol.
- [ ] Explain why TCP delivers a byte stream rather than preserving application message boundaries.
- [ ] Explain why an IP address alone is not enough to identify a server application.

---

## Stage 1 — HTTP mental model and URL anatomy

- [ ] Explain the problem HTTP solves and why a shared application protocol is useful.
- [ ] Identify HTTP as an application-layer protocol.
- [ ] Understand the client-server request/response model.
- [ ] Learn the parts of a URL: scheme, host, port, path, query, and fragment.
- [ ] Understand the difference between `http` and `https` URL schemes.
- [ ] Understand the roles of the browser, DNS resolver, transport connection, web server, and application.
- [ ] Trace what happens after entering a URL in a browser.
- [ ] Understand that HTTP is stateless in its protocol semantics, while applications can maintain state using cookies, tokens, and server-side sessions.

**Prove your understanding**

- [ ] Break down `https://example.com:443/products?id=42#details` into its components.
- [ ] Draw the browser-to-server request/response journey.
- [ ] Explain which steps happen before the HTTP request can be sent.

---

## Stage 2 — HTTP/1.1 request and response structure

Start with HTTP/1.1 because its text-based message format is useful for learning and for the raw-socket project.

### Request

- [ ] Understand the request line: method, request target, and HTTP version.
- [ ] Understand request headers and why header names are case-insensitive.
- [ ] Understand the blank line separating headers from the message body.
- [ ] Understand when a request has a body and how the body is represented.
- [ ] Inspect `Host`, `Accept`, `Content-Type`, `Content-Length`, `Authorization`, and `User-Agent`.
- [ ] Understand request targets at a basic level.

### Response

- [ ] Understand the status line: HTTP version, status code, and reason phrase.
- [ ] Understand response headers.
- [ ] Understand the optional response body.
- [ ] Inspect `Content-Type`, `Content-Length`, `Date`, `Cache-Control`, `Location`, and `Set-Cookie`.
- [ ] Understand that headers describe metadata and the body carries representation data when present.

### Message framing and connections

- [ ] Understand how `Content-Length` indicates the message-body length.
- [ ] Learn chunked transfer coding and `Transfer-Encoding` in HTTP/1.1.
- [ ] Understand why one TCP read event is not necessarily one complete HTTP request.
- [ ] Understand incomplete reads: a message may arrive across multiple TCP chunks.
- [ ] Understand that persistent connections can carry more than one request/response exchange.
- [ ] Learn the purpose of `Connection: close` and persistent connections in HTTP/1.1.

**Practical lab**

- [ ] Inspect a real request and response in browser DevTools → Network.
- [ ] Run `curl -v http://example.com` and read the verbose output.
- [ ] Run `curl -i https://example.com` to inspect response headers.
- [ ] Send a POST request with a JSON body using curl and inspect it.
- [ ] Save one raw request and response example in your notes and label every part.

**Prove your understanding**

- [ ] Explain the structure of an HTTP/1.1 request and response from memory.
- [ ] Explain why a server cannot assume one socket read contains a complete request.

---

## Stage 3 — HTTP methods and semantics

- [ ] Understand `GET` and resource retrieval.
- [ ] Understand `HEAD` and why it returns headers without a response body.
- [ ] Understand `POST` and resource-specific processing.
- [ ] Understand `PUT` and replacement semantics.
- [ ] Understand `PATCH` and partial modification.
- [ ] Understand `DELETE`.
- [ ] Understand `OPTIONS` and capability/preflight use cases.
- [ ] Learn the difference between safe and unsafe methods.
- [ ] Learn the difference between idempotent and non-idempotent methods.
- [ ] Understand why method semantics matter for retries, caching, and API design.
- [ ] Understand that a method name does not guarantee that an application implementation behaves correctly.

**Practical lab**

- [ ] Send GET, POST, PUT, PATCH, DELETE, HEAD, and OPTIONS requests to a test endpoint.
- [ ] Record the expected meaning of each method and observe the actual response.
- [ ] Repeat requests and reason about whether repeating them should change the intended result.

**Prove your understanding**

- [ ] Explain safe vs idempotent with examples.
- [ ] Explain why blindly retrying a payment-style POST can be dangerous.

---

## Stage 4 — Status codes, headers, and content

### Status codes

- [ ] Understand the 1xx informational class.
- [ ] Learn common 2xx responses: `200`, `201`, `202`, `204`.
- [ ] Learn common 3xx responses: `301`, `302`, `303`, `304`, `307`, `308`.
- [ ] Learn common 4xx responses: `400`, `401`, `403`, `404`, `405`, `408`, `409`, `415`, `422`, `429`.
- [ ] Learn common 5xx responses: `500`, `502`, `503`, `504`.
- [ ] Understand the difference between 401 Unauthorized and 403 Forbidden.
- [ ] Understand the difference between 502 Bad Gateway, 503 Service Unavailable, and 504 Gateway Timeout.
- [ ] Choose status codes based on protocol semantics rather than convenience.

### Headers and representation

- [ ] Understand request, response, and representation metadata.
- [ ] Learn `Content-Type` and media types.
- [ ] Learn `Accept` and content negotiation.
- [ ] Understand `Content-Encoding` and compression.
- [ ] Learn `Authorization` and `WWW-Authenticate` at a basic level.
- [ ] Learn `Location` for redirects.
- [ ] Learn `Retry-After` and `Vary`.
- [ ] Understand the difference between representation data and transfer framing.

**Practical lab**

- [ ] Create endpoints that return 200, 201, 204, 400, 401, 403, 404, and 500.
- [ ] Inspect how clients display or handle each response.
- [ ] Send different Accept headers and observe content negotiation where supported.

---

## Stage 5 — Cookies, sessions, and authentication

- [ ] Understand why applications sometimes need state across independent HTTP requests.
- [ ] Understand `Set-Cookie` in a response and `Cookie` in a later request.
- [ ] Learn cookie attributes: `Domain`, `Path`, `Expires`, `Max-Age`, `Secure`, `HttpOnly`, and `SameSite`.
- [ ] Understand how a session ID can connect a browser to server-side session data.
- [ ] Understand the difference between cookie-based sessions and bearer tokens.
- [ ] Understand `Authorization: Bearer ...`.
- [ ] Learn the high-level difference between authentication and authorization.
- [ ] Understand why HTTPS matters when credentials or session identifiers travel over a network.
- [ ] Learn common cookie/session security risks, including session theft and CSRF.

**Practical lab**

- [ ] Build a small login/session demonstration in a local app.
- [ ] Inspect the login response and the next authenticated request.
- [ ] Observe how cookie attributes affect browser behavior.
- [ ] Explain where session state is stored in your implementation.

---

## Stage 6 — Caching and conditional requests

- [ ] Understand why HTTP caching exists.
- [ ] Learn `Cache-Control` directives, including `max-age`, `no-cache`, `no-store`, `public`, and `private`.
- [ ] Understand browser caches, shared caches, and CDNs.
- [ ] Learn `ETag` and `If-None-Match`.
- [ ] Learn `Last-Modified` and `If-Modified-Since`.
- [ ] Understand conditional requests and `304 Not Modified`.
- [ ] Understand freshness, revalidation, and cache invalidation trade-offs.
- [ ] Understand how `Vary` changes cache keys.

**Practical lab**

- [ ] Add cache headers to a local endpoint.
- [ ] Inspect browser caching behavior.
- [ ] Test conditional requests using curl.
- [ ] Compare `no-cache` and `no-store`; they do not mean the same thing.

---

## Stage 7 — Redirects, CORS, and browser behavior

### Redirects

- [ ] Understand the `Location` response header.
- [ ] Learn the differences between 301, 302, 303, 307, and 308.
- [ ] Observe how browsers follow redirects.
- [ ] Understand why redirect status can affect whether the method and body are preserved.

### CORS

- [ ] Understand the same-origin policy.
- [ ] Understand an origin: scheme, host, and port.
- [ ] Understand that CORS is a browser-enforced mechanism controlled by response headers, not a general restriction on server-to-server requests.
- [ ] Learn `Access-Control-Allow-Origin`.
- [ ] Learn allowed methods, allowed headers, and exposed headers.
- [ ] Understand preflight requests using `OPTIONS`.
- [ ] Understand when a browser sends a preflight.
- [ ] Understand credentials mode and why wildcard origins cannot be combined with credentialed CORS access.

**Practical lab**

- [ ] Run a frontend and backend on different local ports.
- [ ] Reproduce a CORS error.
- [ ] Inspect the browser's OPTIONS preflight and the response.
- [ ] Fix the CORS configuration and explain exactly what changed.
- [ ] Create a redirect chain and inspect every response.

---

## Stage 8 — HTTPS and TLS

- [ ] Explain the difference between HTTP and HTTPS.
- [ ] Understand encryption, integrity, and server authentication.
- [ ] Learn what TLS is responsible for.
- [ ] Understand certificates and certificate authorities.
- [ ] Learn the high-level TLS 1.3 handshake.
- [ ] Understand certificate hostname validation and trust chains.
- [ ] Understand SNI and ALPN at a high level.
- [ ] Understand why HTTPS does not automatically make an application secure.
- [ ] Understand where TLS sits relative to HTTP and TCP in common HTTP/1.1 and HTTP/2 deployments.

**Practical lab**

- [ ] Run `curl -v https://example.com` and inspect TLS details.
- [ ] Inspect a site's certificate in the browser.
- [ ] Compare an HTTP request with an HTTPS request.
- [ ] Identify what an invalid, expired, or mismatched certificate means.

---

## Stage 9 — HTTP versions and evolution

- [ ] Understand the basic design and limitations of HTTP/1.0.
- [ ] Understand HTTP/1.1 persistent connections and message framing.
- [ ] Understand HTTP/2's binary framing and multiplexed streams.
- [ ] Understand how HTTP/2 addresses some HTTP/1.1 performance limitations.
- [ ] Understand HTTP/3's use of QUIC over UDP.
- [ ] Understand at a high level how QUIC provides transport features and integrates TLS.
- [ ] Compare connection establishment, multiplexing, and head-of-line blocking across versions.
- [ ] Understand that HTTP semantics are shared across versions even though wire formats and transports differ.

**Practical lab**

- [ ] Use `curl --http1.1 -I https://example.com`.
- [ ] Where supported, use curl to inspect HTTP/2 and HTTP/3 negotiation.
- [ ] Inspect the protocol column in browser DevTools.
- [ ] Write a comparison table for HTTP/1.1, HTTP/2, and HTTP/3.

---

## Stage 10 — Main project: build a mini HTTP/1.1 server from a raw TCP socket

**Do not start with `http.createServer()`.** First use Node.js `node:net` so you can see that TCP gives your program bytes and your program must interpret those bytes as HTTP.

### Part A — TCP foundation

- [ ] Create a TCP server using `net.createServer()`.
- [ ] Listen on `localhost` and a port such as `3000`.
- [ ] Accept a client connection.
- [ ] Log when a client connects and disconnects.
- [ ] Read incoming data as bytes / buffers.
- [ ] Write a simple response to the socket.
- [ ] Test the server using netcat or a small TCP client.

### Part B — Inspect a raw HTTP request

- [ ] Send a request using `curl -v http://localhost:3000/`.
- [ ] Print the bytes received by the server.
- [ ] Identify the request line.
- [ ] Identify each header.
- [ ] Identify the header/body separator: `\r\n\r\n`.
- [ ] Send a request containing a body and inspect it.
- [ ] Observe that a request may arrive in multiple chunks.

### Part C — Parse a basic HTTP/1.1 request

- [ ] Separate the start line, headers, and body.
- [ ] Parse the method, request target, and HTTP version.
- [ ] Parse headers without assuming header-name casing.
- [ ] Detect the end of headers.
- [ ] Handle a request body using `Content-Length`.
- [ ] Buffer incomplete data until enough bytes arrive.
- [ ] Reject malformed requests with an appropriate error response.
- [ ] Document the limitations of your parser.

**Important:** Do not assume each TCP chunk is one complete request. TCP is a byte stream. Your parser must account for partial data and HTTP message framing.

### Part D — Construct HTTP responses

- [ ] Write a valid status line.
- [ ] Add `Content-Type`.
- [ ] Calculate and include the correct `Content-Length` in bytes.
- [ ] Add the blank line between headers and body.
- [ ] Return a plain-text response.
- [ ] Return a JSON response.
- [ ] Return an empty 204 No Content response correctly.
- [ ] Return a 404 Not Found response for unknown routes.
- [ ] Test `Connection: close` and close the socket at the appropriate time.

### Part E — Add application behavior

- [ ] Implement `GET /`.
- [ ] Implement `GET /health`.
- [ ] Implement `GET /users`.
- [ ] Implement `GET /users/:id`.
- [ ] Implement `POST /users` with a JSON request body.
- [ ] Validate malformed JSON and missing fields.
- [ ] Return sensible status codes.
- [ ] Add a small in-memory data store.
- [ ] Separate request parsing, routing, and response writing into different functions/modules.

### Part F — Test and compare

- [ ] Test routes using curl.
- [ ] Test with a browser.
- [ ] Test with a separate Node.js client.
- [ ] Test missing routes, malformed requests, and incomplete bodies.
- [ ] Test a body larger than one incoming TCP chunk.
- [ ] Verify response `Content-Length` using byte length, not JavaScript character count.
- [ ] Compare your implementation with Node.js `http.createServer()`.
- [ ] Write down what the built-in HTTP implementation handles that your educational server does not.

**Scope and safety:** This is a learning project, not a production HTTP implementation. Start with one request per connection and `Connection: close`. Do not expose it publicly or use it for sensitive data. Correctly supporting persistent connections, chunked bodies, pipelining, and all HTTP edge cases requires substantially more work. Use Node.js's built-in HTTP implementation for real applications.

---

## Stage 11 — HTTP in real application architecture

- [ ] Understand reverse proxies and why they sit in front of application servers.
- [ ] Understand load balancers and how they distribute HTTP traffic.
- [ ] Understand TLS termination at a proxy/load balancer.
- [ ] Understand forwarded headers such as `Forwarded` and `X-Forwarded-For`.
- [ ] Understand API gateways at a high level.
- [ ] Understand rate limiting and request timeouts.
- [ ] Understand connection pooling and keep-alive behavior.
- [ ] Understand how HTTP fits into microservices.
- [ ] Connect HTTP retries and idempotency to distributed-system reliability.

**Practical lab**

- [ ] Put a reverse proxy in front of a local application.
- [ ] Inspect request and response headers before and after the proxy.
- [ ] Simulate a slow upstream service and observe timeout behavior.
- [ ] Draw the request path through client, proxy, application, and database.

---

## Stage 12 — HTTP security essentials

- [ ] Understand why HTTPS is necessary but not sufficient for application security.
- [ ] Learn request validation and safe handling of untrusted input.
- [ ] Understand authentication versus authorization.
- [ ] Learn CSRF and the role of SameSite cookies and anti-CSRF defenses.
- [ ] Understand XSS and why output encoding matters.
- [ ] Understand CORS misconfiguration risks.
- [ ] Learn the basics of request smuggling and why inconsistent message framing is dangerous.
- [ ] Understand security headers such as `Content-Security-Policy`, `Strict-Transport-Security`, and `X-Content-Type-Options`.
- [ ] Understand why secrets and sensitive data should not be placed in URLs.

---

## Final project — Explain and demonstrate an HTTP exchange

Before considering this roadmap complete:

- [ ] Capture a real HTTP request and response.
- [ ] Annotate every part of the request and response.
- [ ] Explain how the client found the server.
- [ ] Explain how the connection was established.
- [ ] Explain how HTTP message boundaries were determined.
- [ ] Explain how the server selected a handler and created a response.
- [ ] Explain how the browser interpreted the response.
- [ ] Demonstrate the mini server and its tests.
- [ ] Compare the mini server with Node.js's built-in HTTP server.
- [ ] Write a short explanation of HTTP/1.1, HTTP/2, and HTTP/3.

## Commands and tools to practice

- [ ] `curl -v` — inspect requests, responses, and connection details.
- [ ] `curl -i` — include response headers in output.
- [ ] `curl -X` — choose a request method.
- [ ] `curl -H` — add request headers.
- [ ] `curl -d` — send request data.
- [ ] `curl --http1.1` — force HTTP/1.1 where supported.
- [ ] Browser DevTools → Network — inspect browser HTTP traffic.
- [ ] `nc` / netcat — interact with a TCP socket manually.
- [ ] Wireshark — inspect packets and protocol exchanges.
- [ ] Node.js `node:net` — build a raw TCP server and client.
- [ ] Node.js `node:http` — compare against a real HTTP implementation.

## Reference material

Use standards and documentation to resolve details; use tutorials as supporting explanations.

- [MDN — An overview of HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview)
- [MDN — HTTP messages](https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages)
- [MDN — HTTP request methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)
- [MDN — HTTP response status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
- [RFC 9110 — HTTP Semantics](https://www.rfc-editor.org/rfc/rfc9110)
- [RFC 9112 — HTTP/1.1](https://www.rfc-editor.org/rfc/rfc9112)
- [RFC 9113 — HTTP/2](https://www.rfc-editor.org/rfc/rfc9113)
- [RFC 9114 — HTTP/3](https://www.rfc-editor.org/rfc/rfc9114)
- [Node.js — net](https://nodejs.org/api/net.html)
- [Node.js — http](https://nodejs.org/api/http.html)
- [curl manual](https://curl.se/docs/manpage.html)

## Questions and discoveries

Add questions here whenever an experiment reveals something you cannot yet explain.

- **Question:**
  - What I observed:
  - My current explanation:
  - What I still need to investigate:
  - Experiment / reference:
  - Final explanation:
