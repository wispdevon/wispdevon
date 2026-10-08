# Quester

Make something from your photographs with a new quest prompt every two weeks.
Arrange photos without cropping, style the composition, and save completed
quests in a personal workspace.

A [Devon Labs](https://devonlabs.space) project by [Wisp](https://github.com/wispdevon).

[Open Quester](https://quest.devonlabs.space) · [Development setup](#development) · [Report an issue](https://github.com/wispdevon/quester/issues)

## Try it

Open the hosted workspace. Sign-in uses the Devon Labs passkey authority at
`auth.devonlabs.space`. When a quest is scheduled, choose it, then move through
template, styling, photos, and export. Use uploads or connect an Immich library.
If no quest is active, the hosted interface offers **Start Editor**.

For a local installation, configure an OIDC authority and client before testing
authenticated flows. This repository does not include the authority itself.

## Features

- Full-frame photo templates for up to five photographs, including grids and feature rails.
- Spacing, borders, shadows, canvas colors, black-and-white, and duotone controls.
- Immich albums, date-range search, thumbnails, and completed-quest album export.
- Browser-encrypted Immich profiles synced as opaque ciphertext.
- Encrypted browser storage for original-size uploads using IndexedDB and WebCrypto.
- SQLite quest records and OIDC session-backed users.

**Built with:** TypeScript, Next.js, React, SQLite, Sharp, and WebCrypto.

## Development

Use Node 22 or later and npm, as required by `package.json`.

```bash
git clone https://github.com/wispdevon/quester.git
cd quester
npm install
cp .env.example .env.local
```

Set a random `SESSION_SECRET`, and register an OIDC client with your authority.
Set `OIDC_ISSUER`, `OIDC_CLIENT_ID`, `OIDC_CLIENT_SECRET`, and
`OIDC_REDIRECT_URI` to the values for that client. `APP_ORIGIN` and the callback
URL must match your development origin. The example defaults to port 3000.
`SITE_URL` is the canonical public URL used for social metadata.

```bash
npm run dev
```

Open the URL printed by Next.js. The default is `http://localhost:3000`.
The hosted authority requires a registered client; copying the example client
ID and placeholder secret is not sufficient to sign in.

See [.env.example](.env.example) for `DATABASE_PATH`, the optional operator
Immich connection, private-network URL policy, and `ADMIN_PASSKEY_IDS` for
creating and updating quest prompts. Keep environment files out of Git.

## Privacy and deployment

User Immich credentials are encrypted in the browser; the server stores opaque
ciphertext and receives decrypted credentials transiently for proxy requests.
Passkey PRF protection is used where available; the labeled device-encryption
fallback is tied to the same browser. Original uploads use encrypted IndexedDB.
Operators must protect the SQLite database, session secrets, OIDC client secret,
and any operator-configured Immich API key.

Production redirects must use the configured public app origin. Configure an
OIDC client for that origin, use TLS, and back up SQLite. Do not advertise this
as an auth-independent single-container deployment.

## Contributing

Open an [issue](https://github.com/wispdevon/quester/issues) with the problem or
proposal. Follow [AGENTS.md](AGENTS.md) and the existing interface patterns. Check that
exported output matches the editor and that refreshing an editor URL preserves
the editing view. Use nonprivate photos for screenshots.

```bash
npm run typecheck
npm run build
```

The repository's `npm run lint` still invokes `next lint`, which its agent
instructions identify as broken with the current Next.js version.

## License

The repository currently has no license file. No open-source license is implied
by this README; the maintainer must choose one before advertising reuse rights.

A [Devon Labs](https://devonlabs.space) project by [Wisp](https://github.com/wispdevon).
