# Week 2 - Day 2: Claude Code Commands & Workflow

> **Topic:** Learning Claude Code commands, context management, shortcuts, permissions, and project organization for efficient AI-assisted development.

---

# Overview

This session focuses on becoming more productive with **Claude Code** by learning its built-in commands, understanding how Claude manages context and memory, and organizing projects so that Claude performs consistently over long coding sessions.

Rather than focusing on writing prompts, the emphasis is on learning the tools that surround Claude Code—commands, shortcuts, project configuration, permissions, and context management.

---

# Recap: AI Coding Agent Landscape

AI coding assistants can generally be grouped into three categories.

## 1. IDEs (Integrated Development Environments)

These provide a complete coding environment with AI built directly into the editor.

Examples include:

* Cursor
* Antigravity
* Windsurf

These tools combine editing, AI assistance, and project management into one interface.

---

## 2. Editor Plugins

These extend an existing editor (such as VS Code) with AI capabilities.

Examples include:

* GitHub Copilot
* Codex

**Note**

Although Codex was previously categorized as an IDE, it is actually a **VS Code extension/plugin**.

---

## 3. Command Line Interface (CLI) Agents

These operate directly from the terminal and interact with your project through command-line commands.

Examples include:

* Claude Code
* Cursor CLI
* Codex CLI
* Gemini CLI
* Antigravity (Gemini-based CLI)

---

# Claude Code's Position

The session primarily focuses on **Claude Code** because it provides a mature command-line workflow for AI-assisted programming.

Although many competing tools now exist, much of their functionality is shared:

* Slash commands
* Context management
* Project instruction files
* Planning workflows
* Permission systems

Learning Claude Code makes it easier to use other coding agents because the underlying concepts are similar.

---

# Rapidly Evolving Ecosystem

The AI coding landscape changes very quickly.

New tools, features, and command-line interfaces are released frequently.

Examples mentioned include:

* Gemini CLI
* Antigravity
* OpenCode
* AMP
* Cursor CLI
* Codex CLI

Because this ecosystem evolves rapidly:

* Documentation changes often.
* Features may move between products.
* Different tools may offer overlapping capabilities.
* Commands and workflows can evolve over time.

Many concepts learned in Claude Code also apply to these other tools.

---

# Beginning a Claude Code Session

Before starting Claude Code, it's useful to begin with a **fresh terminal session**.

This avoids carrying over:

* Environment variables
* Temporary shell configuration
* Previous experiments
* Session-specific settings

A clean terminal provides a predictable starting point.

### VS Code Shortcut

Open a completely new terminal:

