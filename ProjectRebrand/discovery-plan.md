# ProjectRebrand discovery plan

Prepared 2026-10-09 for `wispdevon`. All settings and promotion text below are
**proposals**; none have been applied or posted.

## Positioning and profile

**Identity:** Wisp, independent developer based in Thailand, building under
Devon Labs. Lead with photography tools and self-hosted workspaces, followed by
desktop/browser utilities. Give users a path to try the project and give clients
evidence through source, technical choices, and clearly stated constraints.

**Exact proposed bio:**

> Building photography tools, self-hosted workspaces, and desktop utilities at Devon Labs. Independent developer in Thailand.

**Display name:** retain `Wisp`. **Website:** `https://devonlabs.space`.
That URL currently serves **The Depot**, a photography portfolio with contact
navigation. The profile draft describes it as a photography portfolio rather
than claiming it is already a software catalog.

**Recommended pin order:**

1. `GibbonPfp` — display HeadshotFlow; downloadable native application and CLI.
2. `immich-contact` — clear visual result and reachable hosted app.
3. `Immichinko` — recent Immich companion with Docker and screenshot evidence.
4. `quester` — photo composition and browser-encrypted integration work.
5. `strider` — collaborative workflow, SQLite, and passkey authentication.
6. `sharplysearch` — focused Linux utility and independent API integration.

