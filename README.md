# @sero-ai/plugin-notes

Note-taking app for Sero — a standard Pi extension with an optional web UI.

## Sero Plugin Install

Install in **Sero → Admin → Plugins** with:

```text
git:https://github.com/monobyte/sero-notes-plugin.git
```

Sero clones the source repo, installs its dependencies locally, builds the UI,
and then hot-loads the plugin into the sidebar.

## Pi CLI Usage

Install as a Pi package:

```bash
pi install git:https://github.com/monobyte/sero-notes-plugin.git
```

The agent gains a `notes` tool (list, add, edit, remove, pin, unpin, show) and
a `/notes` command. State is stored in `.sero/apps/notes/state.json` relative
to the workspace root (or `~/.sero-ui/apps/notes/state.json` inside Sero).

## Sero Usage

When loaded in Sero, the web UI mounts in the main app area and watches
the same state file. Changes from the agent or the UI are reflected
instantly in both directions.

This is a **global-scoped** app — state is per-user, not per-workspace.

## State File

```
~/.sero-ui/
└── apps/
    └── notes/
        └── state.json
```

```json
{
  "notes": [
    {
      "id": 1,
      "title": "My First Note",
      "body": "Hello, world!",
      "pinned": false,
      "createdAt": "2025-01-01T00:00:00.000Z",
      "updatedAt": "2025-01-01T00:00:00.000Z"
    }
  ],
  "nextId": 2
}
```

## Development

```bash
npm install
npm run build        # Build the web UI (dist/ui/)
npm run typecheck    # Type-check the UI code
```
