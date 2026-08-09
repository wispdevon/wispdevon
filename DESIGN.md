# Devon Labs Project Design Template

This is the starting design system for new Wisp Devon / Devon Labs projects. It is adapted from Strider's visual language and generalized so each new product can inherit a calm, practical foundation without copying Strider screen-for-screen.

Use this as a checklist before inventing new UI rules. If a project needs a different mood, document the difference explicitly in that project's own `DESIGN.md`.

## Design Character

The default product character is a quiet operational workspace with an editorial finish.

- Warm paper in light mode and graphite in dark mode.
- A faint dot grid or similarly subtle working-surface texture.
- Soft opaque panels over restrained translucent headers or toolbars.
- Dark titanium emphasis instead of a bright brand color.
- Optional personal accent derived from the signed-in user or workspace.
- Compact controls, stable dimensions, and restrained motion.
- Display typography for identity and hierarchy; neutral sans text for work.

The interface should feel precise and tactile, but not decorative for its own sake. Content and actions carry the composition. Avoid large marketing heroes, nested cards, glowing gradients, excessive pills, oversized rounding, one-color themes, and decorative backgrounds that compete with the task.

## Product Frame

Build the actual usable product as the first screen unless the project is explicitly a marketing site. A user should immediately understand what can be done, what state the system is in, and where to go next.

- Operational tools should be dense, scannable, and work-focused.
- Creative tools can be more expressive, but the main artifact should still be inspectable.
- Photography tools should respect the image: avoid unnecessary cropping, dark overlays, and stock-like presentation when the user needs to judge the actual photo.
- Self-hosted tools should make data ownership and integration boundaries understandable without turning the UI into documentation.

## Foundation

### Typography

Recommended defaults:

| Role | Font | Use |
| --- | --- | --- |
| Body | Inter | UI text, controls, paragraphs |
| Display | Space Grotesk | Product name, page titles, section headings |
| Code | Geist Mono | Codes, identifiers, technical values |

Body text should use a system-compatible sans stack and `line-height: 1.5` to `1.6`. Display headings can be tighter, but do not scale font sizes continuously with viewport width. Letter spacing should normally be `0`; use positive tracking only for short uppercase metadata labels.

### Color Tokens

Use semantic tokens first. Do not scatter raw colors through components.

```css
:root {
  color-scheme: light;
  --background: #efece6;
  --foreground: #17181b;
  --panel: #f8f6f2;
  --panel-strong: #e7e0d5;
  --border: rgba(23, 24, 27, 0.12);
  --muted: #6e7379;
  --accent: #1d1f23;
  --accent-soft: #ece7de;
  --accent-sheen: #b8b4ab;
  --accent-glow: rgba(29, 31, 35, 0.08);
  --profile-accent: #4b5563;
  --header-surface: rgba(248, 246, 242, 0.9);
  --lane-surface: rgba(248, 246, 242, 0.75);
  --inset-highlight: rgba(255, 255, 255, 0.8);
}

[data-theme="dark"] {
  color-scheme: dark;
  --background: #151617;
  --foreground: #f2f0ea;
  --panel: #202224;
  --panel-strong: #2a2d30;
  --border: rgba(242, 240, 234, 0.13);
  --muted: #a6abb0;
  --accent: var(--profile-accent);
  --accent-soft: color-mix(in srgb, var(--profile-accent) 20%, #202224);
  --accent-sheen: color-mix(in srgb, var(--profile-accent) 52%, white);
  --accent-glow: color-mix(in srgb, var(--profile-accent) 22%, transparent);
  --header-surface: rgba(32, 34, 36, 0.9);
  --lane-surface: rgba(32, 34, 36, 0.72);
  --inset-highlight: rgba(255, 255, 255, 0.06);
}
```

Reserve red, green, and yellow for destructive/error, success, and warning states. Keep their area small. Do not let semantic colors become page themes.

### Canvas

Use a continuous page canvas. If a texture is used, apply it once at the page level and keep it subtle:

```css
body {
  background-color: var(--background);
  background-image:
    radial-gradient(circle, rgba(23, 24, 27, 0.09) 1.2px, transparent 1.2px),
    linear-gradient(180deg, rgba(255, 255, 255, 0.24), rgba(255, 255, 255, 0.02));
  background-size: 18px 18px, cover;
  background-position: center;
}
```

Do not apply the texture independently to every card, footer, modal, or toolbar.

## Layout

- Use a maximum content width near `1280px` for standard pages.
- Dense work surfaces may use the full viewport width.
- Page sections are unframed and full width.
- Cards are for repeated items, modals, menus, and genuinely framed tools.
- Do not put UI cards inside other cards.
- Let desktop layouts breathe horizontally when the workflow benefits from side-by-side tools.
- Stack on mobile only when the viewport needs it.
- Give fixed-format elements explicit dimensions, aspect ratios, grid tracks, or min/max constraints.
- Text, counters, hover states, and loading labels must not resize their containers.
- No foreground panel should cover the primary work area because a canvas or export preview expanded unexpectedly.

