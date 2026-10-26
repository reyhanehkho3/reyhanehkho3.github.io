---
title: Tempreture
publish: true
date created: 2026-10-26
tags:
  - ai
  - agent
---
In AI, temperature is a setting that controls how random or predictable an AI model's responses are.

Think of it as a creativity dial. 🎚️

## How temperature works

Low temperature (0–0.3)

More predictable

The model tends to choose more probable words and produce consistent, focused answers.

Example: explaining a database error or generating structured JSON.

Medium temperature (around 0.7)

Balanced

The model can vary its wording while generally staying focused.

Example: explaining a technical concept in a conversational way.

High temperature (around 1.0–2.0, if supported)

More varied

The model may choose less predictable words and produce more diverse answers.

Example: brainstorming story ideas, creative writing, or generating alternative names.

These ranges are illustrative. The meaning of a particular value depends on the model and API.

## A simple example

Imagine you ask an AI:

> Suggest a name for a task management application.

- Temperature = 0: `TaskFlow`
    
- Temperature = 0.7: `TaskFlow`, `PlanPilot`, or `DailySync`
    
- Temperature = 1.5: It might suggest more unusual names, such as `NebulaTasks` or `QuantumTodo`.
    

These are illustrative outputs, not guaranteed results. Even at temperature 0, some models may not produce identical results every time.

## How does it work technically?

An AI language model predicts the next token (a word or part of a word) by assigning probabilities to possible tokens.

For example, suppose the model predicts the next word after:

> The sky is ...

|Possible token|Probability before temperature|
|---|---|
|blue|70%|
|cloudy|20%|
|dark|10%|

Temperature adjusts how sharply or evenly these probabilities influence the selection.

- Lower temperature: Makes high-probability tokens more dominant.
    
- Higher temperature: Makes lower-probability alternatives more likely to be selected.
    

A simplified mathematical representation is:

\[ P_i = \frac{e^{z_i/T}}{\sum_j e^{z_j/T}} \]

Here:

- \(P_i\) is the adjusted probability of a token.
    
- \(z_i\) is the model's score (logit) for that token.
    
- \(T\) is the temperature.
    

As \(T\) approaches zero, the distribution increasingly favors the highest-scoring token. At \(T=1\), the original softmax distribution is unchanged.

## When should you use each temperature?

|Task|Suggested starting point|
|---|---|
|Structured JSON output|0–0.2|
|Database or technical questions|0–0.3|
|General-purpose chatbot|0.5–0.8|
|Brainstorming ideas|0.8–1.2|
|Creative writing|0.7–1.2|

The best setting depends on the model, and some models ignore temperature or support only specific values.

One important distinction: Temperature controls variation, not intelligence. A higher temperature doesn't make a model smarter or necessarily more creative in a useful way. It can also make answers less consistent or more prone to errors.

If you're configuring an AI agent, a good default is a low temperature for database operations, tool calling, and structured outputs, and a moderate temperature for user-facing explanations.


---
[[Agent]]
[[AI]]