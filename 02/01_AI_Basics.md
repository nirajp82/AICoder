# Week 1, Day 2: AI Basics & How It Actually Works

## 1. What is an LLM (Large Language Model)?

Think of an LLM (like GPT) as a super-powered version of the "autocomplete" feature on your phone's keyboard. It has read almost everything on the internet to learn how humans talk, so it is very good at guessing what word comes next.

* **Tokens (How it reads):** The AI does not read whole words. It chops words into smaller pieces called **tokens** (sometimes a whole word, sometimes just a few letters).
* **Probability (How it guesses):** It does not just pick the single best word. It gives a score to *every* possible next word. For the phrase "Two plus two is", the word "four" gets a nearly 100% score, and the word "banana" gets a 0% score.
* **The Loop (How it writes):** The AI only writes **one piece at a time**. It reads your prompt, guesses the first word, adds it to your prompt, and then reads the whole thing again to guess the second word.

### The Complete Inference Loop

Here is a table showing how the AI loops your text to generate the answer step-by-step:

| Step | What the AI Reads (The Input Sequence) | What the AI Guesses Next |
| --- | --- | --- |
| 1 | "What is the capital of France?" | "The" |
| 2 | "What is the capital of France? The" | "capital" |
| 3 | "What is the capital of France? The capital" | "of" |
| 4 | "What is the capital of France? The capital of" | "France" |
| 5 | "What is the capital of France? The capital of France" | "is" |
| 6 | "What is the capital of France? The capital of France is" | "Paris." |

---

## 2. The Engine vs. The Car (LLMs vs. AI Apps)

People often confuse the AI brain with the website they are using. It is important to know the difference.

| Concept | What it is | Easy Example | Real World Example |
| --- | --- | --- | --- |
| **LLM (The Brain)** | Just the raw math program that predicts the next word. It does nothing else. | The car engine | GPT, Claude |
| **AI Application (The Product)** | The full software built around the brain. It adds a chat box, buttons, memory, and internet search. | The whole car (seats, steering wheel) | ChatGPT, Cursor Agent |

---

## 3. The Four Software "Tricks" That Make AI Look Smart

The raw AI brain is actually pretty basic. To make it feel like you are chatting with a smart human or a capable assistant, developers use software tricks.

### Trick 1: The "Goldfish Memory" Trick

* **The Problem:** The raw AI brain is totally stateless. Every time you ask a question, it is meeting you for the first time.
* **The Trick:** The website (like ChatGPT) secretly copies your *entire past conversation* and pastes it into every new message you send.

> **The "Hi, I'm Ed" Example:**
> If you just used the raw brain and said, "Hi, I'm Ed," it would say "Hello, Ed." If your next message was just "Who am I?", the AI would say "I don't know," because it forgot the first message.
> But ChatGPT tricks the brain by silently sending: *"User: Hi I'm Ed. AI: Hello Ed. User: Who am I?"* all at once. The AI reads that whole script and easily guesses "You are Ed."

### Trick 2: The "Thinking Out Loud" (Reasoning) Trick

* **The Concept (No Inner Voice):** Unlike humans, an AI cannot pause and "think silently" in its head to crunch numbers. It can only generate text based on the exact sequence of words currently fed into its memory (often called the "context window").
* **The Problem:** If you ask a tricky math or logic question and force the AI to answer immediately, it has to rely on a blind instinct. It will usually blurt out the most common, statistically obvious answer (which is often wrong).
* **The Trick ("Chain of Thought"):** Originally, users would literally add the phrase "please think step-by-step" to their prompts. Now, the creators of the LLMs train the models to automatically output sentences explaining their logic directly into the chat text *before* generating the final answer.
* **Why it Works (The "Scratch Paper" Effect):** The AI does not have eyes to "read a screen." Instead, its engine re-processes the *entire text of the conversation* every time it needs to guess the next single word. By typing out its logic first, the AI creates a trail of text (like scratch paper). It feeds its own freshly typed logic back into its engine on every loop, which mathematically steers its "autocomplete" away from a blind guess and toward the correct conclusion.

