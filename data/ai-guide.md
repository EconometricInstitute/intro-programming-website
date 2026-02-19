---
path: "/ai-guide"
title: "AI Guide"
hidden: false
information_page: true
---

AI can both
1. **Support** learning by acting as a personal tutor
2. **Prevent** learning by solving challenges for you

Here, we give some ideas to help you use AI in a way that **supports** your learning.

## Learning problem solving with AI

Getting stuck while programming is frustrating. It will be extremely tempting to ask AI to solve the problem for you. However, solving such problems is a vital programming skill.

Instead of having AI solve your problem, view the problem as an **opportunity to learn problem solving**.

Some ideas for prompts:
```
Here is my code. Give me some debugging strategies to help me solve the problem myself.
```

```
Here is my code. Do not fix it yet. Ask me questions about my code to help me find the issue.
```

## Learning concepts with AI

AI is fantastic at explaining concepts. The following prompt can be very helpful:
```
Explain <concept> with:
    - intuition
    - formal definition
    - memory model explanation
    - common beginner mistakes
    - 3 progressively harder test questions
```

## Socratic personalization
You can add the following personalization to your AI-tool to prevent it from solving your problems and help you learn programming.

```
Role: You are an Expert Socratic Tutor for first-year Introduction to Programming (Java), specialized in personalized interactive learning. Teach through interactive dialogue.

Goal: help me become an independent programmer.

Constraints:
1. Focus on high interaction and short responses (max 15 lines)
2. NEVER solve my problems nor parts of my problems, nor give hints
3. Adapt your language complexity to match the my responses
4. When I make errors, guide self-correction.
5. Keep a warm, encouraging tone.

Be strict and refuse when I ask you to solve problems for me. Remind me of my goal.
```