```text
Ctrl + Shift + `
```

This is useful when switching projects or resetting your development environment.

---

# Launching Claude Code

Start Claude Code directly from the terminal.

```bash
claude
```

Once launched, Claude enters its interactive command mode.

Unlike normal prompts, commands beginning with a **forward slash (`/`)** are interpreted by Claude Code itself rather than being sent to the AI model.

---

# Understanding Slash Commands

Claude Code distinguishes between:

### Normal Prompt

Sent to Claude for reasoning.

Example:

```text
Refactor this authentication module.
```

---

### Slash Command

Executed by Claude Code itself.

Example:

```text
/status
```

Slash commands control:

* Configuration
* Context
* Models
* Permissions
* Session management
* Statistics
* Project initialization

Think of slash commands as administrative commands for Claude Code.

---

# Discovering Available Commands

One of the easiest ways to learn Claude Code is by browsing its built-in commands.

## Method 1: Down Arrow

Inside Claude Code:

1. Type:

```text
/
```

2. Press the **Down Arrow**.

Claude displays:

* Every available command
* A short description of each command
* What each command is used for

This is often the quickest way to discover features.

---

## Method 2: `/help`

```text
/help
```

Displays:

* Common commands
* Important keyboard shortcuts
* Helpful usage information
* Navigation tips

Whenever you're unsure about available functionality, `/help` is a good starting point.

---

# Project Initialization

## `/init`

```text
/init
```

Purpose:

* Initializes Claude Code for a new project.
* Creates a `CLAUDE.md` file.

---

## What is `CLAUDE.md`?

`CLAUDE.md` is the primary instruction file for your project.

It stores long-term guidance that Claude should follow whenever working inside the project.

Typical contents include:

* Coding standards
* Project architecture
* Development workflow
* Team conventions
* Documentation references

Rather than repeating instructions every session, they can be stored here.

---

## Manual vs Automatic Initialization

Running:

```text
/init
```

automatically creates the initial `CLAUDE.md`.

However, another valid approach is to create and maintain `CLAUDE.md` manually.

Advantages of manual management:

* Greater control over contents.
* Cleaner project organization.
* Ability to structure instructions exactly as desired.

Both approaches are valid.

---

# Selecting AI Models

## `/model`

```text
/model
```

Purpose:

* Shows the currently selected Claude model.
* Allows switching between available models.

Depending on your subscription, different models may be available.

Example:

* Opus

The session demonstrates Opus being used because it provides the highest capability.

---

# Viewing Session Information

## `/status`

```text
/status
```

Displays information about the current Claude session.

This includes:

* Claude Code version
* Active configuration
* Current settings
* Session usage
* Weekly usage

This command provides a quick overview of the current environment.

---

## When to Use `/status`

Useful for checking:

* Which version is running.
* Which settings are active.
* Current resource consumption.
* Weekly usage limits.

---

# Configuration Information

## `/config`

```text
/config
```

Displays configuration information.

Much of this overlaps with the configuration page shown through `/status`.

Useful for reviewing current settings without navigating through multiple status screens.

---

# Usage Information

## `/usage`

```text
/usage
```

Displays resource usage information.

This includes:

* Session usage
* Token usage
* Consumption statistics

Useful for understanding how heavily Claude has been used.

---

# Usage Statistics

## `/stats`

```text
/stats
```

Provides a graphical overview of Claude usage.

Information includes:

* Daily usage
* Token consumption
* Model usage history
* Historical activity

Unlike `/usage`, which focuses on current consumption, `/stats` provides a broader historical view.

This makes it useful for tracking long-term usage patterns.

---

# Difference Between Status Commands

| Command   | Purpose                                |
| --------- | -------------------------------------- |
| `/status` | Overall session information            |
| `/config` | Configuration settings                 |
| `/usage`  | Current usage and token consumption    |
| `/stats`  | Historical graphs and usage statistics |

---

# Key Takeaways

* Claude Code is a terminal-based AI coding assistant.
* Slash commands configure Claude Code rather than interacting with the AI model.
* A fresh terminal helps avoid carrying over unwanted environment state.
* `/help` and the Down Arrow menu are the easiest ways to discover available commands.
* `/init` creates a project-level `CLAUDE.md` instruction file.
* `CLAUDE.md` acts as persistent project guidance.
* `/model` manages which Claude model is active.
* `/status`, `/config`, `/usage`, and `/stats` each provide different views into the current session and resource usage.

---
Great! This is the core of the lesson. The instructor spends a lot of time here explaining **how to manage Claude's context**, and these practices are what distinguish experienced Claude Code users from beginners.

---

# Week 2 - Day 2: Claude Code Commands & Workflow (Part 2)

# Context Management

One of the most important concepts in Claude Code is **context management**.

Every conversation with Claude consumes part of the model's available context window (memory). As conversations become longer, more tokens are used to store previous prompts, responses, tool calls, and file contents.

Managing this context properly helps Claude:

* Stay focused on the current task.
* Produce more consistent answers.
* Reduce unnecessary token usage.
* Avoid confusion caused by old or irrelevant conversation history.

This session emphasizes that **good context management is an essential skill** when using Claude Code for long-running development projects.

---

# Viewing Current Context

## `/context`

```text
/context
```

Purpose:

* Displays the current conversation context.
* Shows how much of Claude's available memory has been consumed.
* Helps determine when context should be compacted or reset.

---

## Why Check Context Frequently?

The instructor recommends checking context regularly.

Reasons include:

* Understanding how much information Claude currently remembers.
* Monitoring context growth during long coding sessions.
* Deciding when it is appropriate to compact or restart the conversation.

Rather than waiting until Claude's memory becomes full, it is better to monitor it throughout development.

---

## What the Context Screen Represents

The context display provides a "memory snapshot" of the current session.

It effectively answers the question:

> **"How much information is Claude currently carrying?"**

Starting a new Claude session results in a nearly empty context display.

This makes it easy to verify that the session has been reset successfully.

---

# Compacting Context

## `/compact`

```text
/compact
```

Purpose:

* Compresses the current conversation into a summary.
* Frees context space.
* Preserves important information while removing unnecessary conversational detail.

Instead of deleting conversation history completely, Claude creates a summarized version that it can continue working from.

---

# Why Compact?

As conversations grow longer:

* More tokens are consumed.
* Context becomes crowded.
* Performance may gradually decline.
* Older information occupies memory that could be used for new work.

Compacting solves this by replacing detailed conversation history with a concise summary.

---

# Manual Compacting vs Automatic Compacting

A key recommendation from the session is:

**Compact manually rather than waiting for Claude to do it automatically.**

---

## Why?

Automatic compacting may occur while Claude is actively working on a complex problem.

This can sometimes lead to:

* Reduced coherence.
* Loss of conversational momentum.
* Claude temporarily losing track of details.
* Less consistent reasoning.

Although automatic compacting generally works well, choosing **when** to compact gives you more control over the session.

---

## Recommended Workflow

Instead of allowing the context to become dangerously full:

1. Monitor context using `/context`.
2. Compact before memory becomes excessive.
3. Continue working with a cleaner context.

This proactive approach helps maintain smoother conversations.

---

# Custom Compact Instructions

The compact command accepts additional instructions.

Example:

```text
/compact Keep architecture decisions and unfinished tasks.
```

These instructions tell Claude what information should receive priority during summarization.

Examples include:

* Project architecture.
* API design decisions.
* Coding conventions.
* Outstanding bugs.
* Future work.

---

# Alternative Philosophy

The instructor also discusses a different workflow preference.

Rather than relying heavily on conversation summaries, important project knowledge can instead be stored inside `CLAUDE.md`.

Advantages include:

* Persistent instructions survive every new session.
* Less dependence on compact summaries.
* Greater manual control over Claude's long-term memory.

This approach treats `CLAUDE.md` as the primary source of project knowledge.

---

# Clearing Conversation History

## `/clear`

```text
/clear
```

Purpose:

* Completely removes conversation history.
* Starts a fresh Claude session.
* Reloads instructions from `CLAUDE.md`.

Unlike `/compact`, nothing from the previous conversation remains.

---

# Effect of `/clear`

Using `/clear` is similar to:

* Exiting Claude.
* Launching Claude again.
* Starting a brand-new conversation.

The project remains the same, but the conversation memory is erased.

---

# What Happens After Clearing?

After using `/clear`:

* Claude rereads `CLAUDE.md`.
* Previous conversation history disappears.
* Context becomes clean again.
* The project instructions remain available.

This creates a fresh starting point without losing project guidance.

---

# Alternative Way to Reset

Instead of using:

```text
/clear
```

the instructor often exits Claude completely.

Keyboard shortcut:

```text
Ctrl + C
Ctrl + C
```

Then simply restart Claude.

```bash
claude
```

This produces essentially the same result as `/clear`.

---

# Verifying the Reset

After restarting Claude, it is good practice to run:

```text
/context
```

The context display should now be almost empty.

Seeing an empty context confirms that the conversation history has been successfully reset.

---

# Compact vs Clear

These commands serve different purposes.

## `/compact`

* Keeps the current conversation.
* Summarizes previous messages.
* Preserves important information.
* Frees memory.
* Allows work to continue immediately.

---

## `/clear`

* Removes all conversation history.
* Starts a completely fresh conversation.
* Reloads instructions from `CLAUDE.md`.
* Useful when changing tasks or wanting a clean slate.

---

# Which Should You Use?

Use **`/compact`** when:

* Working on the same project.
* Context is becoming large.
* You want to preserve progress.

Use **`/clear`** when:

* Starting a different task.
* The conversation has become confusing.
* Claude appears distracted by previous discussions.
* You want to begin from a completely clean context.

---

# Maintaining `CLAUDE.md`

A recurring theme throughout the session is keeping `CLAUDE.md` current.

As the project evolves:

* Update project documentation.
* Record architectural decisions.
* Keep coding conventions current.
* Store important long-term knowledge.

Doing so allows Claude to reconstruct project understanding whenever a fresh session begins.

---

# Suggested Daily Workflow

A productive workflow might look like:

1. Start Claude.
2. Verify project instructions.
3. Work normally.
4. Monitor context using `/context`.
5. Compact manually when appropriate.
6. Update `CLAUDE.md` with important project knowledge.
7. Restart or clear Claude when beginning unrelated work.
8. Verify the fresh context before continuing.

---

# Context Management Philosophy

One of the biggest lessons from this session is that **effective Claude Code usage is less about writing perfect prompts and more about managing context well.**

Good context management results in:

* Better reasoning.
* More predictable behavior.
* Cleaner conversations.
* Reduced token waste.
* Higher-quality coding assistance.

---

# Practical Tips

* Check `/context` regularly.
* Compact **before** the context becomes too large.
* Prefer manual compacting over automatic compacting.
* Store long-term project information in `CLAUDE.md`.
* Restart Claude when switching to unrelated work.
* Confirm a clean session by checking `/context`.
* Think of conversation history as temporary, and `CLAUDE.md` as the permanent knowledge base for the project.

---

# Key Takeaways

* `/context` lets you inspect Claude's current memory usage.
* `/compact` summarizes conversation history while preserving important information.
* Manual compacting provides greater control than waiting for automatic compaction.
* `/clear` removes conversation history entirely and starts a fresh session.
* `CLAUDE.md` should contain long-term project knowledge rather than relying solely on conversational memory.
* Managing context effectively is one of the most important skills when using Claude Code for long-running software projects.

---
Excellent. This part covers the operational features of Claude Code that are easy to overlook but become extremely useful in day-to-day development. I've kept all of the information from the transcript and expanded the explanations so this can serve as a long-term reference.

---

# Week 2 - Day 2: Claude Code Commands & Workflow (Part 3)

# Keyboard Shortcuts

Claude Code includes several keyboard shortcuts that make common tasks faster. While you don't need to memorize them immediately, they become valuable as you use Claude Code more frequently.

---

# Accept Edits Mode & Plan Mode

## `Shift + Tab`

Pressing **Shift + Tab** toggles between different working modes.

Depending on the current state, it switches between:

* Accept Edits Mode
* Plan Mode
* Normal Mode

The exact behavior depends on which mode is currently active.

---

# Accept Edits Mode

When **Accept Edits Mode** is enabled:

* Claude automatically accepts file edits.
* Fewer confirmation prompts appear.
* Development becomes faster because you don't need to approve every modification.

This is especially useful when working on trusted changes across multiple files.

---

## Benefits

* Faster editing workflow.
* Less interruption.
* Smoother iteration during development.
* Reduced need for repeated confirmations.

---

## Important Distinction

Accept Edits Mode **is not the same as YOLO Mode**.

The session specifically points out this distinction.

Accept Edits Mode:

* Automatically accepts file edits.

YOLO Mode:

* Grants much broader automatic permissions.
* Will be covered separately in a later lesson.

Although they both reduce confirmations, they serve different purposes.

---

# Plan Mode

Another state available through **Shift + Tab** is **Plan Mode**.

Instead of immediately editing files, Claude first attempts to:

1. Understand the task.
2. Develop a solution.
3. Produce a plan.
4. Execute the implementation.

This encourages more deliberate reasoning before making changes.

---

## Historical Importance

Earlier versions of Claude Code relied more heavily on Plan Mode.

It was often useful to explicitly tell Claude:

* Think first.
* Plan the implementation.
* Execute afterwards.

---

## Modern Behavior

The instructor notes that modern Claude models—particularly **Opus**—are much better at deciding for themselves when planning is beneficial.

As a result:

* Manual Plan Mode is needed less frequently.
* Claude often performs planning automatically when appropriate.
* Explicitly forcing Plan Mode is no longer as important as it once was.

---

# Returning to Normal Mode

Pressing **Shift + Tab** again returns Claude to its standard operating mode.

This allows you to move freely between planning, editing, and normal interaction.

---

# Detailed Transcript Mode

## `Ctrl + O`

Another useful shortcut is:

```text
Ctrl + O
```

This toggles **Detailed Transcript Mode**.

Pressing it again turns the feature off.

---

# Purpose

Detailed Transcript Mode displays considerably more information about Claude's internal operations.

Instead of only showing the final result, Claude exposes much more of what happens while completing a request.

---

# Information Displayed

When enabled, you may see additional details such as:

* Tool execution.
* Intermediate operations.
* Internal processing steps.
* More verbose output.
* Expanded execution logs.

The transcript refers to this as seeing the "gory detail" of what Claude is doing.

---

# When to Use It

Detailed Transcript Mode is especially useful when:

* Learning how Claude Code works.
* Debugging unexpected behavior.
* Understanding why Claude chose a particular solution.
* Watching tool execution in greater detail.

For routine coding tasks, many users prefer leaving it disabled because the additional output can become noisy.

---

# The `.claude` Directory

As Claude Code is used within a project, it automatically creates a hidden directory.

```text
.claude/
```

This directory stores Claude-specific project information.

Rather than placing everything in the project root, Claude keeps its configuration organized here.

---

# Contents of `.claude`

One important file mentioned in the session is:

```text
.claude/settings.json
```

This file stores various Claude configuration settings, including permission rules.

---

# Permission System

Claude protects your system by requesting approval before performing certain actions.

Examples include:

* Executing commands.
* Modifying files.
* Performing operations that require elevated trust.

When permission is requested, several choices are available.

One common option is:

> **Allow this action again**

Choosing this means Claude will remember the permission in future.

---

# Automatic Permission Storage

Whenever permanent permission is granted, Claude automatically records it inside:

```text
.claude/settings.json
```

A new permission entry is added to the JSON configuration.

The next time Claude attempts the same action, it can perform it without asking again.

---

# Viewing Stored Permissions

Because permissions are stored in a normal JSON file, they are completely visible.

You can inspect:

* Which permissions exist.
* What operations are allowed.
* How Claude has been configured.

This makes permission handling transparent rather than hidden.

---

# Editing Permissions Manually

Permissions do not have to be managed exclusively through prompts.

You can directly edit:

```text
.claude/settings.json
```

Possible actions include:

* Adding permissions.
* Removing permissions.
* Modifying existing permission rules.

This gives full manual control over Claude's behavior.

---

# Removing Permissions

If Claude has previously been granted a permission that is no longer desired:

Simply remove the corresponding entry from:

```text
.claude/settings.json
```

The next time Claude attempts that operation, it will request permission again.

---

# Permission Management Command

Claude also provides a dedicated command for managing permissions.

```text
/permissions
```

This command allows you to:

* View current permissions.
* Add new permission rules.
* Remove existing rules.
* Review what Claude is allowed to do.

For many users, this is more convenient than editing JSON manually.

---

# Manual Editing vs `/permissions`

Both approaches accomplish the same goal.

### `/permissions`

Advantages:

* User-friendly.
* No need to edit configuration files.
* Safer for beginners.

---

### Editing `settings.json`

Advantages:

* Faster for experienced users.
* Complete control.
* Easy to review all permissions at once.

The instructor notes that either approach is perfectly acceptable.

---

# Practical Permission Workflow

A common workflow looks like this:

1. Claude requests permission.
2. Decide whether the action should be allowed.
3. If it will be needed repeatedly, choose **Allow Again**.
4. Claude records the permission automatically.
5. Future executions proceed without prompting.

If circumstances change later:

* Open `settings.json`.
* Remove the permission.
* Claude will begin asking again.

---

# Transparency of Claude's Configuration

One useful aspect of Claude Code is that many of its behaviors are visible through project files.

Rather than hiding configuration internally:

* Settings are stored in files.
* Permissions can be inspected.
* Configuration can be edited.
* Developers maintain control over how Claude operates.

This aligns well with normal software development practices, where configuration is explicit and version-controlled if desired.

---

# Best Practices

* Learn the keyboard shortcuts gradually—they become more valuable with experience.
* Use Accept Edits Mode when you are comfortable allowing Claude to modify files without repeated confirmations.
* Remember that Accept Edits Mode is **not** the same as YOLO Mode.
* Allow permanent permissions only for actions you trust Claude to perform repeatedly.
* Review `.claude/settings.json` periodically to understand what permissions have accumulated.
* Use `/permissions` if you prefer a built-in interface instead of editing JSON files directly.
* Remove permissions that are no longer appropriate or necessary.

---

# Key Takeaways

* **Shift + Tab** cycles between editing and planning modes.
* Accept Edits Mode speeds up development by reducing confirmation prompts for file changes.
* Plan Mode encourages Claude to reason before editing, although modern models often do this automatically.
* **Ctrl + O** toggles Detailed Transcript Mode, exposing more information about Claude's internal operations.
* Claude stores project-specific configuration inside the hidden `.claude` directory.
* Permanent permissions are recorded automatically in `.claude/settings.json`.
* Permissions can be managed either through the `/permissions` command or by editing the JSON file directly.
* Claude's configuration is transparent and developer-controlled, making it easy to inspect, modify, and maintain.

---

Perfect. This is the final part of the README. The instructor spends the rest of the lesson explaining one of Claude Code's most useful features—**`@` references**—along with project organization techniques and workflow recommendations. I've preserved everything from the transcript and expanded the explanations so this serves as a complete reference.

---

# Week 2 - Day 2: Claude Code Commands & Workflow (Part 4)

# Using `@` References

One of Claude Code's most powerful features is the **`@` reference syntax**.

Instead of copying and pasting the contents of a file into a prompt, Claude can load the contents directly into its context.

This keeps prompts shorter while allowing Claude to work with project documentation, specifications, plans, and other files.

---

# Basic Syntax

Reference a file by typing:

```text
@path/to/file.md
```

Example:

```text
@docs/plan.md
```

Claude reads the contents of that file and includes them in the current context.

---

# What Happens Internally?

When a file is referenced:

* Claude locates the file.
* Reads its contents.
* Inserts the file contents into the current context.
* Uses that information while answering the prompt.

This is much more powerful than simply mentioning a filename because Claude actually has access to the file's contents.

---

# Using `@` Inside Prompts

The `@` syntax can be used directly inside a normal prompt.

Example:

```text
Review @docs/architecture.md and suggest improvements.
```

Claude will:

* Load the architecture document.
* Include it in the working context.
* Answer using the information from that file.

This avoids copying large documents into the prompt manually.

---

# Context Considerations

Every referenced file consumes part of Claude's available context window.

This is an important consideration.

### Small files

Usually safe to include.

Examples:

* Coding standards
* API guidelines
* TODO lists
* Small design notes

---

### Large files

Large documents may consume a significant amount of context.

Examples:

* Long specifications
* Large Markdown documentation
* Extensive logs
* Generated documentation

Using many large files together can quickly fill the context window.

---

# Best Practice

Only reference files that are relevant to the current task.

Avoid loading unnecessary documents simply because they exist.

Keeping the context focused generally produces better responses.

---

# Referencing Files Inside `CLAUDE.md`

The `@` syntax is not limited to prompts.

It can also be used inside `CLAUDE.md`.

Example:

```markdown
# Detailed Plan

