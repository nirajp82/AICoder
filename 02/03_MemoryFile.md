# Week 1, Day 2 (Part 4): The Project Memory File (`agents.md`)

## 1. Introduction to Markdown and why LLMs Love It

The primary tool used to seed, guide, and prep coding agents is a file named `agents.md`.

* **What is Markdown?** The `.md` extension stands for Markdown. You can think of it as a simpler, more human-readable and writable version of an HTML web page, without all the verbose tags.
* **The Syntax Hierarchy:** Markdown maps structure using simple typographic characters:
* `# Project Summary` (Single hash) represents a big heading (`<h1>`).
* `##` (Two hashes) is like an `<h2>`.
* `###` (Three hashes) is like an `<h3>`.
* Hyphens (`-`) are used for bulleted lists, and numbers for ordered lists.
* **Backticks for Code:** You use a single backtick (`) wrapped around code for inline code (just a little bit of code). You use three backticks (```) to open and close a whole block of code.


* **LLM Affinity:** Large Language Models *love* Markdown. They have been trained on lots of it, and they generate lots of it. It is easy to write, making it the perfect format to prep agents.

## 2. Writing Style for Effective Context Seeding

When writing instructions within an agent file, use a natural language style, just like you would write a standard prompt.

* **Be Concise and Assertive:** You want it to be nice, concise, crisp, assertive, and have no ambiguity. You want as much signal as you can in the words you use.
* **Conserve Precious Token Space:** This file gets squashed into your context window. This is precious space, so do not be verbose. Make every word count.

## 3. Platform Naming Standards & Industry Convergence

The exact name of the file depends on the tool you are using, but the industry is converging on this standard:

* **Cursor, Codex, GitHub Copilot:** `agents.md` *(Note: Cursor and Copilot historically had other kinds of files, like "Cursor rules", but increasingly everyone is converging on `agents.md` as the de facto standard).*
* **Claude Code:** `claude.md`
* **Antigravity (Google):** `gemini.md`

## 4. The Directory Hierarchy & Resolution Logic

The inclusion of an execution file is not static. It works on a hierarchy.

* **Project Root:** You typically have one file at the top of your project root directory (e.g., the `instant` directory from yesterday). This is always included in the context.
* **Subdirectories:** You can have an `agents.md` at any level of nesting (a sub-sub-sub directory). This file is **only** read in when the agent is working on files in that specific folder or deeper.
* **The Override Law:** When working on a file, the agent reads the innermost `agents.md`, then works backwards through all parent directories. Information in the innermost file overrides information in any outer directory. This allows you to apply highly specific rules deep in your project.

---

## 5. Structuring a Production-Grade File

A robust configuration document manages goals, success barriers, and engineering limits.

### INJECT IMAGE HERE: `image_863b48.jpg`

> **Image Placement Note:** Place your original `image_863b48.jpg` reference here.

### The Instructor's Core Rules (Python Example)

Here are the exact things the instructor includes in a good `agents.md` to correct past AI problems:

1. **Goals & Success Criteria:** Provide a checklist so the agent is forced to check things off.
2. **Links:** Provide optional links to other documents.
3. **Simpler is Better:** AI agents love to overcomplicate everything. Stress simplicity.
4. **Short READMEs / No Emojis:** LLMs love generating long, wordy READMEs. (The instructor used to be happy getting these in open-source PRs, but now knows better!). Tell them: short READMEs, no emojis.
5. **Use BLOCK CAPITALS:** Using the word `IMPORTANT` in all block capitals actually works very well.
6. **Avoid Defensive Programming (Python):** They love to put `try` blocks around everything. Tell them to avoid `isinstance` checks (horrible hacky stuff) and only manage exceptions when necessary.
7. **Enforce Tool Wrappers:** If using the Python `uv` package manager, explicitly mandate: "Always use `uv run xxx`, NEVER `python3 xxx`."

### Translation: .NET Microservice Example

Because you are building in .NET, here is how those exact instructor rules translate into a C# Microservice environment for your project:

```markdown
# Project Summary
Building a high-throughput Inventory Tracking Microservice in .NET 8.

## Goals
- Implement Domain-Driven Design (DDD).

## Success Criteria
- [ ] 100% of public endpoints must route through Minimal APIs.

# Code standards and guidelines
1. Simpler is better - do not overcomplicate architectures.
2. Comments only when necessary.
3. Be concise, short README, no emojis.
4. IMPORTANT: Avoid overly defensive programming. Avoid redundant runtime type checks; do not place global try-catch wrappers around everything. Only handle exceptions when explicitly mandatory.
5. Use dotnet CLI; ALWAYS `dotnet run --project xxx` or `dotnet build` - NEVER invoke execution using unmapped native binaries.

```

---

## 6. Framing Logic: Positives vs. Negatives

* **Focus on the Positives:** Tell the LLM what it *should* do.
* **Avoid too many Negatives:** Do not use too many instructions like "Never Python3" or "Do not overcomplicate." LLMs are strangely bad at handling negatives; they lose coherence and forget what *not* to do. They are much better at remembering what they *are* supposed to do.

---

## 7. The Architectural Evolution: 2025 vs. 2026 Mindsets

### The 2025 Prevailing Wisdom (The Control Strategy)

* **The Philosophy:** Your success comes from sweating over a really excellent `agents.md` file. It is hard work.
* **The Execution Loop:** You put files at multiple levels. You continually rewrite and prune them, removing what doesn't matter and adding new things.
* **Manual Pruning Reset:** You frequently stop the agent, prune the file, and restart the agent completely fresh so the context is entirely clear.

### The 2026 Mindset (The Let-Go Strategy)

* **The Philosophy:** Let it hang out. Be more comfortable giving up the reins.
* **The Execution Loop:** Focus strictly on the end goal. Let the agent use new features (skills, loops, sub-agents, swarms) to self-correct and just do its thing.

### The Instructor's Verdict

Despite the 2026 trend, the instructor **is still of the 2025 school of thought for large projects.** The amount of work put into optimizing the `agents.md` file makes an enormous difference to the output.

The only time you should embrace the 2026 "let it go" mindset right now is for **toy projects** (like the first-person shooter web page from yesterday). For everything else, stay all over it and meticulously manage your context!