> **The Coin Toss Example:**
> **Question:** You toss two coins. One is heads. What are the chances the other is tails?
> * **Without the trick (Instant Guess):** The AI sees the words "coin toss" and immediately blurts out **1/2** because 50/50 is the most common association with coins on the internet.
> * **With the trick (Using Scratch Paper):** The AI is forced to output its steps into the chat:
> 
> 
> 1. It generates: *"The possible outcomes for two coins are HH, HT, TH, and TT."*
> 2. It processes that new text, applies the rule, and generates: *"We know at least one is heads, so TT is impossible. That leaves HH, HT, and TH."*
> 3. It processes *that* new text, and generates: *"Out of those 3 options, 2 of them (HT and TH) contain a tails."*
> 4. **The Final Answer:** Now, the AI must guess the final answer. Because the words *"2 out of 3"* are sitting right there in the text it just generated, its engine is mathematically forced to predict **2/3**.
> 
> 

### Trick 3: The "Text-to-Action" Protocol (Tool Calling)

* **The Problem:** The raw AI brain is entirely disconnected from the outside world. It cannot open a browser, crunch numbers, or save files. It only predicts words. If forced to answer a complex math problem, it will just blindly guess a number.
* **The Concept (Text as a Remote Control):** Because the AI can only generate text, developers realized they could use that text as a command trigger. We teach the AI to stop guessing and instead write a specific text command asking the *software* to do the work.
* **The Trick:** In the hidden background instructions, the software wrapper tells the AI: *"You have access to a Python environment. If you need to do math, do not guess. Instead, output the exact string `PYTHON: [your code here]`."*
* **How it Works in Practice:**

1. You ask the AI: "What is the square root of Pi?"
2. The AI realizes its autocomplete can't solve this accurately, so it generates the special text token: `PYTHON: import math; math.sqrt(math.pi)`.
3. **The secret intercept:** The AI *does not run this code*. Your software wrapper sees the word `PYTHON:`, instantly pauses the AI, takes that code, runs it on the computer, gets the exact answer (`1.772`), and secretly pastes that answer back into the AI's context window.
4. The AI reads the injected answer, and then confidently translates it into a normal, human-readable sentence for you.

* **The Pro Takeaway:** The LLM itself *never used a tool*. It just used its autocomplete engine to generate a text request, and the software wrapper acted as the hands that did the actual work.
* **Where it Executes (Browser vs. Thick Client):** Where this intercept actually executes the code depends entirely on the architecture of the application wrapper you are using.

#### 1. The Browser Setup (e.g., ChatGPT.com)

* **Where the Wrapper lives:** On OpenAI's cloud servers.
* **How it works:** Your web browser is just a display terminal. When you ask "What is the square root of Pi?", the AI generates the token: `PYTHON: import math; math.sqrt(math.pi)`. The software wrapper running on OpenAI's servers catches this token, pauses the AI, and executes the script in a locked-down, secure cloud "sandbox" environment on *their* computers (not your local laptop). It gets the result (`1.772`) and slides it back into the AI's context window so it can write out the final answer to you.

#### 2. The Thick Client Setup (e.g., Cursor, VSCode, Terminal CLI)

* **Where the Wrapper lives:** Installed directly on *your local computer*.
* **How it works:** Applications like Cursor are local software wrappers. They send your prompt across the internet to the cloud LLM. But when the cloud LLM returns a tool command (like `WRITE_FILE` or `RUN_TERMINAL`), the local app intercepts it and executes that instruction directly on **your computer's operating system and local hard drive**. This is what gives programming tools the power to read your files, edit your codebase, and compile systems directly on your machine.

#### Architecture Diagram: The Secret Intercept

