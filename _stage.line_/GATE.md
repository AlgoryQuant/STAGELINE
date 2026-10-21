# Temporary site gate („Připravujeme“)

While the gate is active, visitors only see the coming-soon page at `/`. Deep links (`/akce`, `/kms-night`, `/home`, old `.html` paths, etc.) redirect to `/` via `vercel.json`.

**Nothing was deleted.** Full site content is preserved as `home.html` (and `akce.html`, `kms-night.html`, assets, styles).

## Reopen the full site

1. Copy `home.html` over `index.html` (restore the real homepage).
2. In `vercel.json`, remove the gate redirects and restore clean-URL rewrites, e.g.:

```json
{
  "redirects": [
    { "source": "/index.html", "destination": "/", "permanent": true },
    { "source": "/akce.html", "destination": "/akce", "permanent": true },
    { "source": "/kms-night.html", "destination": "/kms-night", "permanent": true }
  ],
  "rewrites": [
    { "source": "/akce", "destination": "/akce.html" },
    { "source": "/kms-night", "destination": "/kms-night.html" }
  ]
}
```

3. Optionally delete this `GATE.md` when you no longer need the note.
