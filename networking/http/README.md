# HTTP — Hypertext Transfer Protocol

## 1. What problem does HTTP solve?

A client (browser, mobile app, or service) needs a standard way to ask a server for a resource or request an operation. The programs may use different languages and operating systems. HTTP defines a shared application-level request/response protocol so they can communicate without knowing each other's implementation.

## 2. Why was HTTP created?

The Web needed an interoperable way to retrieve linked documents across a network. HTTP began as a simple document-retrieval protocol and evolved into a general protocol used by websites, APIs, media, and distributed services.

A simplified evolution:
- **HTTP/1.0:** simple request/response exchanges.
- **HTTP/1.1:** persistent connections, host-based virtual hosting, caching improvements.
- **HTTP/2:** multiplexed streams and more efficient framing over a connection.
- **HTTP/3:** HTTP semantics over QUIC, which uses UDP and integrates modern transport security.

## 3. How does HTTP work?

At a high level:

1. The client identifies the target URL.
2. DNS may resolve the hostname to an IP address.
3. The client establishes or reuses a transport connection (TCP for HTTP/1.1 and HTTP/2; QUIC for HTTP/3).
4. For HTTPS, TLS—or the security built into QUIC—protects communication and authenticates the server.
5. The client sends a request: method, target, headers, and optionally a body.
6. The server or an intermediary processes it.
7. The server returns a response: status code, headers, and optionally a body.
8. The client interprets the response. Caches and connection pools may affect the exchange.

Example request:

```http
GET /products/42 HTTP/1.1
Host: example.com
Accept: application/json
```

Example response:

```http
HTTP/1.1 200 OK
Content-Type: application/json

{"id":42,"name":"Keyboard"}
```

## 4. Core concepts

- **Methods:** GET, POST, PUT, PATCH, DELETE, HEAD, OPTIONS.
- **Status codes:** 2xx success, 3xx redirection, 4xx client errors, 5xx server errors.
- **Headers:** metadata for content negotiation, authentication, caching, and more.
- **Body:** optional representation or submitted data.
- **Stateless semantics:** each request carries the information needed to interpret it; applications can still maintain sessions using cookies or tokens.
- **Safe and idempotent methods:** understand the difference and why retries depend on it.
- **Cookies and sessions:** how state is associated with otherwise independent requests.
- **Caching:** Cache-Control, validators, freshness, and revalidation.
- **CORS:** a browser-enforced cross-origin access policy, not a general server-to-server networking restriction.
- **HTTPS:** HTTP protected by TLS.

## 5. Practical labs

1. Run `curl -v https://example.com` and inspect connection and response details.
2. Use browser DevTools → Network. Inspect method, URL, request/response headers, status, timing, and payload.
3. Build a tiny HTTP server without a framework. Parse a request and return a response.
4. Compare GET and POST. Test missing headers or bodies.
5. Add a cache header and observe browser behavior.
6. Send an OPTIONS request and inspect a CORS preflight.
7. Observe redirects and explain each response in the chain.

## 6. Failure modes

- **DNS failure:** can the hostname be resolved?
- **Connection refused:** is a process listening on the target port?
- **Timeout:** where might the request be stuck?
- **TLS error:** did certificate validation or protocol negotiation fail?
- **401 vs 403:** is authentication missing/invalid, or is access forbidden?
- **404 vs 500:** is the resource absent, or did server processing fail?
- **CORS error:** what did the browser block, and what did the server return?
- **Duplicate operation after retry:** was the operation safe/idempotent?

## 7. Trade-offs and connections

HTTP does not guarantee that a business operation succeeds exactly once. It does not remove network latency or make a server reliable. Connect this topic to TCP/QUIC, DNS, TLS, caching, load balancing, API design, authentication, and distributed systems.

## 8. Explain it back

Without notes, explain:
- What happens after entering a URL in a browser?
- What is the difference between HTTP and HTTPS?
- Why are methods and status codes useful?
- What is the difference between stateless protocol semantics and application sessions?
- Why can a request time out even if the server eventually completes the work?

## 9. Open questions

Add questions here whenever an experiment exposes something you cannot yet explain.