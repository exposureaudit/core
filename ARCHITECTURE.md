# Architecture: Zero-Trust ExposureAudit

## Data Flow
1. Client uploads CSV → encrypted via HTTPS
2. System generates SHA-256+salt hashes of identities
3. Queries ethical APIs (HIBP, DeHashed, Vigilante)
4. Enriches findings with risk scores + dark web context
5. Generates report → delivers via secure link
6. Auto-deletes all data after 5 minutes

## Security Pillars
- No persistent storage
- Ephemeral containers (Docker)
- MFA + IP allowlist for admins
- End-to-end TLS 1.3
- Open-source core (AGPLv3)

## Scalability
- Queued processing (Celery/RQ)
- Batched API calls
- Delta updates for recurring audits
