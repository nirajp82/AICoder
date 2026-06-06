# Week 1, Day 2: AI Basics & How It Actually Works

## 1. What is an LLM (Large Language Model)?

Think of an LLM (like GPT) as a super-powered version of the "autocomplete" feature on your phone's keyboard. It has read almost everything on the internet to learn how humans talk, so it is very good at guessing what word comes next.

* **Tokens (How it reads):** The AI does not read whole words. It chops words into smaller pieces called **tokens** (sometimes a whole word, sometimes just a few letters).
* **Probability (How it guesses):** It does not just pick the single best word. It gives a score to *every* possible next word. For the phrase "Two plus two is", the word "four" gets a nearly 100% score, and the word "banana" gets a 0% score.
* **The Loop (How it writes):** The AI only writes **one piece at a time**. It reads your prompt, guesses the first word, adds it to your prompt, and then reads the whole thing again to guess the second word.

### The Complete Inference Loop

Here is the showing how the AI loops your text to generate the answer step-by-step:

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

## 3. The Two "Tricks" That Make AI Look Smart

The raw AI brain is actually pretty basic. To make it feel like you are chatting with a smart human, developers use software tricks.

### Trick 1: The "Goldfish Memory" Trick

* **The Problem:** The raw AI brain is totally stateless. Every time you ask a question, it is meeting you for the first time.
* **The Trick:** The website (like ChatGPT) secretly copies your *entire past conversation* and pastes it into every new message you send.

> **The "Hi, I'm Ed" Example:**
> If you just used the raw brain and said, "Hi, I'm Ed," it would say "Hello, Ed." If your next message was just "Who am I?", the AI would say "I don't know," because it forgot the first message.
> But ChatGPT tricks the brain by silently sending: *"User: Hi I'm Ed. AI: Hello Ed. User: Who am I?"* all at once. The AI reads that whole script and easily guesses "You are Ed."

### Trick 2: The "Thinking Out Loud" (Reasoning) Trick
Here is the rewritten version for your README, addressing those exact points so the mechanics are crystal clear:

---

### Trick 2: The "Thinking Out Loud" (Reasoning) Trick

* **The Concept (No Inner Voice):** Unlike humans, an AI cannot pause and "think silently" in its head to crunch numbers. It can only generate text based on the exact sequence of words currently fed into its memory (often called the "context window").
* **The Problem:** If you ask a tricky math or logic question and force the AI to answer immediately, it has to rely on a blind instinct. It will usually blurt out the most common, statistically obvious answer (which is often wrong).
* **The Trick ("Chain of Thought"):** Originally, users would literally add the phrase "please think step-by-step" to their prompts. Now, the creators of the LLMs train the models to automatically output sentences explaining their logic directly into the chat text *before* generating the final answer.
* **Why it Works (The "Scratch Paper" Effect):** The AI does not have eyes to "read a screen." Instead, its engine re-processes the *entire text of the conversation* every time it needs to guess the next single word. By typing out its logic first, the AI creates a trail of text (like scratch paper). It feeds its own freshly typed logic back into its engine on every loop, which mathematically steers its "autocomplete" away from a blind guess and toward the correct conclusion.

> **The Coin Toss Example:**
> **Question:** You toss two coins. One is heads. What are the chances the other is tails?
> * **Without the trick (Instant Guess):** The AI sees the words "coin toss" and immediately blurts out **1/2** because 50/50 is the most common association with coins on the internet.
> * **With the trick (Using Scratch Paper):** The AI is forced to output its steps into the chat:
> 1. It generates: *"The possible outcomes for two coins are HH, HT, TH, and TT."*
> 2. It processes that new text, applies the rule, and generates: *"We know at least one is heads, so TT is impossible. That leaves HH, HT, and TH."*
> 3. It processes *that* new text, and generates: *"Out of those 3 options, 2 of them (HT and TH) contain a tails."*
> 4. **The Final Answer:** Now, the AI must guess the final answer. Because the words *"2 out of 3"* are sitting right there in the text it just generated, its engine is mathematically forced to predict **2/3**.
> 
