1. Provide the context first: Who are you, what you want to achieve, your depth
2. Use delimiters
3. Be Specific
4. Assign roles, output format, task to the model (You are a tech educator who specializes in explaining complex topics in simple, relatable language. Your audience is made up of adults with no technical background)
5. Provide relevant example
6. Step by step execution or chain of thought
7.  Breakdown the prompt to components

# Prompting Techniques Cheat Sheet

## Zero-shot

Ask directly, no examples. Best for simple, well-defined tasks.

**Example:**

> Classify the sentiment as Positive, Negative, or Neutral: "The delivery was fast but the packaging was completely crushed."

---

## One-shot

Provide one example to set the pattern.

**Example:**

> Convert job titles to casual versions. Example: Senior Vice President of Marketing → Marketing boss Now convert: Chief Financial Officer

---

## Few-shot

Provide 2–5 examples to establish format or logic.

**Example:**

> Extract the action item and owner from each note. "Sarah will send the revised budget by Thursday." → Action: Send revised budget | Owner: Sarah "James needs to book the conference room." → Action: Book conference room | Owner: James "Priya will follow up with the client on Monday." → Action:

---

## Chain-of-thought

Ask Claude to reason step by step before answering. Best for math, logic, and multi-step problems.

**Example:**

> A store sells apples for $1.20 each or 6 for $5.50. What's the cheapest way to buy exactly 14? Think step by step before answering.

---

## Role-based

Assign a persona to shape tone, vocabulary, and perspective.

**Example:**

> You are a blunt senior software engineer. Give a no-nonsense code review focused only on correctness, readability, and performance. Review this function: [code]

---

## Context-rich

Load Claude with background: audience, constraints, goals, format.

**Example:**

> Context: First-time founder, pre-seed, B2B SaaS for law firms, targeting angels, under 150 words, end with a call ask. Write a cold outreach email to an angel investor who has backed legal-tech startups.

---

## Completion-style

Start the response yourself to lock in tone or structure.

**Example:**

> Write a product announcement. Continue from: "For years, coordinating meetings has been the tax we pay on collaboration. Today, that changes —"

---

## Combining techniques

Role-based + chain-of-thought + context-rich is often the most powerful combo for complex tasks.