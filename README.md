# PLC Version Control

## Getting started with a new project (do this once for every new project)

This repo was created from a template, so it starts out empty except for
this README, `.gitignore`, and a pre-configured `.cursor/mcp.json`. To
actually get this project under version control:

1. **Clone this repo** to your machine (if you haven't already):
   ```
   git clone [this repo's URL]
   ```
2. **Have your TIA Portal project ready** — hardware configured, program
   blocks written, saved.
3. **Open this cloned folder in Cursor.** This activates the Git and
   export tools for this specific project.
4. **Run the first export**, either:
   - Manually: `PLC_Openness_Export.exe --project "[path to .ap16]" --output "[path to this folder]"`, or
   - By asking Cursor: *"Export the PLC project at [path to .ap16] to this folder"*

   This creates `hardware_config.json` and a `Blocks/` folder with your
   project's actual data.
5. **Make your first commit:**
   ```
   git add .
   git commit -m "Initial baseline"
   git push
   ```

Once this is done, the day-to-day workflow below applies going forward.

## What's tracked here
- `Blocks/` — PLC program blocks (OBs, FBs, data blocks), exported via
  the Openness-based export tool
- `hardware_config.json` — hardware configuration (CPU, modules, network
  settings), exported using the same tool:
  https://github.com/michellelyandry-maker/plc-openness-export-tool

## One-time setup (per computer, not per project)
See the export tool's README for full setup instructions (Openness,
.NET Framework, Windows security group, Git, and Cursor/MCP setup):
https://github.com/michellelyandry-maker/plc-openness-export-tool

## Cursor / MCP setup

This repo includes a `.cursor/mcp.json` file, already configured to work
automatically — as long as you clone the export tool to this exact
location on your machine:

```
C:\PLC_Tools\plc-openness-export-tool
```

If you clone it anywhere else, edit the `plc-export` path in
`.cursor/mcp.json` to match. See that repo's README for full setup
instructions (installing `uv`, Python, and the `mcp` package).

## Day-to-day workflow
1. `git pull` — get the latest changes first
2. Make your change in TIA Portal (hardware and/or a program block), save
3. Run the export tool (manually or by asking Cursor), pointing it at
   this project's `.ap16` file and this repo's folder
4. `git add .`
5. `git commit -m "Describe what changed and why"`
6. `git push`

All of the above can also be done conversationally in Cursor once it's
open in this folder — e.g. "what changed?", "commit this with message
'...' and push it".

## Viewing history
- `git log` — see all past changes
- `git diff <old-commit> <new-commit>` — compare two versions
- `git checkout <commit-hash> -- <file>` — restore an old version of a file

Any of the above can also be asked directly in Cursor, e.g. "show me the
git log" or "what changed in the last commit?".