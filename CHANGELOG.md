# Changelog

## 0.1.12

- **Report a Bug and Request a Feature** in the Help menu open a prefilled form on GitHub, with steps, what you
  expected, a proposed solution and, if you leave it ticked, your Hinoki and OS versions (the real Linux release).
- **Windows: model servers keep running** after Hinoki exits, as they already did on Linux and macOS.
- **Models & Servers:** the APIs tab lists your saved model APIs with Edit and Remove. A server whose software is
  missing offers Install. Fit checks and recommended context use your NVIDIA GPU's memory when you have one.
  Removing a model or server asks first, naming it.
- **Project Map:** the machine list folds away on a narrow board, a jump host can log in with its own saved
  password, and a window opened on a server starts with a board on that server.
- **Projects:** New Project makes a first commit, picks templates from the keyboard and says why a name is
  refused. Clone sets up the Project Map, offers Try Again after a failure and Open It when the folder exists.
  KannaCode's `.kanna/` folder stays out of git.
- **Chat:** chats are named from their first message, a stopped reply says "Stopped", the mode name stays visible
  and a `#file` path attaches the right file.
- **Smaller fixes:** File > Open Folder shows the right shortcut, row actions no longer push rows taller, side
  panels open wide enough to read, the Code Map menu closes on Esc or a click outside, a master-password typo no
  longer ends setup, Hinoki has its own Settings section, and the update offer waits until setup is closed.

## 0.1.11 (2026-11-19)

- **Fits a laptop screen:** Models & Servers, Passwords, Setup, New Project and their forms fit a 1120×700 window.
  Field and button rows wrap instead of overflowing, a new server's form scrolls into view when it opens, and only
  the form scrolls in New Project.
- **Hover to see the full name:** rows in Passwords, the KannaCode models list, Models & Servers hosts and the
  benchmark leaderboard show their full name and details when a name is cut off.
- **Checks before running:** New Project on an SSH host, the container engine setting, Run benchmark, Setup's
  KannaCode alias and model port, server ports (1 to 65535) and Clone Repository's URL are checked as you enter
  them, with a message that says what to fix, instead of failing later.
- **Smaller fixes:** the Passwords Create buttons go straight to the master password. Code Map's PDF export opens
  the save dialog in the project folder. Name, path, URL and search fields no longer spell-check.

## 0.1.10

- **Project Map, a machine's Test** now lists its toolchains and their versions (and the ones the project asks
  for), its health, and the project's git status there. It proposes the project's builds for that machine's
  system, and **Run build** and **Run tests** run them in a terminal there after you confirm. A Windows machine's
  Test takes about 7 s instead of 28 s. An opt-in background refresh keeps the board current, from one window per
  project.
- **Project Map, setting up:** click a role on a machine to set it up there; click a machine's Code box to choose
  its folder and open it. The KannaCode box opens a model panel: the current model, the models the Tests found,
  and Configure a new model, which asks your local servers and the board's machines first. A failed SSH login says
  what it means, and Escape, zoom, pan and the keyboard work across the board.
- **SSH with a password:** remote windows, tunnels and folder browsing use the password saved for that machine in
  Passwords, and first connections to never-seen or password-only hosts work. A dropped connection is noticed and
  can be reconnected. ProxyJump and Include aliases, ssh-agent keys, arm64 servers and paths with spaces are
  handled.
- **Security:** host keys are checked before any login, and a changed host key never gets a password. Remote
  tunnels stay on loopback, and a git token stays out of the environment. A machine name can't add lines to
  `~/.ssh/config`. Settings that run programs or choose installers are user-only, so a cloned project can't set
  them. Vulnerable dependencies are updated.
- **KannaCode chat:** failures show with Retry, and replies show their token counts. The model and mode follow your
  settings. Stop works before a reply starts and ends the whole process tree on Windows. Files and images can be
  added by path, and Hinoki's read-only tools run without an approval card.
- **Passwords:** locking clears every window and says so. Entry titles are unique, multi-line keys and notes work,
  and the keychain keeps one item per entry (older entries move over by themselves). A keychain that stops
  answering no longer hangs the KeePass database. In the form, Enter saves and Escape cancels.
