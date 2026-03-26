# Project 3 — Internal API Documentation Portal

## Purpose

Build a centralised, searchable **API documentation portal** for internal engineering teams. The portal will auto-generate docs from OpenAPI specs and provide interactive "Try It" consoles.

---

## Key Features

### Must Have

- Auto-generated reference docs from OpenAPI 3.1 specs
- Interactive request/response playground
- Authentication token management (OAuth2 + API key)
- Versioned documentation (v1, v2, etc.)
- Full-text search with filters

### Nice to Have

- SDK code samples in Python, JavaScript, Go, and Ruby
- Changelog feed per API version
- Rate-limit dashboard per consumer

---

## API Inventory

| Service           | Version | Endpoints | Status        | Owner          |
|-------------------|:-------:|----------:|---------------|----------------|
| Users API         | v2      |        14 | Documented    | Team Alpha     |
| Payments API      | v3      |        22 | Partial       | Team Bravo     |
| Notifications API | v1      |         8 | Missing       | Team Charlie   |
| Analytics API     | v2      |        31 | Documented    | Team Delta     |
| Inventory API     | v1      |        17 | Partial       | Team Alpha     |

### Sample OpenAPI Snippet

```json
{
  "openapi": "3.1.0",
  "info": {
    "title": "Users API",
    "version": "2.0.0",
    "description": "Manage user accounts, profiles, and preferences."
  },
  "paths": {
    "/users/{id}": {
      "get": {
        "summary": "Get user by ID",
        "parameters": [
          {
            "name": "id",
            "in": "path",
            "required": true,
            "schema": { "type": "string", "format": "uuid" }
          }
        ],
        "responses": {
          "200": {
            "description": "User found",
            "content": {
              "application/json": {
                "schema": { "$ref": "#/components/schemas/User" }
              }
            }
          },
          "404": { "description": "User not found" }
        }
      }
    }
  }
}
```

---

## Technical Decisions

### Tool Selection

We evaluated three documentation platforms:

1. **Redocly** — Best rendering quality, but expensive at scale
2. **Stoplight** — Good collaboration features, limited customisation
3. **Swagger UI + Custom Theme** — Maximum flexibility, more maintenance

**Decision:** Go with **Redocly** for external-facing APIs and a custom **Swagger UI theme** for internal APIs.

> *Rationale:* Internal teams value flexibility over polish, while external consumers need a premium experience. This hybrid approach balances cost and quality.

### Hosting Architecture

```
                    ┌──────────────────┐
                    │   GitLab CI/CD   │
                    │  (build on push) │
                    └────────┬─────────┘
                             │
              ┌──────────────┼──────────────┐
              ▼              ▼              ▼
        ┌──────────┐  ┌──────────┐  ┌──────────┐
        │ Users v2 │  │ Pay. v3  │  │ Notif v1 │
        │  (HTML)  │  │  (HTML)  │  │  (HTML)  │
        └────┬─────┘  └────┬─────┘  └────┬─────┘
             └──────────────┼──────────────┘
                            ▼
                    ┌──────────────┐
                    │  S3 + CDN    │
                    │ (static host)│
                    └──────────────┘
```

---

## Definition of Done

- [ ] All 5 services have complete OpenAPI specs
- [ ] Portal renders all endpoints with examples
- [ ] Search returns results in < 200ms
- [ ] "Try It" console works with staging credentials
- [ ] Access control respects team-level permissions
- [ ] CI pipeline rebuilds docs on spec changes

## Budget

| Item                  | Quarterly Cost |
|-----------------------|---------------:|
| Redocly licence       |         $1,200 |
| S3 + CloudFront       |            $45 |
| CI/CD compute         |            $30 |
| **Total**             |     **$1,275** |

---

## Contacts

For questions, reach out in `#api-docs` on Slack or email the API Platform team.

---

*Last updated: 2026-03-20*