```mermaid
flowchart TD
    subgraph Browser [Browser Architecture: ChatGPT Website]
        direction TB
        B_User((You)) -->|1. Types in browser| B_UI[Web Browser]
        B_UI -->|2. Sends text over internet| B_Wrapper[Cloud Software Wrapper]
        
        B_Wrapper -->|3. Sends prompt| B_LLM{Cloud LLM Engine}
        B_LLM -.->|4. Tool Call: PYTHON| B_Wrapper
        
        B_Wrapper -->|5. Secret Intercept: Runs code| B_Exe[Cloud Sandbox Server]
        B_Exe -.->|6. Returns answer| B_Wrapper
        
        B_Wrapper -->|7. Feeds answer back| B_LLM
        B_LLM -.->|8. Final text response| B_Wrapper
        B_Wrapper -->|Displays to user| B_UI
    end

    %% This invisible link forces the Thick Client box to render UNDER the Browser box
    Browser ~~~ ThickClient

    subgraph ThickClient [Thick Client Architecture: Cursor / CLI]
        direction TB
        T_User((You)) -->|1. Types in IDE/CLI| T_Wrapper[Local App: Cursor / CLI]
        
        T_Wrapper -->|2. API Request over internet| T_LLM{Cloud LLM Engine}
        T_LLM -.->|3. Tool Call: RUN_TERMINAL| T_Wrapper
        
        T_Wrapper -->|4. Secret Intercept: Runs code| T_Exe[YOUR Local OS / Hard Drive]
        T_Exe -.->|5. Returns terminal output| T_Wrapper
        
        T_Wrapper -->|6. Feeds output back via API| T_LLM
        T_LLM -.->|7. Final text response| T_Wrapper
        T_Wrapper -->|Displays in IDE| T_User
    end

    %% Styling
    classDef cloud fill:#e1f5fe,stroke:#03a9f4,stroke-width:2px;
    classDef local fill:#e8f5e9,stroke:#4caf50,stroke-width:2px;
    classDef brain fill:#f3e5f5,stroke:#9c27b0,stroke-width:2px;

    class B_Wrapper,B_Exe,T_LLM,B_LLM cloud;
    class T_Wrapper,T_Exe local;
    class B_LLM,T_LLM brain;


```

### Trick 4: The "Are We There Yet?" Trick (The Loop)

* **The Problem:** Asking the AI to do a massive task in one single prompt usually fails. It gets confused or stops halfway.
* **The Trick:** Instead of calling the LLM once and hoping for the best, the software wrapper calls the LLM in a continuous loop.
* **How it Works:** The software asks the AI to take *one* step. Once the AI outputs that step, the software automatically asks: "Are you finished yet?" If the AI says no, the software feeds the progress back into the engine and runs it again. It loops infinitely until the AI finally says the goal is complete.

---

## 4. Advanced Theory: The Mechanics of AI Reasoning

To master AI coding, you must understand how to manipulate the model's prediction engine. The "Thinking Out Loud" trick is professionally known as **Chain of Thought (CoT) Prompting**.

### Pro Terminology: How the Engine Actually Runs

When we say the AI "reads the screen," what is mathematically happening is called **Autoregressive Generation**.

* **The Context Window:** This is the AI's working memory for a single session. It is the exact sequence of tokens (your prompt plus everything it has generated so far) that is fed into the neural network.
* **Autoregressive Generation:** LLMs use their own previous output as input for future predictions.
* **The Mechanism:** The AI cannot look ahead, and it cannot edit what it just wrote. It calculates the probability of the next token strictly based on the current state of the Context Window. If the Context Window lacks logical steps, the probability of generating the correct final answer is incredibly low.

### A Classic Example: The Bat and Ball Problem

To see why Autoregressive Generation fails without Chain of Thought, look at this famous test of cognitive reflection:

> **The Prompt:** "A bat and a ball cost $1.10 in total. The bat costs $1.00 more than the ball. How much does the ball cost?"

* **Scenario A: Zero-Shot Prompting (Instant Guess)**
If you ask the model to just answer the question, its engine looks at the tokens `$1.10` and `$1.00`. The highest probability statistical association between those numbers is simple subtraction.
*The Output:* "The ball costs $0.10."
*The Reality:* If the ball is `$0.10`, and the bat is `$1.00` *more* than the ball (`$1.10`), the total would be `$1.20`. The AI failed because it relied on statistical instinct instead of math.
* **Scenario B: Chain of Thought Prompting (Reasoning)**
If you force the model to output the algebraic steps first, the autoregressive engine is forced to evaluate the logic token-by-token.
*The Output:*

