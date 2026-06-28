# Week 2 - Day 2: Claude Code Commands & Workflow

## Overview

* Focus on using **Claude Code** more effectively through built-in commands and workflow improvements.
* Learn how to manage projects, context, permissions, and memory efficiently.
* Explore productivity shortcuts and best practices for long coding sessions.

---

# AI Coding Agent Landscape

## Categories of AI Coding Tools

* **IDEs**

  * Cursor
  * Antigravity
  * Windsurf

* **Editor Plugins**

  * GitHub Copilot
  * Codex (VS Code extension)

* **CLI (Command Line) Tools**

  * Claude Code
  * Cursor CLI
  * Codex CLI
  * Gemini CLI
  * Antigravity (CLI for Gemini models)

## Key Takeaways

* Most AI coding tools share similar concepts and workflows.
* CLI-based tools typically use **slash (`/`) commands**.
* AI coding tools evolve rapidly, so features and capabilities change frequently.
* Claude Code is presented as the preferred long-term CLI coding assistant.

---

# Starting Claude Code

* Launch Claude Code from the terminal.
* Start with a **fresh terminal session** to avoid leftover environment variables.
* Most commands begin with a **forward slash (`/`)**.

Example:

```text
claude
```

---

# Discovering Available Commands

## View All Commands

* Press the **Down Arrow** after typing `/`
* Browse all available commands with descriptions.

## Help Command

```text
/help
```

Displays:

* Available commands
* Keyboard shortcuts
* General usage information

---

# Common Claude Code Commands

## `/init`

Purpose:

* Initializes a project.
* Creates a new `CLAUDE.md` file.

Notes:

* Useful for first-time setup.
* Alternatively, `CLAUDE.md` can be created manually for greater control.

---

## `/model`

Purpose:

* View the currently selected AI model.
* Switch between available models.

Example:

* Opus
* Other Claude models depending on subscription.

---

## `/status`

Displays:

* Claude Code version
* Current settings
* Session usage
* Weekly usage

Useful for:

* Monitoring configuration and resource consumption.

---

## `/context`

Purpose:

* Displays the current conversation/context memory.
* Helps monitor how much context has accumulated.

Benefits:

* Understand what Claude currently remembers.
* Frequently used during long coding sessions.

---

## `/compact`

Purpose:

* Compresses conversation history into a summary.
* Frees context space while preserving important information.

Benefits:

* Prevents context from becoming too large.
* Improves stability during long sessions.

Can include custom summarization instructions:

```text
/compact Keep project architecture and API decisions.
```

Best Practice:

* Compact manually before context becomes excessively large.

---

## `/clear`

Purpose:

* Completely removes conversation history.
* Starts a fresh Claude session.

Effects:

* Similar to exiting Claude and reopening it.
* Claude reloads instructions from `CLAUDE.md`.

Best Use Cases:

* Begin a completely new task.
* Reset after a long or confusing conversation.
* Maintain a clean workflow.

---

## `/config`

Displays:

* Claude configuration settings.
* Similar information available through the Status screen.

---

## `/usage`

Displays:

* Usage statistics
* Token consumption
* Resource tracking

---

## `/stats`

Provides:

* Visual usage graphs
* Daily token usage
* Model usage history

Useful for:

* Tracking long-term Claude Code usage.

---

# Keyboard Shortcuts

## Shift + Tab

Toggles:

### Accept Edits Mode

* Automatically accepts file edits.

### Plan Mode

* Encourages Claude to plan before editing.

Notes:

* Modern Claude models often decide automatically when planning is beneficial.
* Manual Plan Mode is less necessary than before.

---

## Ctrl + O

Toggles:

**Detailed Transcript Mode**

Shows:

* More internal execution details
* Expanded operation logs

Useful when:

* Debugging
* Understanding Claude's reasoning process
* Inspecting detailed operations

---

# Claude Configuration Folder

Claude automatically creates:

```text
.claude/
```

Contains:

* Configuration files
* Permission settings
* Internal Claude data

---

# Permissions Management

Permissions are stored in:

```text
.claude/settings.json
```

Whenever permanent permission is granted:

* Claude records it in this JSON file.

Permissions can be managed by:

* Editing the JSON directly
* Using the built-in command

```text
/permissions
```

Capabilities:

* View permissions
* Add rules
* Remove rules
* Modify allowed actions

---

# Using `@` File References

Claude supports referencing files using the `@` syntax.

Example:

```text
@docs/plan.md
```

Purpose:

* Inserts file contents into the current context.

Common use:

* Include project documentation.
* Reference specifications.
* Share implementation plans.

---

# Referencing Files Inside `CLAUDE.md`

Example:

```markdown
# Detailed Plan

@docs/plan.md
```

Result:

* The contents of `plan.md` become part of Claude's instructions.

Benefits:

* Keeps `CLAUDE.md` small.
* Separates documentation into multiple files.

---

# Sharing Instructions Between AI Tools

Useful pattern:

Instead of duplicating instructions:

```text
CLAUDE.md
AGENTS.md
```

Use:

```markdown
@AGENTS.md
```

Benefits:

* Maintain a single source of truth.
* Both Claude Code and GitHub Copilot can reference the same instructions.
* Easier maintenance.

---

# Using `@` Inside Prompts

Example:

```text
Explain the architecture using @docs/architecture.md
```

Claude loads that file into context.

Important:

* Large files consume significant context.
* Use selectively to avoid filling the context window.

---

# Referencing Directories

Using:

```text
@docs/
```

Behavior:

* Includes only the directory listing.
* Does **not** automatically load every file.

Useful for:

* Showing project structure without consuming excessive context.

---

# Recommended Workflow

* Start with a clean Claude session.
* Initialize the project if needed.
* Monitor context regularly with `/context`.
* Compact conversations before context becomes too large.
* Use `/clear` when starting a completely different task.
* Organize long instructions into external Markdown files.
* Use `@` references instead of duplicating documentation.
* Keep `CLAUDE.md` concise by referencing other files.
* Review permissions periodically through `/permissions` or `.claude/settings.json`.
* Use keyboard shortcuts to speed up common tasks.

---

# Key Concepts to Remember

* Slash (`/`) commands control Claude Code itself rather than sending prompts to the model.
* Context management is essential for long-running coding sessions.
* `CLAUDE.md` serves as persistent project guidance.
* `@` references allow modular documentation and reusable project instructions.
* The `.claude` folder stores configuration and permission settings.
* Keyboard shortcuts improve productivity during development.