- **Models & Servers:** Ollama downloads show their progress and end with a reason if they stall. Model servers
  outlive a Hinoki restart and restart when their launch settings change. Edit and Remove are in the KannaCode
  view, which follows `~/.kanna` as it changes, and KannaCode's config files are never written over when they
  don't parse. Context sizes read the way their makers write them (1M, 200K). The forms and tabs fit a laptop-size
  window.
- **Updates:** Restart Now closes the windows cleanly instead of killing Hinoki. Stalled or unwritable downloads end
  with a reason, updates use your proxy, and a download Hinoki can't install itself says where the file is and what
  to do with it. Updates now come from `DarrellBest-Org/hinoki-releases`.
- **Smaller fixes:** the setup wizard no longer freezes on an error and can be skipped. A GPU that detection missed
  can be entered by hand. New Project's name checks match what gets created, and Clone Repository never passes the
  URL to git as an option. The About dialog fits a laptop screen. The Benchmarks filter ignores case. An empty Code
  Map says which languages it reads. Cmd+B toggles the side bar.
- **KannaCode 1.18.2** with Hinoki's tool-approval and MCP tool-budget updates, and models kept with their keys in a
  workspace opened at the home folder.

## 0.1.9

- **Code Map, big files:** opening a big module (hundreds of functions) shows its classes and its first functions,
  then a "+K more" box; click it for the next ones. Searching or going to a function shows that one beside them,
  not everything before it. An opened file makes room for itself instead of drawing over its neighbours, and
  Re-layout keeps the map's shape with nothing on top of anything else.
- **Code Map, export as PDF:** a new icon on the map's toolbar saves the map as shown as a sharp vector PDF, on this
  computer, also from an SSH or dev-container window.
- **Report Issue and Documentation** open the public Hinoki releases page. **Install KannaCode** asks where to get it
  from (Settings, `hinoki.kannacode.repository`) instead of assuming a source.
- **KannaCode 1.18.2.** Switching models in the middle of a session no longer breaks the following turns on Bedrock,
  and the GovCloud Bedrock models are back in the built-in list.

## 0.1.8

- **Code Map:** a new icon in the left bar opens a live map of the project's code: its systems, folders, files,
  classes and functions, and how they connect (imports, calls, inheritance). Zoom from the big picture down to one
  function and back. Every box and line has a small go-to-code icon that opens the exact file and line in the editor.
  The map is for reading and finding your way; editing happens in the editor.
  - **Python first:** Python files show their classes, functions and calls. Other languages show their folders,
    files and imports.
  - **Containers:** services from compose files and Dockerfiles are on the map with their networks, ports and
    `depends_on` links, joined with the containers actually running on the project's Docker engine (this computer
    or another machine, marked "on" that machine). Containers that aren't the project's stay off the map.
  - **Stays current as you save:** only the changed file is read again, so a save shows on the map in well under a
    second, also in SSH and dev-container windows. Nothing is installed on a remote box for it.
  - **Summaries (optional, off by default):** turn them on and KannaCode writes a one-line purpose, inputs and
    outputs for each Python file and groups the project into named systems. Each file is summarised at most once a
    day, and only when it changed. Summaries are kept on this computer, not in the project.
  - **KannaCode can read the map** with three new tools: `code_map_overview`, `code_map_node` and `code_map_find`.
- **Thin client:** KannaCode running on the server now gets Hinoki's tools too (the debugger, tests, containers,
  the Code Map and the rest), over the same SSH connection, with a token that lasts only as long as the session.
- **KannaCode 1.18.1.** Its usage totals no longer show old numbers after a usage file is replaced.

## 0.1.7

