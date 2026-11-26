# OWASP Top 10:2025 analysis

## Assessment scope

- **Assessment type:** Static review of this repository's lab configuration and learning materials.
- **In scope:** `docker-compose.yml`, setup instructions, and the intended safe-use boundaries.
- **Out of scope:** Runtime testing of Juice Shop, application source review, the host operating system, Docker daemon configuration, and any network other than the local lab.
- **Runtime validation:** Not performed; Docker is unavailable in the assessment environment.
- **Conclusion:** No application vulnerability is claimed. This is a limited configuration review, not a penetration test or a complete security assessment.

## Category review

| Category | Static observation | Status |
| --- | --- | --- |
| A01 Broken Access Control | No application authorization code is included in this repository; runtime behavior was not tested. | Not assessed |
| A02 Security Misconfiguration | Compose publishes the target on `127.0.0.1:3000` and uses an internal network. Runtime binding and isolation were not verified. | Configuration observed; runtime unverified |
| A03 Software Supply Chain Failures | The training image is pinned to the upstream `v20.4.0` release tag. An immutable image digest is not specified. | Version tag pinned; digest not verified |
| A04 Cryptographic Failures | No application cryptography or sensitive-data handling was assessed. | Not assessed |
| A05 Injection | No application source or runtime input handling was assessed. | Not assessed |
| A06 Insecure Design | No application threat model or design artifacts were assessed. | Not assessed |
| A07 Authentication Failures | No application authentication flow was tested. | Not assessed |
| A08 Software or Data Integrity Failures | No application update, build, or data-integrity flow was assessed. | Not assessed |
| A09 Security Logging and Alerting Failures | No application logging or alerting behavior was assessed. | Not assessed |
| A10 Mishandling of Exceptional Conditions | No application exception or failure behavior was tested. | Not assessed |

## Hardening recommendation

For repeatable training, keep the image on an approved version and consider pinning its immutable digest after verifying it through the official image source. Review image updates deliberately rather than pulling an unreviewed `latest` tag.

## Limitations

The Compose file was inspected as text, but Docker Compose could not be run in the assessment environment. The internal-network and loopback-only properties therefore remain unverified at runtime. Complete a local smoke check before using this lab; do not broaden the target if setup fails.

## References

- [OWASP Top 10:2025](https://owasp.org/Top10/2025/)
- [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/)
