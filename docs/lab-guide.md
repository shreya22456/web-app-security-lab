# Secure web application lab

## Scope and setup

The only allowed target is the local OWASP Juice Shop container at `http://127.0.0.1:3000`. Start it using the repository's Compose file. Do not change the port binding or target another service.

This lab is intentionally non-invasive. Use ordinary browsing, code review, passive proxy observations, and written remediation. Do not run active scans, fuzzers, brute-force checks, exploit attempts, or denial-of-service tests.

## 1. Identify

Create a scope note before opening the target:

- Target: `http://127.0.0.1:3000`
- Owner: your local lab
- Time window:
- Out of scope: every other host, address, service, and network

Browse the home page using normal navigation. In browser developer tools, observe a small number of requests and note methods, status codes, and security-relevant response headers. Do not capture or record cookie values, credentials, or personal data.

If using OWASP ZAP, use it only as a local proxy for passive observation. Do not launch an active scan or spider/crawl. Stop if the browser leaves the loopback target.

## 2. Test safely

Turn observations into test questions about expected behavior, not attack payloads. Examples:

- Does the application distinguish authentication from authorization?
- Are errors generic to users while useful diagnostics remain server-side?
- Are security-sensitive responses configured with appropriate headers?
- Does the code use parameterized database APIs and safe rendering primitives?
- Are security events logged without secrets?

For behaviors that require identity or permissions, review the documented flow and corresponding code or unit tests. Do not guess credentials or attempt to access another user's data.

## 3. Fix in owned code

Juice Shop is a third-party training target; do not patch, exploit, or deploy it. For each observation, write a proposed remediation for an application you own. Use [secure coding patterns](secure-coding-patterns.md) and keep the fix at the correct trust boundary.

Where possible, express the expected control as a unit or integration test against a deliberately local, synthetic fixture. Test normal allowed and denied outcomes without crafting exploit strings.

## 4. Document

Complete the three templates in `deliverables/`. Distinguish:

- **Observed**: directly verified in the local lab.
- **Inferred**: a concern suggested by code or configuration that needs owner validation.
- **Not tested**: outside the safe scope or not assessed.

Do not claim a finding based only on a tool alert. Include enough redacted evidence to support the observation and a practical remediation.

## 5. Clean up

```bash
docker compose down
```

Close the browser proxy, delete unnecessary local captures, and confirm the target is no longer running.
