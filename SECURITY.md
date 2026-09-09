# Security and deployment boundary

## Current application

Vynix Studio Web is a static GitHub Pages site. It has no server-side runtime, database, authentication system, Control Panel API, file upload path, session store, or server-management capability. The dashboard is a public read-only presentation of official product metadata fetched from Modrinth.

Do not add passwords, API keys, tokens, database credentials, or private control-plane URLs to this repository. Browser storage is not an authentication mechanism.

## Required production architecture for a real Control Panel

```text
CDN/WAF/DDoS provider
  -> reverse proxy / load balancer
  -> authenticated application API
  -> private database and server-management workers
```

The API must enforce authorization server-side on every route. Use Argon2id or scrypt for passwords, short-lived secure sessions with rotation and revocation, CSRF protection for cookie-authenticated state changes, strict schema validation, parameterized database queries, bounded pagination, request and upstream timeouts, upload type and size allowlists, and structured security-event logging without secrets.

Configure the reverse proxy to:

- trust forwarded client IP headers only from known proxy CIDRs;
- reject invalid host headers and enforce HTTPS;
- apply managed WAF rules and per-IP/per-user/per-route limits at the edge;
- cap request body size and connection duration;
- return `429` with `Retry-After` for throttled requests;
- isolate the API and server workers from the public network.

Application-level throttling is defense in depth and cannot stop volumetric attacks. A CDN/WAF provider and capacity plan are required for DDoS protection.

## Static hosting headers

GitHub Pages does not provide an application server or a repository-controlled response-header configuration. Configure these at the CDN or reverse proxy: HSTS, `Content-Security-Policy`, `X-Content-Type-Options: nosniff`, `Referrer-Policy: strict-origin-when-cross-origin`, `Permissions-Policy`, and `frame-ancestors`/`X-Frame-Options`. The page includes a compatible CSP meta policy as a client-side fallback, but response headers are stronger.

## Safe verification

Use local or staging tests for authentication, authorization, invalid input, request limits, rate limits, upload validation, and timeout behavior. Do not run stress or DDoS tests against production infrastructure.
