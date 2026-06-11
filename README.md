# druks-app-setup

Static helper for [GitHub's App manifest flow](https://docs.github.com/en/apps/sharing-github-apps/registering-a-github-app-from-a-manifest),
which only accepts a manifest via form POST — so a plain link can't reach it
directly. druks's `install.sh --apps` prints links into this page instead:

```
https://clawhaven.github.io/druks-app-setup/#org=<org>&manifest=<base64url-json>
```

The page decodes the manifest from the URL fragment and auto-submits it to
`github.com/…/settings/apps/new`. Fragments never leave the browser, so no
server — including this one — sees the manifest. GitHub then shows its own
"Create GitHub App" confirmation; nothing is created until you click it.
