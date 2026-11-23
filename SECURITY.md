# Security policy — public integrity-only ledger

This repository is public. Any file, commit, author, timestamp, and update frequency can be observed or copied permanently.

## Forbidden content

Never add customer or employee information, business data, source code from private repositories, deployment addresses, VPS metadata, secrets, access tokens, file paths, financial positions, task content, model prompts or logs. Never store a bare hash of a guessable/private value.

## Future commitments — not yet enabled

A future record may contain only:
- version: strictly increasing positive integer;
- instance: random opaque identifier unrelated to any project;
- commitment: fixed-length cryptographic commitment constructed with proper secret randomization from private state;
- previous_commitment: previous commitment for chain verification.

No raw private state, and no salt/secret/nonce that would make low-entropy private data guessable. The implementation must be separately audited. Identifiers and timing remain public metadata.

## Operational guardrails

1. DISABLED by default. No writer, job, webhook, broker, or auto-initializer is authorized by this file.
2. Check repository identity, authenticated writer permissions and actual branch protection before initialization.
3. Disable force pushes and branch deletion; review bypass and admin permissions. Do not mandate pull requests if a future controlled writer requires immediate compare-and-swap updates; choose a policy compatible with tested writes.
4. Pin the last independently trusted remote version/commitment. On any mismatch, missing record, 403/404/429, timeout, stale compare-and-swap, or unverifiable status: fail closed and do not reissue external actions.
5. Never claim a GitHub commit alone provides tamperproof or irreversible writes: maintainers can change security rules and fast-forward new history with invalid content.
6. Establish a separate trusted checkpoint or monitor and verify restart, loss and rollback scenarios before using this repository to authorize real actions.

Status: documentation only. No witness records. No real external execution.
