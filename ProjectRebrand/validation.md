# ProjectRebrand validation

Checked on **2026-10-09**. These are local documentation drafts, not applied
GitHub settings or tested application releases.

## Source and claims review

Read all ten public original project README files where present, the public
default-branch file inventories, license metadata, relevant manifests/configs,
and available project agent instructions. Compared the local profile revision
against its initial uncommitted content and the remote profile.

| Project | Evidence and draft treatment |
| --- | --- |
| [HeadshotFlow](https://github.com/wispdevon/GibbonPfp) | README, AGENTS.md, public file tree, and v1.0.1 release assets. Retained compatibility, source build commands, distribution/signing notes, models, privacy, and third-party attribution. Existing screenshot still displays GibbonPfp; labeled accordingly. |
| [Immich Contact Sheet](https://github.com/wispdevon/immich-contact) | README, package scripts, environment example, tree, existing screenshots, and reachable hosted interface. Retained credential proxy/encryption boundaries and Docker/private-network guidance. |
| [Immichinko](https://github.com/wispdevon/Immichinko) | README, package manifest, environment example, tree, and screenshot. Retained no-login deployment limits, Immich permission requirements, write recovery, version compatibility, and unverified live Favorite/Undo status. |
| [Quester](https://github.com/wispdevon/quester) | README, AGENTS.md, package scripts, environment example, config schema, and browser profile-encryption source. Documented external OIDC registration, canonical origin, secret requirements, encryption modes, admin quest IDs, and known lint incompatibility. |
| [Strider](https://github.com/wispdevon/strider) | README, AGENTS.md, package manifest, environment example, and file tree. Retained seeded-board protection, passkey origins, SQLite backups, and native SQLite incompatibility with plain Workers deployment. |
| [Sharply Search](https://github.com/wispdevon/sharplysearch) | README, installer source, file tree, and screenshots. Corrected the contradictory no-local-cache claim and installation checkout path; retained independent-tool attribution and installer/keybinding implications. |
| [NoMarky](https://github.com/wispdevon/NoMarky) | README, package scripts, manifest, content script, and options source. Replaced the absolute local installation path; documented the creator defaults, sidebar-only behavior, sync preference storage, Firefox minimum, and local/package availability. |
| [WifiQR](https://github.com/wispdevon/wifiqr) | README and shell source. Corrected the dependency to qrencode; limited platform claims to macOS, WPA, en0, and historical Big Sur testing. Documented missing QR payload escaping. Homebrew command checked against its official formula. |
| [ASCII-ART](https://github.com/wispdevon/ASCII-ART) | Project file, Program.cs, and public tree. No original README. Described the experimental renderer and .NET 7 / Magick.NET dependency; marked derived build commands unexecuted and Windows-style runtime paths unresolved. |
| [schoolcrm](https://github.com/wispdevon/schoolcrm) | Public tree, original one-line README, and MIT license. Contains no application source; the replacement explicitly describes a placeholder. |

Existing command blocks were retained for HeadshotFlow, Immich Contact Sheet,
and Immichinko. Strider adds clone/checkout commands before its existing install
command. Sharply Search changes only the checkout and example absolute path in
its command blocks. No application code was edited.

## Links and hosted availability

- **206** links/images in the ten project drafts parsed and inspected. Every
  relative file/directory target exists in its intended destination repository.
- All **seven** referenced product screenshots fetched successfully through
  GitHub. Every rendered image has descriptive alternative text.
- The proposed profile bio is **123 characters**. All eleven repository
  descriptions fit GitHub's 350-character limit. Topic lists use lowercase
  letters/numbers/hyphens, each topic is at most 50 characters, and each list
  contains fewer than 20 topics. Six pins are proposed.
- `metadata-proposals.json` matches the description/topic tables in the discovery
  plan. All metadata entries identify drafts and are marked unapplied.

| Public URL | Result and interpretation |
| --- | --- |
| https://devonlabs.space | HTTP 200; title The Depot. Photography portfolio with contact navigation, not currently a Devon Labs software catalog. |
| https://sheets.devonlabs.space/ | HTTP 200; Immich Contact Sheet interface and connection controls. No personal library connection was made. |
| https://quest.devonlabs.space | HTTP 200; Quester interface, no active quest at inspection, Start Editor available. No sign-in or export ceremony was performed. |
| https://auth.devonlabs.space | HTTP 404 at the root. This does not establish an OIDC failure. |
| https://auth.devonlabs.space/.well-known/openid-configuration | HTTP 200; issuer and authorization/token/JWKS endpoints present. OIDC discovery is reachable; a complete login flow was not tested. |
| https://www.sharplyphoto.com/developer | HTTP 429. Retained the existing documented URL; developer registration/API access could not be verified due to rate limiting. |
| https://www.last.fm/user/wisp- | HTTP 200. |
| https://github.com/wispdevon/GibbonPfp/releases/latest | GitHub release API confirms latest published v1.0.1 assets: AppImage, Windows installer/ZIP, Intel/ARM macOS DMGs, and checksums. Packages were not installed or executed. |

External references throughout the retained upstream technical documentation
were not all fetched individually. Relative source/docs links, product images,
release assets, and the key public destinations above were checked.

## Rendered review

Rendered the profile, all ten project drafts, and the discovery plan through
GitHub's Markdown API. Reviewed these **12 documents at 375 × 900 and
1280 × 900**, for **24 viewport checks**, using Playwright and local Chromium.
Checked horizontal page overflow, images/alt text, and same-document anchors.
Screenshots of the profile, HeadshotFlow, and discovery plan were visually
inspected; no clipping or overlap was found.

The in-app browser returned `Browser is not available: iab`; its troubleshooting
guidance was consulted before using the local fallback. Review artifacts were
kept under `/tmp`, separate from the existing `readme_preview.html`.

The local preview used GitHub-rendered content with a GitHub-like reading
stylesheet. Product assets were resolved to the public destination repository,
and heading IDs were generated with github-slugger to model GitHub's page layer.
This verifies the document layout and links, not an exact screenshot of a
published GitHub page or every GitHub theme.

## Limits and handoff

- No app builds, typechecks, native installs, browser-extension runs, or live
  Immich write tests were performed: the deliverable changes Markdown and
  metadata proposals in the profile workspace, with no application code changes.
- Quester, NoMarky, WifiQR, and ASCII-ART have no license file. No license was
  selected or added; their draft READMEs preserve that uncertainty.
- No website rebrand, analytics setup, community posting, metadata changes,
  pin changes, remote commits, pushes, or PRs were performed.
- Existing uncommitted profile work was extended. `readme_preview.html`,
  `Lastfm.svg`, and other project workspaces were left untouched.

Supporting references: [GitHub topics](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/classifying-your-repository-with-topics),
[GitHub social previews](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/customizing-your-repositorys-social-media-preview),
and [Homebrew qrencode](https://formulae.brew.sh/formula/qrencode).