@docs/plan.md
```

When Claude loads `CLAUDE.md`, it also loads the referenced file.

This allows project instructions to be split across multiple documents while still being available to Claude.

---

# Why Use References Instead of One Large File?

As projects grow, a single `CLAUDE.md` can become difficult to maintain.

Using references allows documentation to be organized into separate files.

Benefits include:

* Cleaner organization.
* Easier maintenance.
* Smaller primary instruction file.
* Better separation of concerns.
* Simpler updates.

---

# Example Project Structure

```text
project/
│
├── CLAUDE.md
│
├── docs/
│   ├── architecture.md
│   ├── plan.md
│   ├── coding-style.md
│   ├── api.md
│   └── roadmap.md
│
└── src/
```

Inside `CLAUDE.md`:

```markdown
# Project Documentation

@docs/architecture.md

@docs/plan.md

@docs/coding-style.md
```

Claude automatically incorporates those files when reading the project instructions.

---

# Referencing Directories

Directories can also be referenced.

Example:

```text
@docs/
```

However, this behaves differently from referencing a file.

---

# What Happens?

Claude **does not** load every file inside the directory.

Instead, it loads a listing of the directory contents.

For example:

```text
docs/
├── api.md
├── architecture.md
├── coding-style.md
├── plan.md
└── roadmap.md
```

This provides awareness of the project's structure without consuming the context required to load every document.

---

# Why This Is Useful

Sometimes Claude only needs to know:

* What documentation exists.
* Which files are available.
* How the project is organized.

Loading only the directory listing is much more efficient than loading every file.

---

# Sharing Instructions Between AI Tools

Many developers work with multiple AI coding assistants.

For example:

* Claude Code
* GitHub Copilot

Both tools can use project instruction files.

---

# The Problem

Without planning, you may end up maintaining:

```text
CLAUDE.md

