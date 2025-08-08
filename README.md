# Node.js Core Modules Comparison — `http`, `https`, `http2`

This document compares three core Node.js modules: `http`, `https`, and `http2`, covering their purposes, protocol differences, and real-world use cases.

---

## 📦 Purpose of Each Module

| Module  | Purpose |
|---------|---------|
| **`http`** | Implements the HTTP/1.1 protocol for creating web servers and making HTTP requests. No encryption by default. |
| **`https`** | Same API as `http`, but adds TLS/SSL support for encrypted communication (HTTPS). |
| **`http2`** | Implements the HTTP/2 protocol with performance improvements like multiplexing, header compression, and server push. Supports both encrypted (`createSecureServer`) and unencrypted (`createServer`) modes. |

---

## 🔑 HTTP/1.1 vs HTTP/2 — Key Technical Differences

| Feature | HTTP/1.1 (`http` / `https`) | HTTP/2 (`http2`) |
|---------|-----------------------------|------------------|
| **Protocol** | HTTP/1.1 | HTTP/2 |
| **Connections** | One request per TCP connection (may use keep-alive but still sequential) | Multiple parallel streams over a single connection (multiplexing) |
| **Header Compression** | No | Yes (HPACK algorithm) |
| **Server Push** | No | Yes |
| **Latency** | Higher (head-of-line blocking possible) | Lower (parallel streams reduce blocking) |
| **TLS Requirement** | Optional in `http`, required in `https` | Commonly used with TLS but can run without it |

---

## 🚀 When to Use Each Module

### `http`
- Lightweight HTTP/1.1 server or client.
- Local development, simple APIs, or internal services without encryption.
- Legacy support for clients that don’t handle HTTPS or HTTP/2.

### `https`
- Public-facing production applications.
- Secure APIs where data encryption and integrity are critical.
- SEO and compliance requirements (e.g., browsers marking HTTP as “Not Secure”).

### `http2`
- High-performance apps needing lower latency.
- Serving many small assets (SPAs, static sites) efficiently.
- Modern browsers and environments that support HTTP/2.
- Use alongside a fallback to `https` for older clients.


