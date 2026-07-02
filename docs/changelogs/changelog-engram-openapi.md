# Pull Request: OpenAPI Documentation for Engram Miner API

## Description
This Pull Request introduces comprehensive API documentation for the Engram Miner API, specifically mapping key endpoints (`/ChallengeSynapse`, `/stats`) and defining the security schemes required for validator-miner interactions (sr25519 signatures and HMAC challenge proofs).

## Changes
- **API Mapping:** Created `docs/api-map.md` to document request/response payloads and authentication requirements for `ChallengeSynapse` and `/stats`.
- **OpenAPI Specification:** Generated `docs/openapi.yaml` (OpenAPI 3.0.3) containing:
    - Path definitions for key endpoints.
    - Security scheme definitions (`Sr25519Signature`, `HmacChallengeProof`).
- **Feature Specification:** Established `spec/features/bug-hunting/` with `spec.md`, `plan.md`, and `tasks.md` to guide the implementation.

## Verification Steps
1. **Endpoint Analysis:** Verified parameter and payload structures against `neurons/miner.py`.
2. **Schema Design:** Drafted security schemes based on Bittensor cryptographic standards.
3. **YAML Validation:** Performed structural validation of `docs/openapi.yaml` to ensure conformance with OpenAPI 3.0.3 standards.
