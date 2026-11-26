# Demo walkthrough

Suggested 5–7 minute walkthrough for a portfolio or class submission. Demonstrate the process and controls, not an exploit.

## Before recording

- Start the Juice Shop container and verify the address is exactly `127.0.0.1:3000`.
- Close unrelated tabs and applications.
- Use synthetic data only. Ensure no credentials, cookies, tokens, or personal information are visible.
- Prepare the completed templates with findings clearly marked as observed, inferred, or not tested.

## Walkthrough

1. **Scope (30 sec):** Show the loopback-only target and explain the authorization boundary.
2. **HTTP flow (60 sec):** Show one normal request/response and explain method, status, headers, and the role of HTTPS.
3. **Identity and access (60 sec):** Explain authentication vs. authorization and why every protected server operation needs an authorization check.
4. **OWASP analysis (90 sec):** Explain the static configuration review, its OWASP mapping, and which categories were not assessed.
5. **Remediation (90 sec):** Show the version-pinned image reference and explain why an immutable digest can improve reproducibility; distinguish this hardening note from an application vulnerability.
6. **Documentation (60 sec):** Show the report's scope, evidence, limitations, recommendation, and safe verification plan.
7. **Cleanup (30 sec):** Run `docker compose down` and confirm the lab is stopped.

## Presenter checklist

- [ ] No out-of-scope targets or data appeared on screen.
- [ ] No active scanner, fuzzer, exploit, or credential testing was run.
- [ ] Claims are backed by observations and clearly labeled.
- [ ] Repository and attribution links are visible.
- [ ] The intentionally vulnerable app is described as local-only training software.
