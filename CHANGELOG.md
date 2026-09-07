# Changelog

## v5.12.0 - In-development

### New Features

- `ctx.chat.getChat(jid)`: look up any other chat (group or DM) by JID, returning a new `ChatContext` with the same shape (itself `getChat()`-able). Useful for groups discovered via `ctx.chats.all()` or stored earlier by a plugin.
- `ctx.chat.getMsg(msgId)`: look up any message by ID alone, the owning chat's JID is resolved automatically via a new `msgId -> jid` store index, so `.reply()`/`.react()` work on an old/stored message ID.

### Fixed

- Pairing code instructions now show the correct full path.

### Refactors

- Fixed config/`commands.yaml` reload debounce timers (`configReloadTimeout` / `yamlReloadTimeout`) not being cleared on `cleanupPlugins()`, which could leave a dangling timer after shutdown.

### Build / CI

- Added `prepare` npm script (`scripts/install-local-hooks.sh`) that points the clone's git hooks at `scripts/local-hooks/` on `npm install`.
- New local `pre-commit` hook: auto-bumps `packages/types/package.json` minor version when staged changes touch the published `@manybot/types` definitions (`packages/types/{en,pt}`).
- Renamed `hooks/` to `scripts/git-hooks/` (server-side release infra, no contributor impact).

