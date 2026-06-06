Week 1, Day 2: AI Basics & How It Actually Works
1. What is an LLM (Large Language Model)?
Think of an LLM (like GPT) as a super-powered version of the "autocomplete" feature on your phone's keyboard. It has read almost everything on the internet to learn how humans talk, so it is very good at guessing what word comes next.

Tokens (How it reads): The AI does not read whole words. It chops words into smaller pieces called tokens (sometimes a whole word, sometimes just a few letters).
Probability (How it guesses): It does not just pick the single best word. It gives a score to every possible next word. For the phrase "Two plus two is", the word "four" gets a nearly 100% score, and the word "banana" gets a 0% score.
The Loop (How it writes): The AI only writes one piece at a time. To write a whole sentence, it reads your prompt, guesses the first word, adds it to your prompt, and then reads the whole thing again to guess the second word.
Step	What the AI Reads	What the AI Guesses Next
1	"What is the capital of France?"	"The"
2	"What is the capital of France? The"	"capital"
3	"What is the capital of France? The capital"	"of"
2. The Engine vs. The Car (LLMs vs. AI Apps)
People often confuse the AI brain with the website they are using. It is important to know the difference.

Concept	What it is	Easy Example	Real World Example
LLM (The Brain)	Just the raw math program that predicts the next word. It does nothing else.	The car engine	GPT, Claude
AI Application (The Product)	The full software built around the brain. It adds a chat box, buttons, internet search, etc.	The whole car (seats, steering wheel)	ChatGPT, Cursor Agent
3. The Two "Tricks" That Make AI Look Smart
The raw AI brain is actually pretty basic. To make it feel like you are chatting with a smart human, developers use software tricks.

Trick 1: The "Goldfish Memory" Trick
The Problem: The raw AI brain has zero memory. Every time you ask a question, it is like it is meeting you for the first time.
The Trick: The website (like ChatGPT) secretly copies your entire past conversation and pastes it into every new message you send.
The Result: Because the AI reads the whole chat history every single time, it gives the illusion that it "remembers" what you said earlier.
Trick 2: The "Thinking Out Loud" Trick
The Problem: If you ask the AI a hard math or logic question and force it to give an answer immediately, it usually blurts out the wrong answer.
The Trick: Developers tell the AI to write out its steps before giving the final answer (asking it to "think step-by-step").
The Result: By forcing the AI to type out its thought process first, it actually guides itself to the right answer instead of just making a blind guess
