# Tasks: Documenting Cryptographic Signing & API Specification

## Checklist

### 1. Endpoint Mapping
- [X] **Task 1.1:** Analyze `handle_challenge` endpoint parameters (`cid`, `nonce_hex`, `expires_at`, `validator_hotkey_hex`) and response payload structure.
    - *Verification:* Document mapping complete in `docs/api-map.md`.
- [X] **Task 1.2:** Analyze `/stats` endpoint for required authentication headers.
    - *Verification:* Documented headers and payload structure in `docs/api-map.md`.

### 2. OpenAPI Security Design
- [X] **Task 2.1:** Design `securitySchemes` for `sr25519` signed challenges and HMAC-based validation in OpenAPI 3.0 format.
    - *Verification:* Security schema definition drafted.

### 3. Documentation Generation & Validation
- [X] **Task 3.1:** Create `docs/openapi.yaml` incorporating the mapped endpoints and security schemes.
    - *Verification:* File created.
- [X] **Task 3.2:** Validate `docs/openapi.yaml` against OpenAPI 3.0 specification.
    - *Verification:* Validation successful.
