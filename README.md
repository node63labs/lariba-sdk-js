# Lariba Cloud JavaScript SDK

Official JavaScript/TypeScript SDK for integrating applications with **Lariba Cloud**.

The current public SDK surface focuses on **event ingestion**. It provides a small client for sending application events to the Lariba Cloud API without exposing Lariba Cloud's private production implementation.

## Installation

The SDK is currently installed directly from GitHub:

```bash
npm install github:node63labs/lariba-sdk-js
```

The current package name is `lariba-sdk`.

## Usage

```javascript
import { Lariba } from "lariba-sdk"

const apiKey = process.env.LARIBA_API_KEY
const baseUrl = process.env.LARIBA_API_BASE_URL ?? "http://localhost:8000"

if (!apiKey) {
  throw new Error("LARIBA_API_KEY is required")
}

const lariba = new Lariba(apiKey, baseUrl)

await lariba.track("user.signup", {
  plan: "starter"
})
```

## API

### `new Lariba(apiKey, baseUrl?)`

Creates a Lariba Cloud client.

- `apiKey` — Lariba Cloud API key.
- `baseUrl` — optional API base URL. The current SDK defaults to `http://localhost:8000` for local development.

### `lariba.track(eventName, properties?)`

Sends an event to the Lariba Cloud event-ingestion API.

```javascript
await lariba.track("payment.completed", {
  amount: 29,
  currency: "USD"
})
```

## Public developer resources

- [Lariba Cloud API specification](https://github.com/node63labs/lariba-spec)
- [Lariba Cloud developer documentation](https://github.com/node63labs/lariba-docs-site)
- [NODE63 Labs](https://github.com/node63labs)

## Repository boundary

This repository contains the public developer-facing SDK only. Lariba Cloud production applications, control-plane implementation, operational infrastructure, security-sensitive systems, and proprietary automation are maintained outside this public repository.

## Security

Do not report credentials, API keys, secrets, or suspected vulnerabilities in public issues. Follow the security-reporting guidance published by NODE63 Labs or the relevant Lariba Cloud developer resource.

## License

Licensed under the [ISC License](./LICENSE).

Copyright © 2026 NODE63 Labs.
