# NoMarky

Hide YouTube sidebar recommendations from creators you choose to block.
An optional auto-jump tries to leave a blocked creator's video for the first
non-blocked recommendation in the sidebar.

A [Devon Labs](https://devonlabs.space) project by [Wisp](https://github.com/wispdevon).

[Load in Chrome](#load-in-chrome-or-chromium) · [Try in Firefox](#load-temporarily-in-firefox) · [Report an issue](https://github.com/wispdevon/NoMarky/issues)

## Features and limits

- Toggle sidebar blocking and auto-jump from the extension popup.
- Edit the creator list on the options page.
- Creator matching ignores case and accents.
- Runs on `youtube.com` using a Manifest V3 content script and storage permission.

This filters sidebar recommendations, not every YouTube surface. Auto-jump
depends on a suitable sidebar recommendation and can fail when YouTube changes
its page structure. It is not a general content-safety filter.

**Availability:** local installation instructions and Firefox packaging scripts
are included. This README does not claim publication in a browser store.
**Built with:** JavaScript and WebExtensions / Manifest V3.

## Load in Chrome or Chromium

```bash
git clone https://github.com/wispdevon/NoMarky.git
cd NoMarky
```

1. Open `chrome://extensions`.
2. Enable **Developer mode** and select **Load unpacked**.
3. Choose the cloned `NoMarky` folder containing `manifest.json`.
4. Open YouTube and use the extension popup to enable blocking or auto-jump.

## Load temporarily in Firefox

Use Firefox 126 or later, as declared in the manifest.

1. Clone the repository if you have not already done so.
2. Open `about:debugging#/runtime/this-firefox`.
3. Select **Load Temporary Add-on**, then the checkout's `manifest.json`.
4. Use the options page to change the creator list.

Temporary add-ons must be loaded again after restarting Firefox.

## Default blocked creators

The default list targets Markiplier-related channels:

- `markiplier`
- `markipliergame`
- `markiplier highlights`
- `markiplier twitch`
- `markiplier en espanol`
- `markiplier en español`
- `unus annus`

Edit the list for your own preferences. This is an independent extension,
not affiliated with YouTube or the listed creators.

## Package for Firefox Add-ons

```bash
npm install
npm run lint:firefox
npm run build:firefox
```

The uploadable package is created in `web-ext-artifacts/`. Creating this archive
does not publish it to Firefox Add-ons.

## Contributing

Creator preferences use the browser's extension `storage.sync` API and may sync
with your browser account, depending on its configuration.

Report the browser/version, affected YouTube surface, and a reproducible example
through [Issues](https://github.com/wispdevon/NoMarky/issues). For changes, run the
Firefox lint/build scripts and manually check blocking, auto-jump, and the options
page in both browsers. Do not include personal browsing-history exports.

## License

No license file is present in the repository. Public source availability alone
does not grant an open-source license.

A [Devon Labs](https://devonlabs.space) project by [Wisp](https://github.com/wispdevon).
