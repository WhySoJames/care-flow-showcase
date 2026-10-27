# Architecture Notes

This document provides a high-level view of Care-Flow's technical design. Production credentials, schemas containing private data, and proprietary application code are intentionally excluded.

## Delivery Flow

```text
Developer -> GitHub -> CI/CD -> Vercel
                           |
User -> Cloudflare -> Application -> Supabase
                                      |-- Auth
                                      +-- PostgreSQL
```

## Design Principles

- Keep environment secrets outside source control.
- Represent database changes as repeatable migrations.
- Separate user roles and permissions.
- Use managed cloud services where they reduce operational overhead.
- Keep deployment repeatable through source-controlled automation.

## Portfolio Scope

This public repository describes the engineering approach without mirroring the private production repository.
