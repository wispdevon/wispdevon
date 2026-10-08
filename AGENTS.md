# Devon Labs Agent Template

Use this as the default `AGENTS.md` for new projects. Project-specific rules may override it, but they should be explicit and narrow.

## Working Style

- Read the relevant code, docs, and existing patterns before changing behavior.
- Keep edits scoped to the requested feature or bug.
- Prefer the project's existing architecture over introducing a new abstraction.
- Do not revert unrelated user changes in a dirty worktree.
- Prefer `rg` for searching and `apply_patch` for manual edits.
- Use structured parsers or framework APIs instead of ad hoc string manipulation when practical.
- Commit coherent checkpoints after stable implementation work when the user has asked for commits or the project expects them.

## Project Discovery

At the start of a new task, inspect the files that define the project:

- `AGENTS.md`
- `DESIGN.md`
- `README.md`
- `package.json`, lockfiles, config files, and framework docs in the repo
- Route, schema, auth, storage, and integration modules related to the task

Follow the nearest `AGENTS.md` in the directory tree. If project instructions conflict with this template, the project-local instructions win.

## Runtime And Environment

- Detect the package manager from the lockfile.
- Use the runtime version declared by `.nvmrc`, `.node-version`, Dockerfile, or docs.
- For TypeScript/React/Next projects, Node 22 is the preferred default when no stronger local rule exists.
- Do not commit `.env`, credentials, tokens, generated databases, or local runtime artifacts.
- For frontend work, start or reuse a local dev server and report the URL when useful.
- If a port is already in use, inspect before killing anything; use another port when possible.

## Git Rules

- Never run destructive commands such as `git reset --hard` or `git checkout --` unless explicitly requested.
- Do not stage unrelated files.
- Review `git status --short` before committing.
- Use concise Conventional Commit-style subjects when no project-specific style exists, for example `feat: add import flow` or `fix: preserve editor route`.
- Larger commits may include a short bullet body that names concrete changes.

## UI Rules

- Follow `DESIGN.md` before inventing visual treatments.
- Build the usable workflow first, not a marketing landing page, unless the request is explicitly for marketing.
- Keep controls ordered according to the way the user performs the task.
- Avoid nested cards, decorative gradient blobs, excessive pills, and one-note palettes.
- Use icons for familiar tool commands and provide accessible names.
- Ensure text does not clip, overlap, or resize containers unexpectedly.
- Verify responsive behavior for the smallest practical mobile size and a desktop viewport.
- For export or preview tools, the output must match what the user sees.

## Auth And Privacy

- Keep authentication trust boundaries clear: browser-only ceremony helpers stay in the client, verification and session creation stay on the server.
- Passkey projects should not add email or name prompts unless the product explicitly needs identity metadata.
- Production auth redirects must use configured public origins, not localhost.
- Session checks on page load must not automatically start a passkey ceremony.
- Store secrets server-side only, or browser-encrypted when the user owns the credential material.
- Do not log API keys, cookies, passkey assertions, decrypted payloads, access tokens, or personal data beyond what is needed for debugging.
- Prefer opaque server sessions with secure, HttpOnly cookies for web apps.

## Data And Integrations

- Keep schema changes in the project's canonical schema files.
- Do not modify databases directly when the project has migrations or schema tooling.
- Update docs when schema, API, or integration behavior changes.
- External service credentials should be scoped, revocable, and never persisted server-decryptable unless that is an explicit product requirement.
- Integration proxies should pass user credentials transiently and avoid logging request payloads that may contain secrets.

## Validation

Run the smallest meaningful validation for the change, then broaden when risk increases.

- TypeScript changes: run typecheck.
- Frontend or API changes: run build when practical.
- UI behavior: use the in-app browser tool or Playwright against the local server.
- Database changes: run the project's schema or migration validation command.
- Tests: run focused tests first, then relevant suites.

If a validation command is known broken or cannot run in the environment, state that clearly in the final response and include the reason.

## Handoff

Final responses should be concise and concrete:

- Name the files changed.
- Summarize the behavior or document change.
- Report validation performed or not performed.
- Mention any follow-up risk that matters.

Do not tell the user to copy files that already exist in the shared workspace.
