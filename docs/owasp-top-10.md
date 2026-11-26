# OWASP Top 10:2025 overview

The OWASP Top 10 is an awareness document, not a complete security standard or a ranking of every possible risk. Use the [official OWASP Top 10 site](https://owasp.org/Top10/) as the source of truth for current wording and supporting material.

The following summaries are defensive learning notes. The lab focuses on recognizing design and code risks, validating expected behavior safely, and documenting mitigations—not exploiting them.

| Category | What to understand | Defensive focus |
| --- | --- | --- |
| A01 Broken Access Control | Users may reach data or actions beyond their permissions. | Enforce authorization server-side for each operation and resource. Deny by default. |
| A02 Security Misconfiguration | Unsafe defaults, excessive exposure, or inconsistent settings increase risk. | Harden production configuration, remove unused features, and keep error details private. |
| A03 Software Supply Chain Failures | Risk in dependencies, build systems, vendors, and delivery processes. | Inventory dependencies, pin and review updates, protect build credentials, and verify provenance. |
| A04 Cryptographic Failures | Sensitive data may not receive suitable protection. | Minimize sensitive data, use established cryptographic libraries, and protect keys and secrets. |
| A05 Injection | Untrusted input may be interpreted as part of a command or query. | Use parameterized APIs, context-aware output encoding, and strict server-side validation. |
| A06 Insecure Design | Missing security requirements or threat modeling can create systemic weaknesses. | Define trust boundaries, abuse cases, and security requirements before implementation. |
| A07 Authentication Failures | Identity and session controls may be weak or incorrectly implemented. | Use secure authentication flows, protected sessions, rate limits, and safe recovery processes. |
| A08 Software or Data Integrity Failures | Untrusted updates or data may be accepted without adequate integrity checks. | Verify trusted sources and signatures where applicable; protect CI/CD and update processes. |
| A09 Security Logging and Alerting Failures | Important security events may not be recorded or acted upon. | Log meaningful events, protect logs, avoid secrets, and define alert ownership and response. |
| A10 Mishandling of Exceptional Conditions | Errors, edge cases, and failures may leave the application in an unsafe state. | Fail safely, handle exceptions consistently, and test boundary and failure conditions. |

## How to use this list

For each category, write down:

1. A plausible design or implementation risk (do not create a real exploit).
2. The control that should prevent it.
3. A safe regression test using ordinary application behavior or a code-level unit test.
4. The evidence needed to show that the control works.

The Top 10 is updated periodically. Confirm category titles against the official OWASP page before presenting or submitting work.
