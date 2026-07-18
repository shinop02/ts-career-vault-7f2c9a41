# Tomohiro CV

Static executive career site for GitHub Pages.

## Preview Locally

Use any static file server from this directory:

```bash
python3 -m http.server 8080
```

Then open:

```text
http://localhost:8080/
```

The site is static and does not require a Node server, API server, database, or build step.

## Deploy To GitHub Pages

Target repository:

```text
shinop02/ts-career-vault-7f2c9a41
```

Copy these files to the repository root:

```text
index.html
manifest.json
service-worker.js
apple-touch-icon.png
icon-192.png
icon-512.png
robots.txt
README.md
```

Commit and push to the default branch. In GitHub:

1. Open the repository settings.
2. Go to Pages.
3. Set source to Deploy from a branch.
4. Select the default branch and `/root`.
5. Save.

Expected URL:

```text
https://shinop02.github.io/ts-career-vault-7f2c9a41/
```

All asset paths are relative, so the site works under the GitHub Pages repository path.

## Change Password

The lightweight front-end gate is in `index.html`.

Search for:

```js
const pass = ["tm", "shino"].join("");
```

Change the joined string parts. The username check is:

```js
username === "visitor"
```

## Security Limitation

This is client-side gating only. It is not secure authentication. Anyone with access to the static files can inspect the JavaScript and recover the password. Use server-side authentication or a private hosting layer for real access control.

## Edit Resume Content

Content is stored in the `data` object inside `index.html`.

Sections:

- `ja`: Japanese content
- `en`: English content
- `roles`: professional experience
- `projects`: selected project case studies
- `aiUses`: AI use cases
- `capabilities`: skills and operating capabilities

Do not add new metrics, dates, titles, companies, or achievements unless they are verified against source material.

## Update Icons

Replace:

```text
apple-touch-icon.png
icon-192.png
icon-512.png
```

Keep the same filenames unless you also update `manifest.json` and the `<link rel="apple-touch-icon">` in `index.html`.

## iPhone Home Screen

To add to Home Screen:

1. Open the deployed URL in iPhone Safari.
2. Tap Share.
3. Tap Add to Home Screen.
4. Confirm the name `Tomohiro CV`.

The site includes:

- `apple-mobile-web-app-capable`
- `apple-mobile-web-app-status-bar-style`
- `apple-mobile-web-app-title`
- `viewport-fit=cover`
- safe-area CSS handling
- web app manifest

## Apple Passwords / iCloud Keychain

The login form supports Apple Passwords through:

```html
<input name="username" autocomplete="username">
<input name="password" autocomplete="current-password">
```

To save credentials:

1. Open the site in Safari.
2. Enter username and password.
3. Let Safari / Apple Passwords save the credential when prompted.
4. Future visits can use AutoFill where Safari allows it.

## Motion And Accessibility

The site no longer requests device motion or gyroscope permission. Visual motion is handled through lightweight scroll, pointer, and CSS animation effects, and `prefers-reduced-motion` disables expensive motion and animation behavior.