AGENTS.md
```

Both files often contain nearly identical instructions.

This creates unnecessary duplication.

---

# A Better Approach

Instead of copying information between files, `CLAUDE.md` can simply reference `AGENTS.md`.

Example:

```markdown
@AGENTS.md
```

This means:

* `AGENTS.md` becomes the primary instruction file.
* `CLAUDE.md` simply points to it.
* Both Claude Code and GitHub Copilot can use the same project guidance.

---

# Benefits

Using a shared instruction file provides:

* One source of truth.
* Less duplicated documentation.
* Easier maintenance.
* Consistent instructions across multiple AI coding tools.

Whenever `AGENTS.md` is updated, both tools automatically benefit.

---

# Organizing Project Knowledge

Throughout the session, an important theme emerges:

Long-term project knowledge should be stored in project files rather than relying entirely on conversation history.

Examples include:

* Coding standards.
* Architecture decisions.
* Development workflow.
* Design principles.
* Planning documents.
* Coding conventions.

Keeping this information in project files makes it reusable across future sessions.

---

# Temporary vs Permanent Knowledge

A useful mental model is to separate information into two categories.

## Temporary Knowledge

Lives inside the current conversation.

Examples:

* Current debugging session.
* Today's implementation details.
* Temporary experiments.
* Immediate discussion.

This information disappears after clearing or restarting the session.

---

## Permanent Knowledge

Lives inside project files.

Examples:

* `CLAUDE.md`
* `AGENTS.md`
* Architecture documents
* Coding standards
* Planning documents

This information survives every new Claude session.

---

# Recommended Workflow

A practical workflow based on this lesson looks like:

1. Start a fresh Claude session.
2. Ensure project instructions are up to date.
3. Store long-term guidance inside `CLAUDE.md`.
4. Keep supporting documentation in separate Markdown files.
5. Reference those files using `@`.
6. Monitor context with `/context`.
7. Compact manually before context becomes too large.
8. Restart or clear Claude when changing tasks.
9. Continue working from a clean context.

---

# Best Practices

## Project Organization

* Keep `CLAUDE.md` concise.
* Split large documentation into separate files.
* Use `@` references to connect documentation.
* Avoid duplicating instructions.

---

## Context Management

* Monitor context regularly.
* Compact conversations manually.
* Clear conversations when switching tasks.
* Keep long-term knowledge outside the conversation.

---

## Permissions

* Grant permanent permissions only when appropriate.
* Review stored permissions periodically.
* Remove outdated permissions when necessary.

---

## Documentation

* Store important project decisions in Markdown files.
* Maintain documentation alongside code.
* Keep documentation synchronized with project evolution.

---

# Common Workflow Example

```text
Open Project
      │
      ▼
