# Claude Team Cheat Sheet

Need something fast? The Quick Reference below is the cheat sheet. Everything after it, Part I and Part II, is the deep dive.

Compiled from official Anthropic documentation ([docs.claude.com](https://docs.claude.com), [support.claude.com](https://support.claude.com), [code.claude.com/docs](https://code.claude.com/docs)). Accessed 13 Aug 2026.

---

## Quick Reference

**Install**
```bash
# macOS / Linux / WSL
curl -fsSL https://claude.ai/install.sh | bash

# Windows PowerShell
irm https://claude.ai/install.ps1 | iex
```
VS Code extension: Extensions view, search "Claude Code." Two separate installs, one shared history. Details in [section 8](#8-install--first-session).

**Daily commands**

`/init` · `/plan` · `/compact` · `/context` · `/mcp` · `/permissions` · `/code-review` · `/rewind` · `/usage` · `/doctor` · `/model` · `/effort`

Full list in [section 13](#13-essential-slash-commands).

**Permission modes.** Cycle with `Shift+Tab`

`Manual` → `Accept Edits` → `Plan` → `Auto` → `Don't Ask` → `Bypass`

Detail in [section 11](#11-permission-modes).

**Common flags**

| Flag | Does |
|---|---|
| `-p "prompt"` | Run once and exit |
| `-c` / `-r` | Continue / resume a session |
| `--model`, `--effort` | Set model or reasoning level |
| `-w` | Start in an isolated worktree |
| `--permission-mode <mode>` | Start in a specific mode |

Full reference in [section 12](#12-cli-flags-reference).

**Which surface**

| Need | Use |
|---|---|
| Quick question, draft, brainstorm | Chat |
| Hand off a multi-step task, don't watch | Claude Cowork |
| Working in an open Excel/PowerPoint/Word file | Claude for Microsoft 365 |
| Hands-on, full control, any files or code | Claude Code (CLI or VS Code extension) |

Full table in [section 1](#1-which-claude-surface-for-which-job).

**Don't forget**
- Extension installed ≠ `claude` on your PATH. Install both ([section 8](#8-install--first-session)).
- Permission rules check deny → ask → allow. Deny always wins.
- Run `/doctor` first, whenever something feels broken.

---

## Part I: Pick Your Surface

Claude shows up in a lot of places. This part helps you choose the right one. The most common mistake: opening a chat window for work that wanted an agent instead.

## 1. Which Claude Surface for Which Job

| If you want to... | Use |
|---|---|
| Ask a quick question, draft text, brainstorm | **Chat.** claude.ai, desktop, or mobile |
| Get a polished, reusable deliverable out of a chat | **Artifacts** |
| Keep long-running context for a topic, client, or team | **Projects** |
| Hand off a multi-step task and get on with your day | **Claude Cowork** |
| Work inside an Excel, PowerPoint, Word, or Outlook file you already have open | **Claude for Microsoft 365** |
| Have Claude act inside your browser | **Claude in Chrome** |
| Trigger and monitor Claude from Slack | **Claude Tag** |
| Work hands-on across a folder of files (notes, data, docs, or code) with full control over each step | **Claude Code.** Part II |

### Cowork or Claude Code?

Both are agentic, and both run on the same engine. What separates them is how much you want to steer.

- **Cowork.** State a goal and step away. Claude plans the work, runs it, and hands back something finished. Use it when you don't need to watch.
- **Claude Code.** Stay in the loop, approving actions and correcting course turn by turn. Use it when the task is exacting, or when you want to see the work happen.

Chat and Cowork share one home in the desktop app and on claude.ai. Projects and Artifacts show up in both.

---

## 2. Projects & Artifacts

**Projects** are persistent workspaces. They keep files, instructions, and prior chats together so you stop re-explaining background every session.
- Organise by client, topic, or workstream: "Q3 Board Reporting," "Client X Research."
- Claude searches project knowledge and pulls in what's relevant, not everything at once.
- Team and Enterprise plans can share a project with view or edit permissions.

**Artifacts** are the polished, standalone output Claude produces alongside a chat answer: a document, slide outline, chart, interactive tool, or code, shown in its own panel so you can iterate without scrolling past chat text.
- Created automatically once content is significant and reusable, at 15 lines or more.
- Edit in place. Highlight a section, describe the change, and Claude updates that part alone.
- Can go further than static output:
  - Connect to MCP connectors such as Google Calendar or Gmail for live data
  - Publish and share, or let others fork and remix a copy
  - Store up to 20 MB of persistent state, personal to each viewer or shared across all of them
- Available on every paid plan and the free tier. Usage limits vary by plan.

> **Tip:** use a Project for anything you'll return to over weeks. A plain chat plus an Artifact covers a one-off deliverable.

---

## 3. Claude Cowork

Cowork is where you hand Claude a job and walk away. Give it a goal instead of steps. It plans, works across your files and connected tools, and returns something ready for review.

**How it behaves**
- Runs in a sandboxed environment with controlled file and network access. Deleting a file always needs your authorisation.
- Supports scheduled and recurring tasks, so routine work runs without you starting it each time.
- Sessions keep running with your laptop closed. Pick up progress from any device.

**What you need**
- A paid plan: Pro, Max, Team, or Enterprise.
- Desktop for macOS and Windows. Web and mobile are in beta.
- The **Claude Desktop app open on your machine**, for anything that reaches your computer:
  - Local file access
  - Browser use
  - Computer use (Claude clicking and typing on your screen)

```
Read the project brief in brief.docx. Search online for the
latest related market trends. Create an analysis document with
recommendations and an Excel spreadsheet with the action plan
and timelines.
```

---

## 4. Claude for Microsoft 365

Sidebar add-ins let Claude work inside the Office file you already have open. No copying into a chat window.

| App | What Claude does |
|---|---|
| **Excel** | Reads multi-tab workbooks, builds models with real formulas, tracks every cell it changes, preserves formula dependencies |
| **PowerPoint** | Builds and edits slides inside your template (layouts, fonts, colours) and produces native, editable charts |
| **Word** | Edits land as tracked changes. Claude replies in comment threads explaining what changed and why |
| **Outlook** (beta) | Triages your inbox, drafts replies that wait for you to send, finds time across calendars |

**Working across apps**
- Turn on *Let Claude work across apps* and context carries between all four. Pull numbers from an open Excel model straight into a PowerPoint slide or Word memo.
- Claude only reads and writes files that are **currently open**. It can't open, close, or switch files on its own.
- Skills work inside the Excel and PowerPoint add-ins too, so one team workflow becomes a one-click action.

**Setup & access**
- Install each add-in from the Microsoft Marketplace. Open each app and activate the add-in once before using cross-app features.
- Available on all paid plans. The Word add-in requires Team or Enterprise.
- Routable through Amazon Bedrock, Google Cloud's Vertex AI, or Microsoft Foundry, though cross-app mode requires signing in with a Claude account directly.
- Team and Enterprise admins control access through **Organization settings → Office agents**.

---

## 5. Claude in Chrome & Claude Tag

- **Claude in Chrome** reads the page you're on from the side panel. With the desktop app open, it can also act: clicking, filling forms, navigating sites for tasks like testing a web app or extracting data.
- **Claude Tag** lets you tag `@Claude` in a Slack channel to delegate a task without leaving Slack. Anyone in the channel can trigger and monitor it.

---

## Part II: Claude Code

The most capable and configurable surface, and the engine the others are built on. Worth learning whether or not you write code.

## 6. What Claude Code Is

Claude Code is Anthropic's agentic tool for working in a folder on your machine. It reads what's there, then plans, edits, runs commands, and iterates through natural-language instructions, with you approving as much or as little as you like.

- **Agentic loop.** Claude reads your prompt, picks the tools it needs (Read, Edit, Bash, WebFetch, and others), runs them, and keeps going until the task is done.
- **Session-based.** Each conversation has its own context window. Resume, branch, or fork it later.
- **Two ways in, same engine:** the CLI in a terminal (including VS Code's integrated terminal), or the VS Code extension's graphical panel. This reference covers both, and [section 20](#20-cli-vs-vs-code-extension) lists exactly where they differ.

---

## 7. Not Just for Code

The name undersells it. Claude Code's architecture doesn't care what kind of files it's pointed at. The official docs cover working in notes and non-code folders as a first-class workflow, and Cowork itself is built on the same foundation. If it lives in a folder, Claude Code can work on it.

**Why it works for non-code files**
- **Filesystem access.** Reads and writes any file format, source files or otherwise.
- **Shell execution.** Runs any command-line tool, covering conversion, extraction, and batch processing.
- **MCP connectors.** Reaches external systems like Drive, Slack, or a database.
- **Skills.** Encode any repeatable workflow, not only coding ones.

**What that looks like in practice**
- **Research and writing.** Synthesise a folder of notes into a draft, compare several documents and surface the differences, keep a running second brain up to date.
- **Data work.** Turn a directory of CSVs into a single summary, clean messy exports, produce charts from raw numbers.
- **Document production.** Generate reports, briefs, or meeting packs from source material, and regenerate them when the inputs change.
- **File and folder operations.** Reorganise a chaotic directory, rename by convention, extract structured data from a pile of PDFs.

> **Tip for non-developers:** start Claude Code in a folder of documents rather than a repo, and write a `CLAUDE.md` describing what the folder is for and how you want output formatted. Everything else in this reference works the same way.

---

## 8. Install & First Session

**macOS / Linux / WSL:**
```bash
curl -fsSL https://claude.ai/install.sh | bash
```

**Windows, PowerShell (recommended, no admin rights required):**
```powershell
irm https://claude.ai/install.ps1 | iex
```

**Windows, CMD:**
```cmd
curl -fsSL https://claude.ai/install.cmd -o install.cmd && install.cmd && del install.cmd
```

**Package managers:**
```bash
brew install --cask claude-code
winget install Anthropic.ClaudeCode
npm install -g @anthropic-ai/claude-code
```

> **Windows notes:** the error `The token '&&' is not a valid statement separator` means you're in PowerShell, not CMD. Use the PowerShell command instead. Git for Windows is optional but enables the Bash tool; without it, Claude Code uses the PowerShell tool. Sandboxing needs WSL2. Native Windows and WSL1 don't support it.

**Verify and start:**
```bash
claude --version
claude                                       # interactive session in the current folder
claude "summarise the notes in ./research"   # one-shot prompt
```

**Also want the VS Code extension?**

The CLI above works in any terminal, VS Code's included. The extension adds a graphical panel on top: inline diffs, an @-mention picker, and automatic context from your selection. Install it separately.

1. In VS Code, press `Cmd+Shift+X` (Mac) or `Ctrl+Shift+X` (Windows/Linux) to open Extensions.
2. Search "Claude Code" and click **Install**.
3. Click the Spark icon in the editor toolbar (appears once a file is open), or use the Command Palette and type "Claude Code."

> **The extension does not put `claude` on your PATH.** It bundles a private copy of the CLI for its own panel only. Do both installs above if you want the terminal command *and* the graphical panel; they share your login and conversation history either way. More on how they differ in [section 20](#20-cli-vs-vs-code-extension).

**First-session setup:**
1. Run `/init` to generate a starter `CLAUDE.md` for the folder.
2. Run `/mcp` to connect any servers you need.
3. Run `/permissions` to set your approval rules.

> **Tip:** run `/doctor` any time. It diagnoses install problems, trims a bloated CLAUDE.md, and suggests pre-approving commands you keep having to allow.

---

## 9. Your First Claude Code Project: HTML From a GitHub Repo (VS Code)

A short walkthrough for going from an empty VS Code window to a working HTML file in a real repo. Two paths: tell Claude to do the git work, or drive it yourself.

**1. Have Claude Code ready**

Either surface works for this walkthrough: the CLI (install steps in [section 8](#8-install--first-session)), the VS Code extension, or both. If you skipped [section 8](#8-install--first-session), install the extension from VS Code's Extensions view and search "Claude Code."

**2. Open a working folder**

Open a folder in VS Code (`File → Open Folder`), then open the integrated terminal (`` Ctrl+` `` on Windows/Linux, `` Cmd+` `` on macOS). Everything below runs from there.

**3. Get the repo, one of two ways**

**Path A: tell Claude to clone it.** Start Claude Code in the empty folder and prompt it directly:

```bash
claude
```
```
Clone https://github.com/<your-username>/<your-repo>.git into this folder.
```

Claude runs `git clone` through its Bash tool. In Manual mode it asks you to approve the command first; in Accept Edits or Auto mode it runs without stopping.

**Path B: clone it yourself first.** For engineers who'd rather drive:

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
code .
claude
```

`code .` reopens VS Code scoped to the cloned folder. Starting `claude` from inside it means every file reference, edit, and commit stays scoped to that repo.

**4. Explore first, then decide what to build**

Don't hand Claude a fixed spec here, and don't feel locked into "index.html" either. Let it look around the repo, and let yourself get a little creative with the brief:

```
Explore this repository: what it does, how it's structured, any existing
style or branding you can find. Based on what you find, create an HTML
file that fits the project, a landing page, a demo, a status page,
whatever makes sense. Use your own judgement on layout, copy, design,
and what to name the file. Keep it to one file, no build step.
```

Change the brief to whatever you want. Ask for something playful, something that matches a colour scheme already in the repo, or a page themed around what the project actually does. Let Claude name the file too; a status dashboard might make more sense as `status.html` than `index.html`. The interesting part of this step isn't the HTML. It's watching Claude read the repo and make choices you didn't spell out.

**5. Review before you accept**

The VS Code extension shows the change as an inline diff, the same view you'd get from a pull request. Read it, then approve or ask for a change before it writes to disk.

**6. Preview it**

Open the file Claude created directly in a browser, or install the **Live Server** VS Code extension and click "Go Live" for auto-refresh on save.

**7. Commit and push**

Ask Claude:
```
Commit this with a clear message and push to main.
```

Or run it yourself:
```bash
git add .
git commit -m "Add project page"
git push
```

> **Tip:** if `git push` fails with a permissions or auth error, check `git remote -v` first. A repo cloned over HTTPS needs a GitHub personal access token the first time you push; one cloned over SSH needs a key already added to your GitHub account.

---

*Compiled from official Anthropic documentation at docs.claude.com, support.claude.com, and code.claude.com/docs. Accessed 13 Aug 2026. These products change quickly. Check `/release-notes` in Claude Code, or the relevant Help Centre article, before treating any detail here as current.*
## 10. Core Concepts

| Concept | What it means |
|---|---|
| CLAUDE.md | A memory file Claude loads automatically at session start: conventions, context about the folder, commands to run. |
| Context window | The model's working memory for the session. Fills up over long sessions; free it with `/compact`. |
| Checkpoints | Snapshots of files and conversation, saved after each turn. `/rewind` rolls back either or both. |
| Subagent | A separate Claude instance handling a delegated task, with its own context window. Used for research, isolation, and parallel work. |
| Skill | A reusable, invokable capability: a prompt plus optional scripts. Yours, bundled, or synced from claude.ai. |
| Plugin | A bundle of skills, agents, hooks, and MCP servers, installed or shared as one unit. |
| Hook | A script that runs at a lifecycle event: before a tool runs, after a file changes, at session start. |
| MCP server | A connector giving Claude access to an external system such as GitHub, Postgres, Sentry, or Slack. |
| Worktree | An isolated git checkout, so parallel sessions and subagents don't collide on the same files. |

---

## 11. Permission Modes

Cycle modes with `Shift+Tab` in the CLI, or use the mode selector in VS Code, Desktop, and claude.ai. This is the main dial for how much Claude does before pausing to ask.

| Mode | Flag value | Runs without asking | Best for |
|---|---|---|---|
| Manual | `default` | Reads only | Getting started, sensitive work |
| Accept Edits | `acceptEdits` | Reads, file edits, common filesystem commands | Iterating on work you're reviewing |
| Plan | `plan` | Reads and research; edits blocked until you approve a plan | Exploring before changing anything |
| Auto | `auto` | Everything, with a background classifier checking risky actions | Long tasks, cutting prompt fatigue |
| Don't Ask | `dontAsk` | Only pre-approved tools; everything else denied | Locked-down CI and scripts |
| Bypass | `bypassPermissions` | Everything, no checks at all | Isolated containers and VMs only |

**Set the starting mode from the CLI:**
```bash
claude --permission-mode plan
claude --dangerously-skip-permissions   # shorthand for bypassPermissions
```
The flag overrides `defaultMode` in settings for that session. To let a session switch into Bypass later, via `Shift+Tab`, without starting there, add `--allow-dangerously-skip-permissions`.

**Fine-grained rules: allow / ask / deny**

Modes set the baseline. Rules handle the exceptions. Rules live in `settings.json` as three arrays. Every incoming tool call gets checked deny, then ask, then allow. First match wins. A more specific allow rule can't override a matching deny.

```json
{
  "permissions": {
    "defaultMode": "default",
    "allow": [
      "Bash(git diff:*)",
      "Bash(npm run lint:*)",
      "Read(./**)"
    ],
    "ask": [
      "Bash(git push:*)",
      "Bash(gh pr merge:*)"
    ],
    "deny": [
      "Bash(rm -rf:*)",
      "Bash(curl:*)",
      "Read(./.env)",
      "Read(./.env.*)"
    ]
  }
}
```

- Syntax is `Tool(specifier)`. A bare tool name matches every use of it. A scoped pattern like `Bash(npm run lint:*)` matches only that command prefix.
- File locations, in ascending precedence for the same key (though allow/deny lists across levels merge rather than replace):
  - `~/.claude/settings.json`: your personal defaults, every project
  - `.claude/settings.json`: project-wide, checked into the repo
  - `.claude/settings.local.json`: your machine-only overrides, gitignored by default
  - Managed/enterprise policy: set by an admin, always wins
- A deny rule at any level survives an allow rule at another. A team-wide `Bash(rm -rf:*)` deny stands even if a project file tries to allow it.

> **Tip:** Auto mode becomes the default for new sessions on Pro, Max, and Team plans from 14 Aug 2026. Its classifier still blocks risky actions by default: piping downloads into a shell, force pushes, production deploys, anything that would send secrets outside the repo. Your own deny rules stack on top of that.

---

## 12. CLI Flags Reference

The commands below cover a session in progress. These flags shape how a session starts, for scripting, CI, and shortcuts worth knowing by heart. Run `claude --help` for the full list; it's long, and not every flag appears there.

**Sessions & models**

| Flag | Does |
|---|---|
| `-c`, `--continue` | Reopen the most recent conversation in this folder |
| `-r`, `--resume <id\|name>` | Resume a specific session, or show a picker if you omit the argument |
| `-n`, `--name <name>` | Name the session so it's easy to find in `/resume` later |
| `--fork-session` | Resume into a new session ID instead of continuing the original |
| `--model <name>` | Set the model: an alias like `sonnet`, `opus`, `haiku`, or a full model name |
| `--effort <level>` | How hard it thinks: `low`, `medium`, `high`, `xhigh`, or `max` |
| `-w`, `--worktree <name>` | Start in an isolated git worktree; pass a PR number or URL to branch from it |
| `--bg`, `--background` | Launch as a background agent and get your terminal back right away |

**Scripting & CI (print mode)**

| Flag | Does |
|---|---|
| `-p`, `--print <prompt>` | Run one-shot and exit. The workhorse for scripts and pipelines |
| `--output-format <fmt>` | `text`, `json`, or `stream-json`. Structured output includes cost and turn count |
| `--max-turns <n>` | Hard cap on agentic turns; exits with an error if it's hit |
| `--max-budget-usd <n>` | Stop once API spend for the session hits this dollar amount |
| `--input-format stream-json` | Feed structured input for programmatic multi-turn use |

```bash
claude -p "run the smoke tests and summarise failures" \
  --output-format json --max-turns 5 \
  --permission-mode bypassPermissions
```
Run `bypassPermissions` only inside something already sandboxed, a CI runner or container. Never on your own machine.

**Permissions & tool access**

| Flag | Does |
|---|---|
| `--permission-mode <mode>` | Start in a specific mode. See [section 11](#11-permission-modes) for values |
| `--dangerously-skip-permissions` | Shorthand for `--permission-mode bypassPermissions` |
| `--allowedTools "Read" "Bash(git diff *)"` | Extra allow rules for this session only |
| `--disallowedTools "Edit"` | Extra deny rules for this session only |
| `--tools "Bash,Edit,Read"` | Restrict which built-in tools exist at all for this session |
| `--add-dir <path>` | Grant read/edit access to folders outside the current one |

**Config & context**

| Flag | Does |
|---|---|
| `--settings <path\|json>` | Override settings.json values for this session only |
| `--mcp-config <file>` | Load MCP servers from a JSON file for this session |
| `--append-system-prompt <text>` | Add extra instructions on top of the default prompt |
| `--agent <name>` | Start the session as a specific custom subagent |
| `--verbose` | Full turn-by-turn output. Useful for debugging a prompt or hook |

> **Tip:** `claude --help` doesn't list every flag. The CLI reference at code.claude.com is the source of truth, and new flags ship between documentation updates.

---

## 13. Essential Slash Commands

| Command | Purpose |
|---|---|
| `/init` | Generate a starter CLAUDE.md for the folder |
| `/memory` | Edit CLAUDE.md files, and enable or review auto memory |
| `/plan` | Enter plan mode: research and propose before touching anything |
| `/model`, `/effort` | Switch model, or how much reasoning it applies |
| `/context` | Visualise what's filling the context window |
| `/compact` | Summarise the conversation to free up context |
| `/mcp` | Manage MCP server connections |
| `/permissions` | View and edit allow, ask, and deny rules |
| `/diff` | Interactive viewer for uncommitted changes |
| `/code-review` (`/review`) | Review the current diff or a PR; add `--fix` to apply findings |
| `/security-review` | Scan the current branch's diff for security vulnerabilities |
| `/rewind` (`/undo`, `/checkpoint`) | Roll files and/or conversation back to a checkpoint |
| `/clear`, `/resume` | Start fresh, or reopen an earlier conversation |
| `/branch`, `/fork` | Branch the conversation to try another direction, or copy it into a background session |
| `/background` (`/bg`) | Detach the session to run as a background agent |
| `/batch` | Split a large change into parallel subagent tasks, each in its own worktree |
| `/deep-research` | Fan out web searches, cross-check sources, synthesise a cited report |
| `/usage` (`/cost`) | Show usage and cost breakdown |
| `/doctor` | Setup checkup that diagnoses and can fix config problems |
| `/help` | List everything available to you |

Type `/` in a session to browse the full list. There are 80+ built-in commands, and which ones appear depends on your plan and platform.

---

## 14. CLAUDE.md & Memory

**CLAUDE.md**
- Loads automatically at session start. The single highest-leverage thing you can set up: conventions, context, and commands.
- Layer it per directory in a large folder tree, so each area carries its own instructions.
- Alternatives and companions:
  - `.claude/rules/` for path-scoped rule files, instead of one enormous CLAUDE.md
  - `AGENTS.md`, supported as a cross-tool alternative

**Auto memory**
- Claude saves durable facts it learns during a session, without you writing them down.
- Enable, disable, and review saved entries with `/memory`.

> **Tip:** if Claude isn't following your CLAUDE.md, check its size and specificity first. `/doctor` flags bloated or redundant memory files and can trim them.

---

## 15. MCP: Connecting External Tools

Model Context Protocol connects Claude to outside systems: databases, ticketing, monitoring, internal APIs, cloud storage. The same protocol powers connectors in Claude.ai and Artifacts.

```bash
claude mcp add <name> <command>                 # local stdio server
claude mcp add --transport http <name> <url>    # remote HTTP server
```

- Servers install at one of three scopes:
  - **Local:** you alone, scoped to this folder
  - **Project:** shared with the team through a checked-in `.mcp.json`
  - **User:** available across all your folders
- Common examples: GitHub for reviews and PRs, Postgres for querying a database, Sentry for errors, Slack, the Google connectors.
- MCP Tool Search lets Claude discover tools on demand instead of loading every definition upfront, which keeps context cost down when an org runs many servers.

---

## 16. Skills & Plugins

**Skills.** A reusable capability written as a markdown prompt plus optional scripts. Teach Claude a workflow once and reuse it forever.
- Where they live:
  - `.claude/skills/` for skills shared with a project
  - `~/.claude/skills/` for your personal ones, available everywhere
- How they run:
  - Invoked explicitly with `/skill-name args`
  - Or triggered automatically when Claude judges them relevant
  - Up to six can be chained in a single message
- Bundled skills ship with Claude Code. `/code-review`, `/batch`, `/deep-research`, `/doctor`, and `/security-review` are all skills rather than hard-coded commands.
- Skills also work inside the Claude for Excel and PowerPoint add-ins, so one definition serves both surfaces.

**Plugins.** A plugin packages skills, subagents, hooks, and MCP servers into a single installable unit, the right shape for anything a whole team should have.
- Distributed through marketplaces: the official Anthropic one, the community one, or a private marketplace you host yourself.
- Browse and install with `/plugin`. Add a team marketplace with `/plugin marketplace add`.
- Best for standardising house style, review checklists, and org-specific workflows, instead of asking everyone to configure the same thing by hand.

---

## 17. Subagents & Parallel Work

**Delegating inside a session**
- **Subagents.** Separate Claude instances with their own context window and tool restrictions. Use them to keep high-volume investigation out of the main conversation:
  - Isolate noisy operations that would otherwise fill your context
  - Run several lines of research at once and collect the findings
  - Give a task narrower tools than the main session has
- **Agent Teams.** Multiple Claude teammates on a shared goal, each with a role, that you can message directly, steer, and monitor.

**Running work in parallel**
- **Worktrees.** Isolated git checkouts, so parallel sessions and subagents never collide on the same files.
- **`/batch`.** For changes that span everything: researches the folder, splits the work into 5 to 30 independent units, runs each in its own subagent and worktree, opens a pull request per unit.
- **Background agents.** `/background` detaches a session so it keeps running while you do something else. `claude agents` monitors everything in flight.

---

## 18. Hooks & Automation

Hooks are scripts that fire at lifecycle events. They enforce a team standard without relying on Claude remembering to follow it.

| Hook event | Typical use |
|---|---|
| PreToolUse | Block edits to protected files, or apply custom approval logic |
| PostToolUse | Auto-format or lint after every edit |
| UserPromptSubmit | Inject extra context before Claude responds |
| SessionStart | Reload environment variables, or re-inject context after compaction |
| Stop / SubagentStop | Write an audit trail, or enforce a quality gate before finishing |

**Keeping work running**
- **`/loop`.** Runs a prompt on an interval while the session stays open.
- **`/schedule`.** Creates cloud-run routines triggered by a cron schedule, an API call, or a GitHub event. Cowork has its own scheduled tasks for knowledge work.
- **`/goal`.** Keeps Claude working across turns until a condition you define is met.

---

## 19. Checkpoints, Sandboxing & Security

**Undo and recovery**
- **Checkpoints.** Snapshots after each turn. In the CLI, `/rewind` restores files, the conversation, or both. In the extension, hover any message for the same three options: fork the conversation, rewind the code, or both.
- Useful, but not a replacement for version control. Bash-driven changes and subagent edits aren't always captured.

**Isolation**
- **Sandboxing.** An OS-level sandbox isolates filesystem and network access for shell commands, so fewer actions need your approval. Cowork tasks run in an isolated VM on the same principle.
- **Protected paths.** `.git`, `.claude`, shell rc files, and similar are never auto-approved for writes outside Bypass mode, even if an allow rule matches.

**Prompt injection**
- In Auto mode, the safety classifier reads your messages and CLAUDE.md, but tool results get stripped before it decides. Hostile content in a file or web page can't steer it directly.
- A separate server-side probe scans incoming tool results and flags suspicious content before Claude reads it.
- Boundaries you state in conversation, "don't push," "wait until I review," count as block signals until you lift them. For a hard guarantee, use a deny rule instead.

---

## 20. CLI vs. VS Code Extension

Both are the same Claude Code engine: same models, same CLAUDE.md, same hooks, skills, and MCP servers. The CLI is the full interface. The extension wraps it in a graphical panel with a few trade-offs worth knowing before you rely on one over the other.

| Feature | CLI | Extension |
|---|---|---|
| Commands & skills | All | Subset (type `/` to see what's available) |
| MCP server config | Full | Partial: add servers via CLI, manage existing ones with `/mcp` in the panel |
| Checkpoints | Yes, `/rewind` | Yes, hover a message for a rewind button |
| `!` bash shortcut | Yes | No |
| Tab completion | Yes | No |
| Selection & open-file context | Via `/ide` or an integrated terminal | Automatic. Highlighted code and the open file are always visible to Claude |

> **Two separate installs, one shared history** (setup steps in [section 8](#8-install--first-session)). Whichever you install, run `claude --resume` in the terminal to pick up a conversation you started in the other one.

**Nuances worth knowing**
- **Selected code is automatic context in the extension.** Highlight a range and Claude sees it without an @-mention. Press `Option+K` (Mac) / `Alt+K` (Windows/Linux) to also insert an explicit `@file.ts#5-10` reference into your prompt.
- **The CLI needs a connection to get the same context.** Run it from VS Code's integrated terminal and it connects automatically. From an external terminal, run `/ide` to connect it to a running VS Code window.
- **Diagnostics and diffs share one path.** Whichever surface you're in, edits open in VS Code's native diff viewer and Claude can read the Problems panel. This runs through a local IDE connection the extension starts, not a public server.
- **Plugins stay in sync.** Type `/plugins` in the extension panel for a graphical install/manage view. It uses the same CLI commands underneath, so a plugin added in one surface shows up in the other.
- **Background/long-running commands are easier to watch in the CLI.** The extension shows progress in the status bar but with less detail. For a command you'll want to monitor closely, ask Claude to print it so you can run it yourself in the integrated terminal.
- **Terminal mode is one setting away.** Prefer the CLI's look and feel but want it inside the extension's panel anyway? Toggle `claudeCode.useTerminal` in VS Code settings.

---

## 21. Managing Cost & Context

**See where it's going**
- `/usage` shows your spend and plan limits. `/context` shows what's filling the window right now.
- Team and Enterprise plans get Analytics: adoption, PRs per user, top contributors.

**Bring it down**
- Keep CLAUDE.md lean and move detailed instructions into skills that load on demand.
- Delegate verbose investigation to subagents, so their output never enters your main context.
- Match the model and effort level to the task instead of defaulting to the largest.
- Use `/fast` for quick, cheaper responses on simple work.
- Expect agentic work to cost more than chat. Cowork and long Claude Code sessions both consume more than a standard conversation.

---

## 22. Build Your Own Skill (and Package It as a Plugin)

If you keep pasting the same instructions into chat, or a section of your CLAUDE.md has grown into its own procedure, that's a skill.

**The minimum a skill needs**

A folder with one file: `SKILL.md`. YAML frontmatter, then markdown instructions.

```
.claude/skills/pr-summary/
└── SKILL.md
```

```markdown
---
name: pr-summary
description: Summarise a pull request's changes and risk areas. Use when the user asks for a PR summary or a review starting point.
---

Read the diff for the current branch against main. Summarise:
1. What changed, grouped by area
2. Anything that touches auth, payments, or migrations
3. Missing test coverage for new logic

Keep the summary under 200 words.
```

- Project skills live in `.claude/skills/<name>/`, shared with the team. Personal ones live in `~/.claude/skills/<name>/`, available in every folder you work in.
- `name` and `description` are the only required fields. `description` is what Claude matches your prompt against, so name what the skill does and when to use it.
- Optional frontmatter: `allowed-tools` restricts what the skill can touch, `disable-model-invocation: true` means only you can trigger it (never Claude on its own), `user-invocable: false` hides it from the `/` menu while still letting Claude call it.
- Keep the body short. Once a skill loads, it stays in context for the rest of the session, so every line is a recurring cost.

**Testing it**

1. Run it directly: `/pr-summary`. Confirm the output matches what you wrote.
2. Check that it triggers on its own. Ask a question close to the trigger phrase in your description, without invoking the slash command, and see whether Claude reaches for it.
3. Write eval queries. A short JSON list of realistic prompts, some that should trigger the skill and some that shouldn't:
   ```json
   [
     {"query": "can you summarise this PR for me", "should_trigger": true},
     {"query": "what does this function do", "should_trigger": false}
   ]
   ```
4. Run `/doctor` if a skill won't fire. It flags description problems, like a budget overflow silently dropping keywords.
5. Iterate on the description, not the instructions, when triggering is the problem. The instructions only matter once the skill has already fired.

**Turning it into a plugin**

A plugin bundles one or more skills (plus agents, hooks, or MCP servers) into a single installable unit.

```
release-tools/
├── .claude-plugin/
│   └── plugin.json        # the ONLY file in this directory
├── skills/
│   └── pr-summary/
│       └── SKILL.md
├── agents/
├── hooks/
└── .mcp.json
```

```json
{
  "name": "release-tools",
  "version": "0.1.0",
  "description": "PR review helpers for the platform team",
  "author": { "name": "Your Name", "email": "you@example.com" }
}
```

Everything except `.claude-plugin/plugin.json` sits at the plugin root, not inside `.claude-plugin/`. Misplacing a component folder inside `.claude-plugin/` doesn't throw an error. The plugin loads, but the skill or hook silently doesn't appear.

Load it locally before publishing anywhere:
```bash
claude --plugin-dir ./release-tools
claude plugin validate ./release-tools
```
`claude plugin validate` checks the manifest, frontmatter fields, and directory layout, and catches the misplaced-folder mistake before your team hits it.

---

## 23. Host Your Own Marketplace

A marketplace is a git repository with a manifest listing your plugins. Nothing to install, nothing to host beyond the repo itself.

**What it needs**

One file at the repository root: `.claude-plugin/marketplace.json`.

```json
{
  "name": "acme-plugins",
  "owner": { "name": "Acme Platform Team" },
  "plugins": [
    {
      "name": "release-tools",
      "source": "./release-tools",
      "description": "PR review helpers for the platform team"
    }
  ]
}
```

- `source` can point inside the same repo (`./release-tools`), or to a different repository entirely, pinned by `ref` (a branch or tag) or `sha` (an exact commit). The marketplace repo and a plugin's source repo are pinned independently.
- Host the repo anywhere with git: GitHub, GitLab, Bitbucket, or self-hosted. Private repos work the same way, using your normal git credentials. If `git clone` works in your terminal, it works for Claude Code too.

**Publishing and installing**

```bash
# team members add your marketplace once
/plugin marketplace add your-org/acme-plugins

# then install from it
/plugin install release-tools@acme-plugins
```

`/plugin` opens a menu to browse what's installed and enable, disable, or remove plugins, without touching the terminal.

**Before you share it**

Run the validator against the whole repo, and check the two most common failure modes: a component folder placed inside `.claude-plugin/` instead of at the plugin root, and a marketplace with no plugins listed yet.

```bash
claude plugin validate .
```

**Keeping it current**

Team members can turn on auto-update per marketplace: `/plugin` → Marketplaces tab → enable Auto-update. Or set it directly in `settings.json`:

```json
{
  "extraKnownMarketplaces": [
    { "url": "https://github.com/your-org/acme-plugins", "autoUpdate": true }
  ]
}
```

For a private marketplace pulled in CI, export a token with read access as `GH_TOKEN` and run `gh auth setup-git` first. The default GitHub Actions token only reaches the workflow's own repository.

---

## 24. Where to Start, by Role

**Knowledge workers**
- Start with Projects and Artifacts for anything recurring, and Cowork for multi-step tasks you'd rather hand off.
- Living in Excel, PowerPoint, or Word day to day? Install the Microsoft 365 add-ins and turn on cross-app context.
- Want to watch and steer the work instead of handing it over? Open Claude Code in the folder.

**Engineers**
- Run `/init` in your main repos to establish a baseline CLAUDE.md.
- Agree a default permission mode per repo type: Plan for exploration, Accept Edits for trusted iteration.
- Make `/code-review` and `/security-review` a habit before every PR.
- For migrations and repo-wide changes, reach for `/batch` instead of working through it one file at a time.

**Whoever owns the setup**
- Standardise shared MCP servers at **project scope** through a checked-in `.mcp.json`.
- Package house style and review checklists as a shared plugin or skill. One definition works in both Claude Code and the Office add-ins.
- Decide the org position on Auto mode and Bypass mode before the 14 Aug 2026 default change, not after.

---

