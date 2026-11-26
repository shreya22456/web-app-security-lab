# HTTP, cookies, sessions, and access control

## HTTP request/response lifecycle

An HTTP client sends a request to a server. A request commonly contains a method, path, headers, and sometimes a body. The server routes it, applies validation and authorization, performs the requested operation, and returns a response with a status code, headers, and optionally a body.

```text
Browser → request → web server / application → response → Browser
```

Common methods include `GET` for reading and `POST` for submitting data. Status codes communicate the broad result: `2xx` success, `3xx` redirection, `4xx` client or authorization issue, and `5xx` server error. HTTPS protects data in transit between the client and server; it does not by itself prove a user is allowed to access a resource.

During the lab, inspect only requests to `127.0.0.1:3000`. In browser developer tools or a local proxy, note the method, path, status, and relevant security headers. Redact query values and request bodies before saving notes.

## Cookies and sessions

HTTP is stateless: each request is independent unless the application associates it with state. A common pattern is:

1. The server authenticates a user and creates server-side session state.
2. The browser receives a session identifier in a cookie.
3. The browser sends that cookie on later requests to the matching site.
4. The server validates the session and applies authorization for each requested action.

A cookie is a bearer credential: anyone who obtains a valid session cookie may be able to act as its owner. Never copy session values into reports, screenshots, source control, or chat.

Important cookie attributes:

- `HttpOnly` prevents ordinary page scripts from reading the cookie.
- `Secure` restricts transmission to HTTPS.
- `SameSite` helps reduce cross-site request risks; choose a value compatible with the application flow.
- A narrow `Path` and appropriate lifetime reduce exposure.

These settings are defense in depth, not a substitute for authorization or CSRF protections.

## Authentication vs. authorization

- **Authentication** answers: “Who is this user?” Examples include verifying an identity and establishing a session.
- **Authorization** answers: “May this authenticated user perform this action on this resource?” It must be checked server-side on every relevant request.

Never rely only on a hidden button, client-side route, or identifier being difficult to guess. A safe design checks the authenticated principal, requested action, and resource ownership or permission at the server boundary.

## Lab checkpoint

Using only the local target:

1. Open browser developer tools and visit the home page.
2. Identify one `GET` request and one response status.
3. Locate cookie names and flags in the browser storage view, but do not copy cookie values.
4. In your worksheet, explain the difference between session authentication and server-side authorization.
5. Close developer tools and avoid saving a HAR or browser profile.
