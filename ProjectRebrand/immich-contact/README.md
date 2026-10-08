<a id="readme-top"></a>

# Immich Contact Sheet

Turn an Immich album into a contact sheet you can preview and download.
Choose a compact grid, preserve each photograph's full frame, or compose a
film-strip layout, then export JPEG or PNG.

A [Devon Labs](https://devonlabs.space) project by [Wisp](https://github.com/wispdevon).

[Open the hosted app](https://sheets.devonlabs.space/) · [Self-host with Docker](#docker) · [Report an issue](https://github.com/wispdevon/immich-contact/issues)

## Try it

Open the hosted app with your own Immich server connection and a dedicated
read-only API key. The app's server must be able to reach your Immich server;
private-network installations should use the self-hosted setup below.
Saved visitor keys are encrypted in the browser, but are sent transiently to
the app's server to proxy Immich requests. See [Privacy](#privacy) before
connecting a library.

![Immich Contact Sheet album and composition controls](docs/images/configuration.png)

## About the project

Immich Contact Sheet is a focused, self-hosted companion for [Immich](https://immich.app). It reads albums and thumbnails through a least-privilege API key, lays the selected images onto a configurable sheet, and lets you inspect the finished result before downloading it as JPEG or PNG.

It is intentionally separate from the Immich server. Album dates, covers, and metadata come from Immich; composition happens in memory. A deployment can use one operator-configured server, or let visitors save encrypted connection profiles in their own browser.

Features include:

- Albums sorted by newest image date, with cover thumbnails.
- Balanced automatic grids or fixed row and column counts.
- Default, true-to-ratio, and filmic composition methods.
- Full-color and black-and-white rendering.
- Warm white, middle gray, and black canvases.
- Optional transparent 135 with continuous perforated row strips, 135 without perfs, or 120 film-stock styles with dated edge markings.
- Adjustable output resolution with JPEG and PNG export.
- In-page preview before download.
- Metadata fallback warnings for incomplete Immich assets.
- Structured request and error logs with request IDs.
- Multiple browser-persistent Immich profiles with server URL, account identity, and profile image.
- AES-GCM encrypted API keys with optional passkey-protected unlock.
- Local hot reload and production Docker deployment.

### Standard contact sheet

The default style produces a compact, evenly cropped grid with the selected canvas and export settings.

![Standard generated contact sheet preview](docs/images/standard-contact-sheet-preview.png)

### Filmic contact sheet

Filmic composition can be combined with continuous perforated film stock, black-and-white rendering, transparent PNG output, and dated edge markings.

![Filmic generated contact sheet preview](docs/images/contact-sheet-preview.png)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Composition methods

- **Default** crops each image to a consistent 4:3 tile. This is the compact behavior used by the original version.
- **True to ratio** fits the complete image inside its tile using Immich dimensions and EXIF orientation, so portrait and landscape photographs are not cropped.
- **Filmic** preserves the full frame and turns portrait photographs sideways, like reading portrait exposures on a strip of film. Upside-down 180° frames are normalized to 0°, and 270° frames are normalized to the same 90° reading direction as other portrait frames.

True-to-ratio and filmic generation report how many assets are missing dimensions or orientation metadata. Filmic mode safely falls back to the rendered thumbnail dimensions to detect portrait frames, while true-to-ratio fitting prevents incomplete metadata from aborting the sheet.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Built with

- [Node.js](https://nodejs.org/)
- [TypeScript](https://www.typescriptlang.org/)
- [Express](https://expressjs.com/)
- [Sharp](https://sharp.pixelplumbing.com/)
- [Zod](https://zod.dev/)
- HTML, CSS, and browser JavaScript

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Getting started

### Prerequisites

- Node.js 20 or newer
- An accessible Immich server
- An Immich API key with `album.read`, `asset.read`, `asset.view`, `user.read`, and `userProfileImage.read` permissions

Create the key from **Immich → Account settings → API Keys**. Use a dedicated read-only key rather than an administrative key.

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/wispdevon/immich-contact.git
   cd immich-contact
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Create the local environment file:

   ```bash
   cp .env.example .env
   ```

4. Set `IMMICH_URL` and `IMMICH_API_KEY` in `.env`, or enable visitor profiles with `ALLOW_USER_CONNECTIONS=true`.

5. Start the hot-reloading development server:

   ```bash
   npm run dev
   ```

6. Open [http://localhost:4001](http://localhost:4001).

Never commit `.env`. Operator credentials remain server-side. Visitor-provided credentials are encrypted in that visitor's browser and sent only to this application's proxy for authenticated Immich requests.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Usage

1. Select an album. Albums are ordered by their newest image date.
2. Choose a composition method and grid layout.
3. Select color mode, canvas, format, and output width.
4. Generate the preview.
5. Review metadata warnings and the completed sheet.
6. Download the existing preview without rendering it again.

### Connection profiles

Select the profile control in the header to add one or more Immich servers. After verifying the URL and API key, the app retrieves the current Immich user's name and profile image and saves the profile in IndexedDB. The API key is encrypted with a non-extractable AES-GCM device key before it is stored.

“Add passkey” uses the strongest mode available. With WebAuthn PRF, it replaces device-key protection with an encryption key derived from the passkey. When a provider such as Bitwarden supplies a valid passkey but no PRF output, the app uses the passkey for user verification while retaining encryption with the browser's non-extractable device key. The passkey does **not** contain the API key. Clearing site data removes the encrypted profile, and this version does not sync the encrypted record between devices.

### Scripts

```bash
npm run dev    # Start the hot-reloading development server
npm run check  # Type-check without emitting files
npm test       # Run layout tests
npm run build  # Build production JavaScript
npm run start  # Start the production server
```

### Environment

See [.env.example](.env.example) for the supported variables.

- `IMMICH_URL`: Immich origin, with or without `/api`.
- `IMMICH_API_KEY`: Read-only key for albums, asset search, and thumbnails.
- `PORT`: Server port; the example uses `4001`.
- `MAX_ASSETS`: Maximum images accepted for one generated sheet.
- `ALLOW_USER_CONNECTIONS`: Allow visitors to submit and locally save their own server URL and API key. Disabled by default.
- `ALLOW_PRIVATE_IMMICH_URLS`: Permit private-network URLs and HTTP for trusted self-hosted deployments. Keep disabled on a public host.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Docker

Build and start the production service:

```bash
docker compose up --build -d
docker compose logs -f contact-sheet
```

Open [http://localhost:4001](http://localhost:4001).

The Compose deployment starts in visitor-profile mode when `IMMICH_URL` and `IMMICH_API_KEY` are unset. Set both variables to also provide a server-default profile. Never set only one of them.

For a reverse proxy running on the Docker host, proxy to `http://127.0.0.1:4001`. To expose the port only on loopback, set `HOST_BIND=127.0.0.1` in `.env` before starting Compose. If the reverse proxy itself runs in Docker, attach it to the same network and proxy to `http://contact-sheet:3000` instead of `localhost:4001`.

If the app is not attached to Immich's Docker network, `IMMICH_URL` must be reachable from inside the container. `localhost` inside one container does not refer to another container or the Docker host.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Project structure

```text
src/                 Express server, Immich client, and sheet generator
public/              Browser interface and static assets
test/                Grid calculation tests
docs/images/         README screenshots
migrations/          Cloudflare D1-compatible future sync schema
Dockerfile           Production container image
compose.yaml         Docker Compose deployment
```

Core files:

- [src/server.ts](src/server.ts): routes, validation, logging, and downloads.
- [src/immich.ts](src/immich.ts): Immich client and v3-compatible asset search.
- [src/sheet.ts](src/sheet.ts): image orientation, fitting, and composition.
- [src/grid.ts](src/grid.ts): automatic and fixed grid calculations.
- [public/app.js](public/app.js): album selection, preview, warnings, and download flow.
- [public/profile-store.js](public/profile-store.js): IndexedDB persistence, encryption, and optional passkey unlock.
- [src/connection.ts](src/connection.ts): per-request connections and public-host URL restrictions.

Immich v3 removed assets from album responses, so this project retrieves album contents through `POST /search/metadata` with EXIF data enabled.

### Cloudflare path

The profile model is prepared for a future Cloudflare deployment: [`wrangler.jsonc`](wrangler.jsonc) declares a D1 binding and [`migrations/0001_connection_profiles.sql`](migrations/0001_connection_profiles.sql) stores only encrypted credential payloads for optional cross-device sync. The current release intentionally keeps profiles local and does not upload them to D1.

The image renderer uses Sharp and Express, so it is suited to Node or a Cloudflare Container rather than a plain Workers runtime. A future Workers/Pages edge layer can serve the UI and D1 profile API while delegating image composition to the container. See [docs/cloudflare.md](docs/cloudflare.md).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Privacy

Contact sheets are composed in memory and returned to the browser. The application does not save generated sheets to disk or a database. Saved profiles remain in browser IndexedDB; API keys are encrypted at rest. Operational logs include request and album identifiers but exclude the Immich API key and image content.

Read the full [Privacy Policy](PRIVACY.md). Deployment operators remain responsible for environment secrets, TLS, network access, infrastructure logs, and their Immich server.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Roadmap

- [x] Automatic and fixed grids
- [x] Color and black-and-white export
- [x] Preview-before-download workflow
- [x] Album dates and cover thumbnails
- [x] True-to-ratio and filmic composition
- [x] Encrypted, browser-persistent connection profiles
- [x] Optional passkey-protected profile unlock
- [ ] Optional encrypted cross-device profile sync through Cloudflare D1
- [ ] Optional filenames and capture dates beneath frames
- [ ] PDF and multi-page sheets
- [ ] Saved presets

See the [open issues](https://github.com/wispdevon/immich-contact/issues) for proposed features and known problems.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Contributing

Contributions are welcome.

1. Fork the repository.
2. Create a feature branch: `git checkout -b feat/your-change`.
3. Run `npm run check`, `npm test`, and `npm run build`.
4. Commit using the project style, for example `feat: add sheet captions`.
5. Push the branch and open a pull request.

Please avoid committing `.env`, API keys, generated contact sheets, or private Immich data.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## License

Distributed under the Apache License 2.0. See [LICENSE](LICENSE) for details.

Built by [Devon Labs](https://devonlabs.space).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

[license-shield]: https://img.shields.io/badge/license-Apache%202.0-2f3136.svg?style=for-the-badge
[license-url]: LICENSE
[typescript-shield]: https://img.shields.io/badge/TypeScript-5-3178c6.svg?style=for-the-badge&logo=typescript&logoColor=white
[typescript-url]: https://www.typescriptlang.org/
[immich-shield]: https://img.shields.io/badge/Immich-companion-4250af.svg?style=for-the-badge
[immich-url]: https://immich.app/
