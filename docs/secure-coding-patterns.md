# Secure coding patterns

Use these patterns when building an application you own. Prefer framework and database APIs over custom security logic.

## Validate input and parameterize queries

Validate type, length, and allowed values at the server boundary. Use a database driver's parameterized query API instead of joining untrusted values into SQL:

```js
const result = await db.query(
  "SELECT id, display_name FROM users WHERE id = $1",
  [userId]
);
```

Keep validation and authorization separate: valid input does not imply the caller is allowed to use it.

## Authorize on the server

For every resource operation, derive the current user from a verified server-side identity and check the requested permission against the resource. Do not accept an owner identity supplied only by the browser. Apply the same rule to reads, edits, deletes, exports, and background operations.

## Render untrusted data safely

Use framework auto-escaping and context-appropriate output encoding. In browser code, prefer text rendering APIs such as `textContent` over parsing untrusted strings as HTML. Avoid bypasses to framework escaping unless there is a reviewed, narrowly scoped need.

## Protect credentials and sessions

- Store passwords with a modern password-hashing function and per-password salt; do not store plaintext or reversible password values.
- Keep secrets out of source control, logs, URLs, and client-side bundles.
- Use appropriately configured session cookies (`HttpOnly`, `Secure` over HTTPS, and a considered `SameSite` policy).
- Rotate or invalidate sessions at authentication boundaries and on logout.
- Add CSRF defenses for state-changing cookie-authenticated requests.

## Fail safely and log carefully

Return useful but non-sensitive error messages to clients. Keep stack traces and secrets in protected server-side diagnostics, if needed. Log security-relevant events with enough context for response while excluding passwords, session identifiers, tokens, and unnecessary personal data.

## Regression tests

Write tests for expected controls: unauthenticated requests are rejected, users cannot read or modify another user's resource, malformed input is rejected, and error responses do not disclose secrets. Keep test data synthetic and test services isolated.