- **Project Map:** every project opens on a board of where its parts run, and the Project Map has its own icon in the
  left bar. Put machines on it (this computer, SSH hosts, cloud model APIs) and give each one jobs: KannaCode, the
  code (in an exact folder), the model and containers. Draw SSH, API and jump-host lines between them. New Project hands
  the project it made to the map, with the code already on its machine and folder.
  - **Adding a machine** asks how it logs in: this computer's SSH key; its password once, after which Hinoki puts this
    computer's key on it (making one if this computer has none); a password kept in Hinoki's Passwords; or a key file,
    through a `~/.ssh/config` entry Hinoki shows you before writing it.
  - **Each machine** can get an SSH key of its own, shows the public key it is reached with (to copy), and opens a
    terminal on it, in the project folder.
  - **The code will live here:** a folder that isn't there yet can be created, or a repository cloned into it. The
    clone runs on this computer, with its git logins, so the machine needs no internet.
  - **Models:** connect KannaCode to a model provider (a cloud API, a model server on another machine, or one on this
    computer). Detect lists the models it has, when its API can, or you add them by hand; the dropdown on KannaCode's
    line picks the one it uses.
  - **Test** checks a machine for real from this computer: SSH, a shell, the project folder, Docker, model servers on
    the usual ports, internet access and its operating system.
  - **Apply** sets the project up from the board. It opens SSH tunnels to model servers (through a jump host when the
    board draws one), adds a KannaCode model for each model, picks the one KannaCode uses, points containers at the
    right machine, and offers to open the code where it lives. What only you can do comes back as a button. A project
    that was applied gets its tunnels back when its window opens.
  - **Ready-made setups:** everything local; a cloud model; code on a server; a model on another machine; a Mac serving
    the model with MLX; a Linux GPU box for the model and containers; one Linux server for everything; a server behind a
    jump host; a local model plus a cloud one; code on one server and the model on another (a Windows PC as the screen,
    say); and a thin client. Or copy another project's board.
- **API keys live in Hinoki's Passwords** (KeePass or the system keychain), not in a file: KannaCode asks Hinoki for a
  key when it calls the model. Each provider's block links the page where its keys are made, and the board links
  GitHub, GitLab and Hugging Face tokens. Keys already in `~/.kanna/keys.json` move over with one button.
- **KannaCode drives the debugger, tests and containers.** It can set breakpoints (with conditions and logpoints),
  start and step through a debug session, read the stack and variables, and evaluate. It can find and run tests,
  also under the debugger, and read the failures. It can list containers, read their logs, run commands in them and
  open a window inside one. This works in local and remote windows.
- **Containers can run on another machine:** choose this computer's Docker (its current context, so colima and
  OrbStack work), an SSH host's Docker or Podman, or a Docker URL. Reopening a project in a container on a remote
  engine copies it into a volume there. KannaCode works on code inside dev containers the same way it does on an
  SSH host.
- **Passwords:** a password store in an encrypted KeePass database (KeePassXC opens it) or the system keychain, with
  a Passwords view to add, find, copy and lock. Git logins are saved and filled in from it. KannaCode can use a
  password without seeing it: you type the value into Hinoki's prompt, and commands that need one run in a terminal
  you can see.
- **KannaCode is the only AI in Hinoki.** Theia's own model providers and agents are gone, so no window, local or
  remote, calls a model API by itself, and API keys are no longer put into the environment of terminals and other
  programs.
- **Security fix:** the backend Hinoki starts on an SSH host now listens only on that host's loopback, reached
  through the SSH connection. Before, anyone who could reach the host's network could use it without logging in.
- Switching containers back to this computer after a remote engine failed no longer leaves Docker pointed at the
  failed engine until Hinoki restarts.
- **Hinoki is the hub.** Your code and your models can each be on this computer or on another box, and Hinoki
  connects them:
  - **KannaCode always runs on this computer**, also in a remote window. Its file, search, shell and git work happens
    on the remote box through Hinoki, and every model call goes out from here.
  - **The remote box needs only SSH:** no admin rights, no internet access and no model API. Nothing is installed
    there. Hinoki brings its own backend and runtime, and carries the Linux one, so connecting needs no download.
  - **Models anywhere:** a model on this computer, a cloud API, or a model on another box behind Hinoki's SSH tunnel
    works the same for local and remote projects.
  - In a remote window, **KannaCode can operate the window** with its Hinoki tools, and **Open KannaCode in
    Terminal** opens a terminal window on this computer.
