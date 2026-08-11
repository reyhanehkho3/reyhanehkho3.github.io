---
title: Agent
publish: true
date created: 2026-08-11
---
If an **LLM** (Large Language Model) is the **"brain"**—a powerful engine that processes information and generates text—then an **Agent** is the **"brain + hands + eyes + memory."**

An Agent is an AI system that uses an LLM as its core reasoning engine, but it is given the ability to **take action**, **use tools**, and **make decisions autonomously** to achieve a specific goal.

Official definition: **An AI Agent is a system that perceives its environment, uses an LLM to reason and plan, and takes actions to accomplish a goal without needing step-by-step human instructions.**

### How does an Agent actually work? (The Loop)

An Agent operates in a continuous **"Reasoning-Action-Observation" loop**:

1. **Reason (Think):** You give it a goal. The LLM brain breaks that goal down into a step-by-step plan.
    
2. **Act (Do):** It decides it needs external information or the ability to change the real world. So, it calls a **Tool**.
    
3. **Observe (Look):** It gets the result back from the tool.
    
4. **Repeat:** It looks at the result, updates its plan, and takes the _next_ action. It only stops when it decides the original goal has been successfully completed.

### What "Tools" does an Agent use?

This is the key to an Agent. Tools are functions or APIs that the Agent can call. Examples include:

- **Web Search / Browser:** To look up real-time information (stock prices, today's news).
    
- **Calculators / Code Interpreters:** To do precise math or run data analysis.
    
- **External Apps:** To send emails, create calendar invites, or update a database.
    
- **APIs:** To connect to external software, like booking a flight via Expedia or ordering food via DoorDash.
    
- **File System:** To read, write, or edit documents stored on your computer.

### A Real-World Example

Let's say you ask a plain **Chatbot**: _"What is the weather in Tokyo and should I pack an umbrella?"_ It will generate a text reply based on its training data (which is probably outdated) and stop.

Now, let's say you ask an **Agent**: _"My flight to Tokyo lands at 3 PM tomorrow. Book me a car to my hotel, and if it's going to rain, email my boss to say I might be late."_

Here is what the Agent does automatically:

1. **Thinks:** _"I need to know the time, the weather, and my boss's email."_
    
2. **Action 1:** Calls the **Weather API** to get the forecast for 3 PM tomorrow in Tokyo. (Observation: _It will rain_).
    
3. **Action 2:** Calls the **Calendar API** to find your boss's email address.
    
4. **Action 3:** Calls the **Email API** to draft and send the email about possibly being late.
    
5. **Action 4:** Calls the **Ride-Booking API** to reserve a car from the airport to your hotel.
    
6. **Observes:** _"Reservation confirmed."_
    
7. **Final Reply to you:** _"Done! I booked your car and emailed your boss about the rain."_





---
## Questions
what is harness?

[[Java]]
