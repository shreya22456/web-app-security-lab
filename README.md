# Web Application Security Lab

A defensive, beginner-friendly learning module covering HTTP, cookies and sessions, authentication and authorization, the OWASP Top 10, secure coding, and a controlled local lab.

The practice target is OWASP Juice Shop, an intentionally vulnerable training app. It is published only on `127.0.0.1` and attached to an internal Docker network. This repository does not include exploit payloads or instructions for testing third-party systems.

## Safety and authorization

- Run the target only on a machine you control. Do not expose port `3000` to a LAN or the internet.
- The target is intentionally vulnerable. Start it only for the exercise and stop it when finished.
- Stay within `http://127.0.0.1:3000`. Do not test any public website, IP, or other local service.
- This lab uses observation, passive proxy analysis, code review, and remediation planning. Do not perform active scans, fuzzing, credential guessing, exploit attempts, or denial-of-service testing.
- Do not save or share cookies, credentials, personal data, raw traffic, or browser profiles.

## Learning path

1. [HTTP, cookies, sessions, and access control](docs/http-and-sessions.md)
2. [OWASP Top 10:2025 overview](docs/owasp-top-10.md)
3. [Secure coding patterns](docs/secure-coding-patterns.md)
4. [Identify → Test → Fix → Document lab](docs/lab-guide.md)
5. Complete the [OWASP analysis](deliverables/owasp-analysis.md), [vulnerability report](deliverables/vulnerability-report.md), and [remediation plan](deliverables/remediation-recommendations.md).
6. Follow the [demo walkthrough](docs/demo-walkthrough.md).

## Prerequisites

- Docker Engine and the Docker Compose plugin.
- A modern browser.
- Optional: OWASP ZAP for passive observation only. Use its official download and setup instructions.
- Optional: a code editor for reviewing the remediation patterns.

## Start the local lab

From this directory:

```bash
docker compose up -d
docker compose ps
```

Open <http://127.0.0.1:3000>. The Compose file binds only to loopback and uses an internal Docker network. Do not change the host binding to `0.0.0.0`.

When finished:

```bash
docker compose down
```

If the container does not start, inspect `docker compose ps` and `docker compose logs --tail=50 juice-shop`. Do not substitute a public target.

## Deliverable status

The OWASP analysis and hardening report document a static review of this repository's lab configuration. They do not claim a runtime assessment of Juice Shop. Use the reusable finding template in the report for additional authorized observations, and clearly label untested areas.

## References

- [OWASP Top 10](https://owasp.org/Top10/)
- [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)

## License

Original learning materials are licensed under the MIT License. See [LICENSE](LICENSE). OWASP Juice Shop is a separate project and remains subject to its own license and terms.