- **New projects on a server:** in New Project, choose an SSH host under "Where", browse its folders (or make a new
  one) and create. The files are made here and copied over, with dependencies recorded but nothing installed, and
  the window opens the project on the server. KannaCode can do the same (`create_project` with `ssh_host`).
- **SSH terminals:** "Hinoki: Open SSH Terminal…" opens a shell on a server in a folder you pick. In a remote window,
  every new terminal already runs on the server in the project folder. Connecting to a host also lets you browse
  for the folder instead of typing it.
- **KannaCode is packaged with Hinoki,** with its own Python and everything it needs. Nothing is installed or
  downloaded on first start, and it updates together with Hinoki.
- **Setup and Models & Servers manage this computer's model servers** in every window. The "relay to the workspace
  host" step is gone, and a model set up on an SSH host gets its own name instead of replacing the local one.
- **Ollama keeps the context you chose:** Hinoki sends it with every request. Before, Ollama could load a smaller
  one and drop the start of a long conversation, which showed up as HTTP 500 "no user query found in messages".
  The Qwen3.8-27B recipe uses the right Ollama tag, waits for the download and reports a failed one.
- **Remote fixes:**
  - Extensions copied to a remote box keep their executable bit, also from Windows, and a Linux box gets the Linux
    builds of debugpy and ruff, so both work there.
  - A remote window is no longer titled "Dev Container".
  - A model server that already runs (an Ollama service, or an mlx-serve or vLLM you started by hand) is used as it
    is, on an SSH host or on this computer, instead of starting a second copy. Stopping it in Hinoki then only
    closes the tunnel and leaves the server running.
  - An SSH host can be typed as `user@hostname` in Setup and in Models & Servers ("Other host…"); it no longer has
    to be in `~/.ssh/config` first. Hosts added to that file show up without restarting Hinoki.
  - **A remote box makes no calls of its own.** The AI model providers, MCP servers, benchmarks and update checks of
    a remote window run on this computer; before, the box's backend could call a model provider's API (with a key it
    found on the box) and check for updates from the box.
  - The backend on a remote box keeps its state in `~/.hinoki-remote`, so it no longer overwrites the settings of a
    Hinoki installed on that box, and an updated Hinoki always copies its new backend there (before, a rebuild of the
    same version kept running the old one).
  - KannaCode's file paths in a remote window are the box's: relative to the open folder, with `~` the box's home
    (from Windows, they were turned into Windows paths and `get_problems` found nothing).
- **Removing a server also removes the KannaCode model name** that reaches it (the dialog says which), so the model
  list doesn't keep a name that answers nothing.
- **An answered approval in the chat shows just your answer** (✓ Allow or ✓ Deny) instead of buttons that look
  like they still need clicking.
- **Hinoki's terminals identify themselves as VS Code's do** (`TERM_PROGRAM=vscode`), so a server whose shell
  startup attaches a tmux or zellij session no longer drops you into your running session.
- **A project Hinoki creates** (from New Project or by KannaCode) opens without the "trust the authors" prompt.
- **The window can no longer end up scrolled** (the top cut off and a black bar at the bottom).
- **The chat says why KannaCode could not start** (for example an unknown flag in `hinoki.kannacode.extraArgs`);
  before, the message just got no answer.
- **Setup:**
  - Reusing an existing model server applies the recipe's context when the server's is larger, which could overflow
    the GPU.
  - The model that setup makes the default is now the one the chat and status bar use, even if you picked another
    one earlier with Select Model.
- **Windows:** KannaCode prefers Git for Windows' bash over WSL's, so commands run with the right environment, and
  the installer carries the Windows builds of debugpy and ruff (it had the Linux ones, so ruff did not start).

## 0.1.6

- **What's New:** after an update, Hinoki shows what changed (this page).
- **Fewer approval prompts:** Hinoki's read-only tools, like `hinoki_status`, `get_problems` and `list_servers`,
  run without asking. Tools that change something still ask in Ask and Auto-edit mode.
