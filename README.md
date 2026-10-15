# Tontouma Bot API Gateway

Zuplo API gateway configuration for the Tontouma Bot MVP. The OpenAPI specification in `config/routes.oas.json` documents the prioritized backend endpoints used by the application.

## Scope

The current specification focuses on the MVP's core user stories, including organization/service information and the access-ticket entry point for the AI conversation flow. The text-streaming and voice-WebSocket conversation channels are specified separately and are not implemented by this gateway configuration.

## API contract

- OpenAPI specification: `config/routes.oas.json`
- Production base URL in the spec: `https://api.tontoumabot.sn/api/v1` (marked as **to be confirmed**)
- Local development base URL: `http://localhost:8080/api/v1`
- Authentication: Clerk bearer JWT for protected endpoints; public and access-ticket endpoints are documented separately in the spec.

Always treat the OpenAPI file as the source of truth for the currently declared endpoints and schemas. A declared route or server URL does not by itself prove that the backend is deployed or reachable.

## Local development

Requirements: Node.js and a package manager supported by Zuplo.

```bash
npm install
npm run dev
```

The local gateway runs on port 9000 by default. OpenAPI routes can be edited in `config/routes.oas.json`.

## Validation checklist

Before release, verify that:
- the gateway's declared routes match the backend implementation;
- auth requirements are enforced by the deployed services;
- production URLs and CORS settings are correct;
- no API keys, JWTs, or environment secrets are committed.