1. Let $b$ be the cost of the ball and $B$ be the cost of the bat.
2. We know the total is `$1.10`: $B + b = 1.10$
3. We know the bat is `$1.00` more than the ball: $B = b + 1.00$
4. Substitute $B$ into the first equation: $(b + 1.00) + b = 1.10$
5. Combine terms: $2b + 1.00 = 1.10$
6. Subtract `$1.00`: $2b = 0.10$
7. Divide by 2: $b = 0.05$

*The Reality:* By the time the AI needs to generate the final answer, the token `0.05` is mathematically the only possible next token. The AI solved it correctly because we forced the Context Window to contain the proof.

### Why This Matters for AI Coders

As you progress in your course to building AI Agents, you will apply this mechanic to writing software.

If you ask an AI: *"Write a Python script to scrape a website, parse the data, and save it to a database."*

* **Without CoT:** The AI instantly starts writing code. It will likely hallucinate variables, forget dependencies, and write a buggy script because it is guessing the code token-by-token without a plan.
* **With CoT:** You prompt the AI: *"Before writing any code, outline the architecture, list the necessary Python libraries, and define the data schema."* The AI generates a text plan. When it finally writes the code, it uses that generated plan inside its Context Window as a rigid blueprint, resulting in functional, bug-free code.

---

## 5. What is an AI Agent? (The Winning Definition)