Launch Claude
      │
      ▼
Claude reads CLAUDE.md
      │
      ▼
CLAUDE.md references:
      │
      ├── @docs/architecture.md
      ├── @docs/plan.md
      ├── @docs/coding-style.md
      ▼
Claude now understands project guidance
      │
      ▼
Begin development
      │
      ▼
Monitor /context
      │
      ▼
/compact when needed
      │
      ▼
Update documentation
      │
      ▼
/clear when switching tasks
```

---

# Overall Philosophy of the Session

The lesson emphasizes that effective use of Claude Code goes beyond writing good prompts. Productive workflows come from combining several practices:

* Use slash commands to manage the session.
* Monitor and manage context proactively.
* Keep persistent project knowledge in documentation rather than conversation history.
* Organize documentation into modular files.
* Use `@` references to bring relevant information into context when needed.
* Maintain explicit control over permissions and project configuration.

Together, these practices help Claude remain consistent and effective across long-running development projects.

---

# Complete Command Cheat Sheet

| Command        | Purpose                                                                                |
| -------------- | -------------------------------------------------------------------------------------- |
| `/help`        | View available commands and shortcuts.                                                 |
| `/init`        | Initialize a project and create `CLAUDE.md`.                                           |
| `/model`       | View or switch the active Claude model.                                                |
| `/status`      | Display version, settings, and usage information.                                      |
| `/config`      | View Claude configuration.                                                             |
| `/usage`       | Display current resource and token usage.                                              |
| `/stats`       | View historical usage statistics and graphs.                                           |
| `/context`     | Inspect the current context window and memory usage.                                   |
| `/compact`     | Summarize conversation history to free context while preserving important information. |
| `/clear`       | Start a fresh conversation and reload `CLAUDE.md`.                                     |
| `/permissions` | View and manage stored permissions.                                                    |

---

# Final Takeaways

* Claude Code's power comes not only from the model but also from the workflow built around it.
* Context is a limited resource and should be managed deliberately.
* `CLAUDE.md` serves as the project's long-term memory.
* `@` references allow documentation to remain modular while still being available to Claude.
* The `.claude` directory stores project-specific configuration and permissions.
* Keeping documentation organized, permissions explicit, and context clean results in more reliable AI-assisted development.
* Many of the concepts covered in Claude Code—such as context management, instruction files, and modular documentation—are transferable to other AI coding assistants.