For app workflows, prefer a clear left-to-right or top-to-bottom progression. Controls should appear in the order users naturally apply them.

## Component Grammar

### Surfaces

- Work lanes and tool regions use `lane-surface`, a 1px border, and a subtle inset highlight.
- Repeated cards use `panel`, a 1px border, and a low neutral shadow.
- Inputs use `panel` or `panel-strong`.
- Menus and dialogs use `panel`, stronger shadow, and an explicit backdrop.

Reference elevation:

```css
/* sticky header */ box-shadow: 0 8px 24px rgba(17, 17, 17, 0.04);
/* ordinary card */ box-shadow: 0 10px 30px rgba(17, 17, 17, 0.05);
/* hovered card */ box-shadow: 0 14px 36px rgba(17, 17, 17, 0.08);
/* floating menu */ box-shadow: 0 12px 40px rgba(17, 17, 17, 0.12);
```

### Radius

Use a restrained radius scale:

| Element | Radius |
| --- | --- |
| Inputs, icon buttons, command buttons | `8px` |
| Cards and floating menus | `12px` |
| Large dialogs and broad lanes | `16px` |
| Tags and avatars | Fully round only when semantically appropriate |

Avoid making every control pill-shaped. Pills are for compact statuses, avatars, and binary labels.

### Controls

- Toolbar controls should keep a stable `40px` minimum hit target.
- Prominent form rows should be around `44px` high.
- Use familiar icons for icon-only commands and include `aria-label` plus `title`.
- Use segmented controls for modes, sliders or numeric inputs for numeric values, swatches for colors, menus for option sets, toggles for true binary settings, and text buttons for clear commands.
- Disabled controls should preserve layout, reduce opacity, and prevent duplicate submission.
- Focus should use an accent border plus a visible ring; do not rely on color alone.

## Motion

Motion confirms interaction; it does not decorate idle screens.

Recommended defaults:

| Interaction | Motion |
| --- | --- |
| Toolbar hover/tap | scale `1.05` / `0.95` |
| Primary button tap | scale `0.98` |
| Card hover | scale `1.01` to `1.02`, only where layout permits |
| Popover enter | opacity and small Y transition over `150ms` |
| Dialog enter | backdrop fade, panel scale and Y transition |
| Routine color/shadow | `200ms` to `300ms` ease |

Always add a reduced-motion path. Preserve immediate state feedback under `prefers-reduced-motion: reduce`.

## Media And Artifacts

- Use real or generated bitmap images when the user needs a visual subject.
- Avoid generic stock-like imagery when the product, place, person, or photo itself matters.
- Do not hide important media behind dark, blurred, or overly cropped presentation.
- For export tools, the exported artifact must match the visible preview.
- Shadows, borders, spacing, masks, and shapes should be part of the same composition model in preview and export.

## Social Preview Embeds

Every public web app should ship a Discord/Open Graph preview instead of relying on crawler defaults.

- Define a canonical public URL such as `SITE_URL` and use it as the metadata base.
- Add `openGraph` and `twitter` metadata at the root layout level for app-wide previews.
- Use `summary_large_image` for Twitter-compatible consumers.
- Provide a `1200x630` preview image in `public/`, preferably SVG or a generated bitmap that follows this design system.
- The preview should show the product name, a concrete offer or workflow, and a truthful representation of the main surface.
- Avoid tiny screenshots, dark blurred stock images, and copy-heavy cards.
- The preview image should be absolute-resolvable through metadata; crawlers such as Discord must not see a localhost URL in production.
- Keep the preview accessible with a meaningful image `alt` value in metadata and `title`/`desc` if the asset is SVG.

## States And Accessibility

Every feature-complete screen needs loading, empty, error, disabled, active, hover, focus, and success states where applicable.

- Meet WCAG AA contrast for body text, muted text, focus indicators, and text on accents.
- Keep pointer targets at least `40px` square for toolbar actions.
- Trap focus inside modal dialogs and restore focus on close.
- Close menus and dialogs on Escape.
- Do not communicate completion, warning, stage, or assignment through color alone.
- Avoid essential information that appears only on hover.
- Expose drag-and-drop alternatives where the feature is important.

## Implementation Order

1. Define tokens, fonts, theme bootstrap, and canvas.
2. Build shared button, input, menu, modal, panel, and typography primitives.
3. Compose the primary workflow using stable layout constraints.
4. Add personalized accent or workspace branding only after the neutral system works.
5. Add restrained motion and reduced-motion fallbacks.
6. Implement loading, empty, error, focus, and disabled states.
7. Verify with browser screenshots at desktop and mobile sizes.

The design is successful when it still works with the accent removed: readable, calm, tactile, and focused on the thing the user came to do.