Because "AI Agent" became a massive buzzword, the definition kept changing. Over time, it evolved from "a system that does work independently" (OpenAI's early definition) to "an LLM that controls a workflow" (Hugging Face / Anthropic).

However, as an AI Coder, the modern, widely accepted definition you need to know is:

> **An AI Agent is an LLM that runs TOOLS in a LOOP to achieve a GOAL.**

### Deconstructing the Cursor Agent Example

If you tell an AI coding app like Cursor: *"Build me a first-person shooter game in a web page,"* here is how it uses all the foundational tricks to become an "Agent":

| Component | What is actually happening? |
| --- | --- |
| **The Goal** | You provided the prompt: "Build a first-person shooter." |
| **The Tools (Trick 3)** | The LLM generates text asking the software to use tools (e.g., `WRITE_FILE: index.html`, or `RUN_TERMINAL: npm start`). |
| **The Loop (Trick 4)** | The software executes the tool, feeds the result back to the LLM, and asks, "Is the game done?" The LLM loops again and again, writing code file by file, until the game is finished. |

---

## Pro Tips

* **Pre-fill the Context:** When starting a complex task, paste your project documentation or API references into the chat first. Because the AI relies entirely on its Context Window, "seeding" it with factual constraints heavily reduces hallucinations.
* **Force the Format to Force the Logic:** Ask the AI to structure its output using Markdown headings or a JSON schema. Constraining *how* the AI formats its response inherently slows down its autoregressive generation, forcing it to structure its thoughts more logically before jumping to a final answer.
* **Acknowledge the Limit:** The Context Window has a maximum size (e.g., 128k tokens). In deep agent loops, the "Goldfish Memory" trick eventually runs out of space. Advanced developers use summarization prompts mid-loop to condense older conversation history and free up token space for new actions.

## Real-World Use Cases

* **Automated Customer Support (Intercom, Zendesk AI):** These systems use the "Goldfish Memory" trick alongside "Tool Calling" to fetch a customer's billing history from an external database and securely process refunds without human intervention.
* **AI IDEs (Cursor, GitHub Copilot Workspace):** Code editors use the "Thick Client Setup" to locally execute tool calls (`READ_FILE`, `RUN_LINTER`, `WRITE_CODE`) directly on your machine's file system, essentially putting a junior developer inside your laptop.
* **Data Extraction & Web Scraping Pipelines:** Agents are deployed to navigate unstructured websites, scrape data, use Chain of Thought to identify relevant metrics, format the data into a strict schema, and use a tool to insert it directly into a SQL database.

## Key Takeaways

* **LLMs are just guessing engines:** They predict the next token based purely on the text currently in their Context Window.
* **The App is not the Brain:** ChatGPT is a software application that adds memory, UI, and tools; GPT-4 is the raw engine powering it underneath.
* **Reasoning requires writing:** Because an AI has no internal monologue, it must write its thoughts out loud (Chain of Thought) to mathematically guide its next-word prediction toward a correct, logical answer.
* **Tools are intercepted text:** An LLM cannot execute code. It outputs a text string asking for code to be run, and the surrounding software intercepts it, runs it, and feeds the result back.
* **Agents equal Loops + Tools:** An AI Agent is simply an LLM placed in an automated software loop, continuously triggering tools until a defined goal is met.

## Glossary

* **Token:** The fundamental unit of text an LLM reads and generates (can be a word, part of a word, or punctuation).
* **Context Window:** The temporary working memory of an LLM during a session; it includes your prompt and everything generated in that specific conversation so far.
* **Autoregressive Generation:** The mathematical process where an AI uses its own previously generated tokens as the input to predict the next token.
* **Chain of Thought (CoT):** A prompting strategy that forces the AI to output step-by-step reasoning before producing a final answer, improving logical accuracy.
* **Tool Calling:** A protocol where an LLM generates a specific text command that instructs an external software wrapper to perform an action (like running code or searching the web).
* **AI Agent:** An LLM wrapped in a software architecture that allows it to execute tools in a continuous loop to achieve a complex goal.

## Revision Notes

* **What it does:** Predicts the highest probability next token.
* **Trick 1 (Memory):** Pastes the entire conversation history into every new prompt.
* **Trick 2 (Reasoning):** Uses "scratch paper" (Chain of Thought) to steer its math/logic.
* **Trick 3 (Tools):** Outputs text commands that the software wrapper executes (Browser = Cloud sandbox; Thick Client = Local hard drive).
* **Trick 4 (The Loop):** Software repeatedly prompts the AI to take the next step until the overarching goal is completed.
* **The Golden Definition:** `Agent = LLM + Tools + Loop + Goal`

## Interview Questions

**Q: Explain the difference between an LLM and an AI Application.**

> **A:** An LLM is the raw, underlying neural network engine designed solely to predict the next token based on a sequence of text. An AI Application is the software wrapper built around the LLM that provides a user interface, maintains state (memory), and intercepts specific text outputs to run external tools.

**Q: Why does "Chain of Thought" prompting drastically improve an LLM's performance on math or logic problems?**

> **A:** LLMs generate text autoregressively and do not possess a hidden "internal monologue" to calculate answers before typing. By forcing the LLM to output its logical steps into the chat first, those steps become part of the Context Window. The model then uses that highly logical text as the context to accurately predict the final answer token, rather than relying on a blind statistical guess.

**Q: If an LLM is disconnected from the internet, how does it manage to browse the web or run Python code?**

> **A:** The LLM itself does not browse the web or run code. It is trained on a "Tool Calling" protocol. When it recognizes a task it cannot do, it outputs a specifically formatted text string (e.g., `SEARCH: [query]`). The surrounding AI application intercepts this string, pauses the LLM, executes the search using traditional software, and then pastes the search results back into the LLM's Context Window.

## Practice Exercises

1. **The Tokenization Test:** Go to OpenAI's public Tokenizer tool ([platform.openai.com/tokenizer](https://platform.openai.com/tokenizer)) and paste in a paragraph of complex code or text. Observe how words are split. Try to identify which types of words cost more tokens (e.g., common English words vs. complex variables).
2. **Zero-Shot vs. Chain of Thought:** Open an AI chatbot. Give it a complex logic puzzle or a multi-step word problem *and explicitly tell it to answer in exactly one word*. Note the failure. Open a new chat and ask the same puzzle, but command it to write out three paragraphs of reasoning before answering. Compare the final outputs.
3. **Simulate a Tool Call:** Act as the "Software Wrapper" for a friend. Have them write a prompt on a piece of paper (the LLM). When they need to do math, they must write `CALCULATE: [equation]`. You take the paper, use a calculator, write the answer down, and hand it back so they can finish their sentence. This physical exercise perfectly demonstrates how the Text-to-Action protocol works in production.
