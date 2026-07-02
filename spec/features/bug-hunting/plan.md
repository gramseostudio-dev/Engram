# Plan: Cryptographic Signing Bug Fix

## 1. Executive Summary
The cryptographic signing mechanism in `neurons/miner.py` for `ChallengeSynapse` uses HMAC-SHA256, which relies on a nonce and validator hotkey. We need to audit this implementation against Bittensor's standard signing practices to ensure that the challenges issued to validators are cryptographically sound and tamper-proof.

## 2. Architecture & Data Flow
### 2.1 Cryptographic Challenge Flow
1. **Validator Request:** Validator sends `ChallengeSynapse` containing `cid`, `nonce_hex`, `expires_at`, and its `validator_hotkey_hex`.
2. **Miner Derivation:** 
   - `_derive_hmac_key`: Derives key using `validator_hotkey_hex` + `nonce_bytes`.
   - `_hash_embedding`: Hashes stored embedding.
   - `_compute_proof`: HMAC-SHA256 over `embedding_hash` using derived key.
3. **Response:** Miner returns `{embedding_hash, proof}`.

### 2.2 Affected Code Paths
- `neurons/miner.py`:
  - `_derive_hmac_key` (Line 72)
  - `_compute_proof` (Line 77)
  - `_proof_response_for_challenge` (Line 90)
  - `handle_challenge` (Line 860)

## 3. Risks & Hazards
- **Vulnerability:** If `validator_hotkey_hex` is missing or default-filled improperly, the HMAC key may be easily guessable.
- **Dependency:** Reliance on `engram_core` (Rust) for performance-critical proofs creates a parity risk if the Python fallback implementation differs or is less secure.

## 4. Proposed Investigation Steps
- [ ] Review `engram.miner.auth.verify_request` implementation (referenced in `handle_challenge`).
- [ ] Validate how `validator_hotkey_hex` is obtained and passed to `_proof_response_for_challenge`.
- [ ] Verify consistency of HMAC derivation against Bittensor standards.
- [ ] Ensure `/stats` and `/ChallengeSynapse` handlers log appropriate debugging info when signature/HMAC verification fails.
