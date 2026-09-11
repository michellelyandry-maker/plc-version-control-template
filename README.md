\# PLC Version Control



This repository tracks version history for the \[Project Name] PLC project

(TIA Portal), covering both hardware configuration and PLC program blocks.



\## What's tracked here

\- `Workspace1/` — PLC program blocks, exported via TIA Portal's built-in

&#x20; Version Control Interface (VCI)

\- `hardware\\\_config.json` — hardware configuration (CPU, modules, network

&#x20; settings), exported using the shared export tool:

&#x20; https://github.com/michellelyandry-maker/plc-openness-export-tool



\## One-time setup

See the export tool's README for full setup instructions (Openness,

.NET Framework, Windows security group, Git):

https://github.com/michellelyandry-maker/plc-openness-export-tool



## Cursor / MCP setup

This repo includes a `.cursor/mcp.json` file, already configured to work
automatically — as long as you clone the export tool to this exact
location on your machine:

C:\PLC_Tools\plc-openness-export-tool


If you clone it anywhere else, edit the `plc-export` path in
`.cursor/mcp.json` to match. See that repo's README for full setup
instructions (installing `uv`, Python, and the `mcp` package).



\## Day-to-day workflow

1\. `git pull` — get the latest changes first

2\. Make your change in TIA Portal (hardware and/or a program block), save

3\. Export:

&#x20;  - For program blocks: right-click the block under Version control

&#x20;    interface → export to `Workspace1` (Cancel any "Git Commit" popup

&#x20;    TIA Portal shows — we commit manually, see below)

&#x20;  - For hardware config: run the export tool, pointing it at this

&#x20;    project's `.ap16` file and this repo's folder

4\. `git add .`

5\. `git commit -m "Describe what changed and why"`

6\. `git push`



\## Viewing history

\- `git log` — see all past changes

\- `git diff <old-commit> <new-commit>` — compare two versions

\- `git checkout <commit-hash> -- <file>` — restore an old version of a file