GitHub supports up to six pinned repositories/gists, and topics help users find
projects by purpose, community, and technology. These are discovery surfaces,
not promises of ranking or traffic. See [profile documentation](https://docs.github.com/en/account-and-profile/concepts/contributions-on-your-profile)
and [topic documentation](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/classifying-your-repository-with-topics).

## Exact repository metadata proposals

Use the descriptions verbatim. Topics are lowercase, relevant to implemented
behavior, and below GitHub's limit of 20. Homepage proposals link to the actual
hosted product where verified; otherwise they use the repository's existing
release or README page. An empty homepage means leave it blank.

| Repository | Proposed description | Proposed homepage |
| --- | --- | --- |
| `GibbonPfp` | HeadshotFlow: offline portrait editor and CLI for face-aware crops, RAW development, local background removal, and batch export. A Devon Labs project. | https://github.com/wispdevon/GibbonPfp/releases/latest |
| `immich-contact` | Turn Immich albums into previewable contact sheets with classic grids, full-frame layouts, and film strips. Self-hosted, with JPEG/PNG export. By Devon Labs. | https://sheets.devonlabs.space/ |
| `Immichinko` | Rediscover your Immich library ten photos a day. Favorite, Pass, or Later with durable sessions, local cooldowns, and Docker deployment. By Devon Labs. | https://github.com/wispdevon/Immichinko#readme |
| `quester` | A personal photo quest workspace with full-frame layouts, composition controls, Immich integration, and browser-encrypted storage. A Devon Labs project. | https://quest.devonlabs.space |
| `strider` | Collaborative Kanban with passkeys, board invites, assignments, subtasks, and a Hall of Fame for completed work. Next.js and SQLite. By Devon Labs. | https://github.com/wispdevon/strider#readme |
| `sharplysearch` | Find cameras and lenses from Wayland with Wofi, fuzzy search, live Sharply API specifications, and clipboard copying. Independent launcher by Devon Labs. | https://github.com/wispdevon/sharplysearch#readme |
| `NoMarky` | A Firefox and Chromium extension to hide YouTube sidebar recommendations from selected creators and optionally jump away from blocked videos. By Devon Labs. | https://github.com/wispdevon/NoMarky#readme |
| `wifiqr` | A macOS shell utility that displays the current WPA Wi-Fi network as a terminal QR code using Keychain and qrencode. A Devon Labs project. | https://github.com/wispdevon/wifiqr#readme |
| `ASCII-ART` | Experimental C# and Magick.NET renderer for randomized ASCII dragon artwork with element colors and loot images. A Devon Labs experiment. | Leave blank |
| `schoolcrm` | Placeholder for a Devon Labs school CRM project. No application implementation or installation workflow yet. | Leave blank |
| `wispdevon` | Wisp / Devon Labs: photography tools, self-hosted workspaces, and focused desktop and browser utilities. | https://devonlabs.space |

| Repository | Exact proposed topics |
| --- | --- |
| `GibbonPfp` | `photography`, `portrait`, `image-processing`, `background-removal`, `qt`, `qml`, `cpp`, `offline`, `batch-processing` |
| `immich-contact` | `immich`, `photography`, `contact-sheet`, `self-hosted`, `image-processing`, `docker`, `typescript`, `sharp` |
| `Immichinko` | `immich`, `photography`, `photo-library`, `self-hosted`, `sveltekit`, `sqlite`, `docker`, `typescript` |
| `quester` | `photography`, `photo-collage`, `immich`, `nextjs`, `typescript`, `webcrypto`, `sqlite`, `oidc` |
| `strider` | `kanban`, `project-management`, `self-hosted`, `passkeys`, `webauthn`, `nextjs`, `sqlite`, `typescript` |
| `sharplysearch` | `photography`, `wayland`, `wofi`, `hyprland`, `bash`, `camera`, `fuzzy-search` |
| `NoMarky` | `youtube`, `browser-extension`, `firefox`, `chromium`, `webextensions`, `javascript`, `manifest-v3` |
| `wifiqr` | `macos`, `wifi`, `qr-code`, `bash`, `command-line`, `keychain` |
| `ASCII-ART` | `ascii-art`, `csharp`, `magick-net`, `generative-art`, `experimental` |
| `schoolcrm` | `prototype`, `devon-labs` |
| `wispdevon` | `github-profile`, `portfolio`, `photography`, `self-hosted`, `devon-labs` |

The `schoolcrm` tags identify its placeholder status; do not add feature-oriented
education/CRM tags until there is an implementation worth discovering.

## Priorities and ready-to-edit promotion copy

**First:** publish the reviewed profile and project README changes, then apply
the proposed descriptions/topics/pins. Pair descriptions with the README so the
repository listing and product name agree. No renames or organization transfers
are needed.

**Next:** share one concrete workflow at a time. Use existing screenshots or a
short demonstration with nonprivate images. Check each community's current
submission rules before posting; no accounts have been contacted in this task.

| Project | First audience/channel | Draft announcement |
| --- | --- | --- |
| HeadshotFlow | Photography workflows and Linux desktop communities | I built HeadshotFlow at Devon Labs to prepare consistent portraits offline: face-aware crops, RAW development, local background removal, and batch export. Originals stay untouched. Published packages are available for Linux, Windows, and macOS; platform/signing notes are in the README. Try the built-in sample: https://github.com/wispdevon/GibbonPfp/releases/latest |
| Immich Contact Sheet | Immich community showcases and self-hosting communities | Want to see an Immich album as a contact sheet? My Devon Labs companion previews classic grids, full-frame layouts, and film strips before JPEG/PNG export. You can self-host it or use the hosted app with a reachable Immich server and a dedicated read-only key. Visitor keys are encrypted in the browser and sent transiently to the proxy for requests: https://github.com/wispdevon/immich-contact |
| Immichinko | Immich users interested in rediscovering large libraries | Immichinko is my Devon Labs experiment in a small photo habit: review ten photos a day, Favorite back to Immich, Pass, or Later. Docker setup and an optional sidebar integration are documented. It is intended for one account behind private-network/proxy authentication; live Favorite/Undo validation remains a documented limitation: https://github.com/wispdevon/Immichinko |
| Quester | Photography challenges and composition communities | Quester is a Devon Labs workspace for photo prompts and full-frame compositions. Arrange up to five images, style the result, and use uploads or an Immich connection. It uses the Devon Labs passkey authority. The hosted page currently offers Start Editor when no quest is scheduled: https://quest.devonlabs.space |
| Strider | Self-hosted productivity users and technical portfolio readers | Strider is my Devon Labs Kanban workspace: Plan, Active, Review, assignments, subtasks, and a Hall of Fame for completed work. It uses Next.js, SQLite, and passkeys. The README includes local setup and the deployment requirements, including securing the seeded board: https://github.com/wispdevon/strider |
| Sharply Search | Wayland/Hyprland users and photography gear communities | I built an independent Wayland launcher that puts Sharply Photo's camera and lens catalog in Wofi. Search cached gear, open live specifications, and copy details with the keyboard. It needs a Sharply developer key and is not an official Sharply app. Installation and screenshots: https://github.com/wispdevon/sharplysearch |

**Secondary:** present NoMarky to browser-extension users only after cross-browser
checks; describe its sidebar-only scope and local installation. WifiQR needs
current macOS validation and payload escaping before a broad launch. ASCII-ART
needs reproducible build/runtime instructions and asset licensing; schoolcrm
needs an implementation. These projects remain documented without occupying
the flagship pins.

**Licensing:** Quester, NoMarky, WifiQR, and ASCII-ART have no license file in
their public default branches. Retain that fact in their READMEs; the maintainer
must choose a license before calling them open-source projects with reuse rights.
This draft does not select or add licenses.

**Brand follow-up:** give Devon Labs an explicit software-project index on its
website, or connect a clearly labeled software section to The Depot. The current
site is a photography portfolio. Website changes are outside this deliverable.
For flagship repository social previews, use product name, one workflow, and
existing UI imagery with the quiet paper/graphite design language. A future
GitHub upload should be a PNG/JPG/GIF under 1 MB, ideally 1280 × 640 according to
[GitHub's social preview guidance](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/customizing-your-repositorys-social-media-preview).
No new preview asset has been generated or uploaded here. HeadshotFlow's existing
workspace screenshot still displays GibbonPfp; the draft labels that fact.
Capture an updated native screenshot before using it in a rebrand launch image.

## Measuring discovery

Baseline on 2026-10-09: all 21 owned repositories have no topics, the profile has
no bio and no pinned items, and several public originals have no descriptions.
Of the ten public original project repositories, Sharply Search has two stars;
the other nine have zero. The profile repository is a separate eleventh original.
This inventory excludes four private repositories and six forks from the draft set.

When publishing, record GitHub traffic views, unique visitors, clones, stars,
and meaningful issues/contributions. Check again after two and four weeks;
GitHub traffic is a short rolling window, so save the available baseline when
publishing. Evaluate hosted-product visits and completed workflows separately
where existing analytics are available. No analytics infrastructure or tracking
has been added, and no traffic uplift is claimed.
