# Personal App Store — Manifest

This repo hosts the JSON manifest for [Matej Store](https://github.com/MatejGroombridge/personal-app-store-frontend), a personal Android app store.

## How it works

The store app periodically polls `docs/manifest.json` (served via GitHub Pages) to discover available apps. It downloads, verifies, and installs APKs based on the entries in that file.

## Manifest structure

Each app entry in `manifest.json` supports the following fields:

```json
{
  "package_name": "com.example.app",
  "display_name": "My App",
  "description": "Short description.",
  "version_code": 1,
  "version_name": "1.0.0",
  "apk_url": "https://...",
  "apk_sha256": "...",
  "apk_size_bytes": 123456,
  "min_sdk": 26,
  "released_at": "2026-01-01T00:00:00Z",
  "changelog": "## v1.0.0 — 2026-01-01\n\nInitial release."
}
```

## Adding an app

1. Build and sign your APK.
2. Upload it to a GitHub release (or any stable public URL).
3. Add an entry to `docs/manifest.json` with the correct SHA-256 hash and metadata.
4. Commit and push — the store will pick it up on its next poll.