- **The chat stays on the newest message** until you scroll up yourself. Before, an approval card appearing or
  resizing could stop the scrolling, so later cards and replies appeared out of view and the chat seemed stuck.
  KannaCode's "retrying in Ns" notices now show in the chat too.
- **Workspace trust:** until you answer "Do you trust the authors of the files in this folder?", tasks and language
  servers wait. KannaCode now tells you so right away instead of a task hanging for minutes, and `hinoki_status`
  shows whether the folder is trusted.
- **Your API key stays with the endpoint it belongs to:** a model that uses its own `base_url` (a proxy or gateway)
  no longer shares its key with Hinoki's built-in providers.
- **KannaCode can control Hinoki right after setup**, without restarting Hinoki first.
- **Changing the default model through KannaCode** now updates Hinoki's model choice and the status bar.
- **Models & Servers** refreshes when KannaCode adds a server, and `list_server_types` says which server types are
  installed.
- **Tasks:** `list_tasks` shows your tasks.json tasks right away, and `run_task` runs them directly.
- **Extensions:** `uninstall_extension` accepts the extension's id, and removed extensions no longer show as
  installed.
- **New projects:**
  - A plain folder with a venv now uses the uv that ships with Hinoki and shows the real error if it fails.
  - The Python package template's starter test passes for names with dashes.
- **Updates:** version suffixes such as `.post1` and `rc1` are compared correctly.

## 0.1.5

- **Models through this computer:** in a remote workspace, run a model on this computer or on a machine only it
  can reach (like the Mac on your desk running MLX). Hinoki relays it to the workspace host over its own SSH
  connection, so KannaCode there can use it although the workspace host never connects to that machine.
- **Any model from Hugging Face** in setup (Hinoki Setup → Model, or Models & Servers → Set up a model…):
  search filtered to what the machine runs (MLX, GGUF or vLLM), a details card (parameters, quantization, size,
  context, vision) and recommended settings, including a context window that fits the machine's memory.
- **Remote workspaces:** the host list reads your ~/.ssh/config, and a host's Port, User and IdentityFile
  (with `~` paths) now apply, so key logins work without a password prompt.
- **Mac model hosts over SSH** start correctly and stay awake while serving; SSH hosts report their memory.
- **llama.cpp** downloads GGUF repos itself (`owner/repo:Q4_K_M`); registered models use the context a running
  server reports.

## 0.1.4

- **KannaCode chat approvals work:** the Allow and Deny buttons on "KannaCode wants to run…" prompts (and the
  buttons on KannaCode's questions) can be clicked again.
- **Long commands wrap** inside approval prompts instead of running off the right edge.
- **Launch KannaCode opens the chat panel.** Each model in the KannaCode view also has a button to chat with it
  and a button to open it in a terminal.

## 0.1.3, the first public release

- **Projects, PyCharm-style:**
  - **Projects home screen:** recent projects with search, git branch and project type.
  - **New Project wizard:** Python (uv + .venv), Python package, FastAPI, data science (Jupyter), Node.js +
    TypeScript, empty, or "describe it to KannaCode".
  - **File menu:** Clone Repository and Close Project.
  - **Project view:** the file tree is now called the Project view.
- **KannaCode operates Hinoki:**
  - **52 built-in tools** for projects, files, terminals, IDE commands, extensions, tasks, model servers, cloud
    models and keys, MCP servers, SSH remotes and settings.
  - **A complete Hinoki guide** that KannaCode reads, so it can answer questions and suggest next steps.
- **Web search** for KannaCode, on by default (`hinoki.kannacode.webSearch`: on, ask, docs or off).
- **Automatic updates:** Hinoki checks this repository's `latest.json`, verifies the download's checksum and
  updates itself.
- **Setup wizard fixes:**
  - It reuses a model server you already set up instead of downloading the model again.
  - Its model test works when Hinoki is opened from the Dock or Finder.
- **KannaCode's built-in defaults** are the commercial AWS Bedrock ones.
