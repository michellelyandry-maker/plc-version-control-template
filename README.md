# [Project Name] — PLC Version Control

This repository (a "repo" is just a project folder that Git tracks the
history of) keeps a full history of changes for the [Project Name] PLC
project — both the hardware configuration and the PLC program blocks.

## ⚠️ Before you do anything: how to start a NEW project correctly

If you're setting up version control for a **new** PLC project, there is
**one important rule**:

> **Click the green "Use this template" button on GitHub. Do NOT use
> `git clone` on this template repo directly.**

### Why this matters

This repository you're looking at right now is a **template** — a
reusable blank starting point, not a real project. If you `git clone`
it directly, your computer will think it's connected to *this* template
repo, and any changes you save could accidentally get pushed into the
shared template that everyone else uses to start their own projects.
That would be a mess for everyone.

Clicking **"Use this template"** instead makes GitHub create a **brand
new, separate, independent copy** just for your project — with its own
history, that only you and your team can see, completely disconnected
from this template.

### Step-by-step: setting up a new project

1. **Go to this repository's page on GitHub** (in your web browser).
2. Click the green **"Use this template"** button near the top of the
   page.
3. Click **"Create a new repository"**.
4. Give it a clear name for your actual project, e.g.
   `machine-B-plc-version-control`.
5. Choose **Private**, then click **Create repository**.
6. GitHub will show you the new repository's page. Copy its web address
   (it will look like
   `https://github.com/your-org/machine-B-plc-version-control.git`).
7. Now, and only now, use `git clone` — but with the **new** address
   from step 6, not this template's address:
   ```
   git clone https://github.com/your-org/machine-B-plc-version-control.git
   ```
   This downloads your new, empty project folder onto your computer,
   already containing this same `.gitignore`, README, and Cursor setup
   — but as your own separate project.
8. Make sure you have an actual TIA Portal project ready — hardware set
   up, program blocks written, and saved.
9. **Open this newly cloned folder in Cursor** (File → Open Folder).
   This turns on the Git and export tools for this specific project.
10. **Run the export tool for the first time**, either:
    - By typing this in Command Prompt (replace the paths with your own):
      ```
      PLC_Openness_Export.exe --project "C:\path\to\YourProject.ap16" --output "C:\path\to\this\cloned\folder"
      ```
    - Or, more simply, by typing this into Cursor's chat:
      ```
      Export the PLC project at C:\path\to\YourProject.ap16 to this folder
      ```
    This creates two things inside your folder: `hardware_config.json`
    (the hardware info) and a `Blocks` folder (your program logic).
11. **Open this README file** and replace `[Project Name]` at the very
    top with your actual project's name.
12. **Save your first version** by running these three commands in
    order (or asking Cursor to do it for you):
    ```
    git add .
    git commit -m "Initial baseline"
    git push
    ```

That's it — your project is now under version control. From here on,
just follow the "Day-to-day workflow" section below every time you make
a change.

## What's tracked here
- `Blocks/` — your PLC's program logic (organizational blocks, function
  blocks, data blocks), saved as readable files
- `hardware_config.json` — your PLC's hardware setup (CPU, modules,
  network settings), saved as a readable file

Both are created by the shared export tool:
https://github.com/michellelyandry-maker/plc-openness-export-tool

## One-time computer setup (only needs to be done once per person, ever)
Full instructions — installing TIA Portal Openness, .NET Framework, the
required Windows permission, Git, and the Cursor/AI integration — are in
the export tool's README:
https://github.com/michellelyandry-maker/plc-openness-export-tool

You do **not** need to repeat this setup for every new project — just
once per computer.

## Cursor setup (already done for you, one thing to check)

This repo already includes a file called `.cursor/mcp.json`, which lets
you talk to Cursor in plain English to run exports and manage Git,
instead of typing commands. It's pre-configured to work automatically,
**as long as** the export tool is installed at exactly this location on
your computer:

```
C:\PLC_Tools\plc-openness-export-tool
```

If you installed it somewhere else, open `.cursor/mcp.json` in this
folder and update the path listed there to match where you actually put
it.

## Day-to-day workflow (after the project is already set up)

Every time you make a change to the PLC — hardware or program logic —
follow these steps:

1. **Get the latest version first:**
   ```
   git pull
   ```
2. **Make your change** in TIA Portal (hardware and/or a program block),
   then save.
3. **Run the export** — either type the command manually, or just ask
   Cursor: *"Export this PLC project"*.
4. **Save the new version:**
   ```
   git add .
   git commit -m "Describe what you changed and why"
   git push
   ```

You can also just ask Cursor to do steps 3 and 4 for you conversationally
— for example: *"What changed since my last export? If it looks right,
commit it and push."*

## Looking at history (seeing what changed and when)

- `git log` — lists every saved version, who made it, and when
- `git diff <old-version> <new-version>` — shows exactly what changed
  between two versions
- `git checkout <version> -- <file>` — brings back an old version of a
  file

You can also just ask Cursor things like *"show me the history of this
project"* or *"what changed in the last version?"* instead of typing
these commands yourself.