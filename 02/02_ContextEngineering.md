# Week 1, Day 2: Context Engineering & Memory Architecture

Possibly the single most popular expression in the AI engineering world last year was **Context Engineering**. Because Large Language Models (LLMs) are entirely stateless (they have no native memory), they rely exclusively on the exact input you provide in that exact moment to generate their output.

A couple of years ago, the focus was on "Prompt Engineering"—simply figuring out how to ask a chatbot a good question. Today, this has evolved into **Context Engineering**. This discipline recognizes that success is not just about the text prompt; it is about architecting the entire environment (tools, rules, active memory, and history) to give the LLM exactly what it needs to achieve your goal.

---

## 1. The Context Stack: What Goes Into the LLM

To engineer context properly, you must understand how an AI wrapper packages your project before sending it to the LLM. Think of the context stack as a payload of information divided into specific layers.

<img width="1022" height="956" alt="image" src="https://github.com/user-attachments/assets/886cff0f-6abd-4b41-a500-07b502c4d9cc" />

### The 4 Layers of Context Storage

To make this easy to remember, view the context window as four distinct operational layers:

* **Layer 1: The System Prompt (The Persona)**
* *What it is:* The most crucial, general information at the absolute beginning of the payload.
* *Purpose:* It frames the LLM's identity, its overall job (e.g., an autonomous C# developer vs. an airline chatbot), its tone, and its strategic approach.


* **Layer 2: Tools (The Capability Menu)**
* *What it is:* A technical description of the capabilities the LLM has access to.
* *Purpose:* It teaches the LLM how to interact with the outside world. If the LLM knows that outputting a specific command (like `dotnet build`) will trigger a background script, it can use that tool and wait for the results. *(Note: Many developers conceptually group this under the System Prompt).*


* **Layer 3: Project Memory (The Persistent Rules)**
* *What it is:* Specialized, persistent files—most commonly named `agents.md`, `claude.md`, or `gemini.md`—that get injected into the context every single time.
* *Purpose:* To store coding standards, folder architectures, and project constraints so the agent never has to guess your repository's rules.


* **Layer 4: Conversation History (The Scratchpad)**
* *What it is:* The massive, rolling log of the current session that gives the LLM the "illusion" of memory.
* *Purpose:* It holds all user messages, the AI's step-by-step reasoning tokens, generated code, tool execution requests, and the raw terminal outputs returned by those tools.



---

## 2. Token Limits and the "Less is More" Law

Every LLM has a hard "Context Window Limit"—the absolute maximum number of words (tokens) it can hold in its memory at one time before crashing.

**Hard Token Capacity Metrics (2026 Benchmarks):**

* **Anthropic Claude 4.5 (Sonnet & Opus):** 200,000 tokens
* **OpenAI GPT-5.2:** 400,000 tokens
* **Google Gemini (in Antigravity):** 1,000,000 tokens

**The Golden Rule of Context:**
While developers obsess over maximizing these massive limits, the engineering reality is that **accuracy degrades long before you hit the hard limit**. If you shove too much data into the context window, the model gets distracted, loses coherence, and forgets core instructions. You will always get the highest-quality, most accurate code generation when the context window is clean, focused, and nearly empty. **Less is more.**

---

## 3. Context Compacting: Managing the Overload

Because autonomous coding loops generate massive amounts of history (Layer 4), the context window fills up rapidly. To prevent crashes, modern platforms use **Context Compacting**.

<img width="1043" height="1012" alt="image" src="https://github.com/user-attachments/assets/66eb8ec9-3d82-4f61-8634-95a40be22142" />

* **How it Works:** When the software detects the context limit approaching, it temporarily pauses the agent. It forces the LLM to read the entire bloated history, write a highly dense summary, and replace the massive log with that tiny summary. This instantly frees up thousands of tokens of space.
* **The Developer's Dilemma:**
* *The Old Guard Fear:* Historically, developers didn't trust this process. If the AI summarized away a critical bug fix, it would immediately repeat the same mistake. Developers preferred to manually stop the agent, rewrite their `agents.md` file, and completely restart the session.
* *The Modern 2026 Best Practice:* Compacting algorithms have become incredibly reliable. The modern standard is to **trust the compactor out of the box** and let the software manage its own memory limits.



---

## 4. Full Context Engineering Sample: .NET Microservice

To see how all these pieces fit together, here is a complete, copy-pasteable example of how a professional Context Package is structured for a specific project. This combines the System Prompt, Tool Menu, and `agents.md` rules into a single, cohesive architecture.

### The Agent Configuration Payload

**[LAYER 1] System Prompt:**

> "You are an elite backend software engineer specializing in C# and .NET 8. Your objective is to build high-performance, scalable microservices. You must write clean, asynchronous C# code, utilize dependency injection strictly, use structured routing architectures, and always communicate your architectural decisions clearly before generating code."

**[LAYER 2] Tools Definitions:**

> "You have access to the `dotnet_cli` tool. If you need to add a NuGet package, output the command `dotnet add package [PackageName]`. You also have access to `ef_core_migrations`. Use this tool to execute `dotnet ef database update` when database schemas change."

**[LAYER 3] Persistent Project Memory (`agents.md`):**

```markdown
# Project Context
Inventory Management Microservice

## Global Engineering Standards
1. All microservices in this organization must use Serilog for structured logging.
2. Databases must use PostgreSQL via Entity Framework Core.
3. Authentication is always handled via standard JWT bearer tokens validated against Azure Active Directory.

## Architecture Rules (Clean Architecture)
- **Domain Layer:** All domain entities must reside strictly inside the `Inventory.Domain` project layer.
- **Infrastructure:** All database context setups must map inside `Inventory.Infrastructure`.
- **API Routing:** All REST endpoints must be Minimal APIs defined cleanly in the `Inventory.API` orchestration layer.
- **Testing:** Use xUnit for all unit testing coverage.

```

**[LAYER 4] Active Conversation History (The Live Log):**

> **User:** "Create the `Product` domain entity and compile it."
> **AI Reasoning:** "I need to create a C# record or class for the Product entity with standard properties like Id, Name, and Price, ensuring it maps cleanly to EF Core."
> **AI Action (Code Generation):** `public class Product { public Guid Id { get; set; } public string Name { get; set; } public decimal Price { get; set; } }`
> **AI Action (Tool Call):** `[Execute: dotnet build]`
> **System Return:** `Build succeeded. 0 Warning(s). 0 Error(s).`

#### References:

* [https://www.udemy.com/course/ai-coder-from-vibe-coder-to-agentic-engineer/learn/lecture/54780267#overview](https://www.udemy.com/course/ai-coder-from-vibe-coder-to-agentic-engineer/learn/lecture/54780267#overview)
