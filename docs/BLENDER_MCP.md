# Blender MCP for Zea

[MCP for Blender](https://github.com/ahujasid/mcp-for-blender) (formerly `blender-mcp`) lets Claude control a running copy of Blender: it can build scenes, add and edit objects, set materials and lighting, and render. For Zea, that means Claude can help make 3D characters, story settings and illustration renders for the stories.

> Blender runs on **your own computer**, so this only works there (Claude Code or Claude Desktop on your machine). It does not work in a cloud session.

## 1. One-time setup

**macOS / Linux**

```bash
curl -LsSf https://www.mcp-for-blender.com/install.sh | sh
```

**Windows (PowerShell)**

```powershell
irm https://www.mcp-for-blender.com/install.ps1 | iex
```

The installer installs [uv](https://docs.astral.sh/uv/) if you don't have it, sets up the Blender add-on, and offers to configure your AI apps.

If you'd rather do it by hand:

1. Install uv (`brew install uv` on macOS, `winget install --id=astral-sh.uv -e` on Windows).
2. Install the add-on: `uvx mcp-for-blender install-addon`
3. In Blender, go to **Edit → Preferences → Add-ons** and enable **Interface: MCP for Blender**.

## 2. Connect Claude

- **Claude Code in this repo:** nothing to do. The `.mcp.json` file at the repo root already registers the `blender` server. Approve it the first time Claude Code asks.
- **Claude Code anywhere else:** `claude mcp add blender uvx mcp-for-blender`
- **Claude Desktop:** go to Settings → Developer → Edit Config, add the same `blender` entry that's in `.mcp.json`, then fully quit and reopen the app.

Run only **one** MCP client against Blender at a time.

## 3. Use it

1. Open Blender. The add-on starts its server automatically. To check, press `N` in the 3D viewport, open the **MCP for Blender** tab, and click **Start MCP Server** if it isn't running.
2. Ask Claude, for example:
   - "Create a cozy low-poly treehouse scene at sunset for a children's story."
   - "Add a friendly cartoon owl character on the branch and render a 1920×1080 image."
   - "Save the render to `images/` so we can use it on the website."

## Notes

- The add-on can run arbitrary Python inside Blender. Save your `.blend` file before big changes.
- Renders saved into `images/` can be referenced from `index.html` like the existing images.
