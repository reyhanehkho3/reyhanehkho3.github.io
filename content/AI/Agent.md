---
title: Agent
publish: true
date created: 2026-08-11
tags:
  - AI
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


### Architecture of agent
‫Goal -> Inspect -> Plan -> Act with tools -> Observe -> Verify -> Repeat/Finish‬‬


### How to run a project with agent:
- Declare the purpose and the acceptance criteria.
- Ask the agent to inspect th environment and relevant files.
- Ask for a short plan, not just implementation.
- Changes should be small and level-by-level.
- Check the test, diff and the output.
- The work is done when the evidence supports it.


Note: when using git via Agent, never confirm commit/push without reading the diff, checking the secrets and test. (diffs are the changes in the code)


### Types of Agents
- tester.
- reviewer.
- implementer.
- planner.
- explorer.
- orchestrator.

**Separation of roles is only useful when the output boundary, and responsibility are clear.**

- An agent without tools only suggests test. Common tools:
		file and text search, reading/editing, shell, database API, browser, Git, test runner, compiler, and documentation.

or more generally:

**Simple Reflex Agent**
Acts based on the current state and rules like `if condition → action`; it has no state or model of the world. Example: when it detects the keyword "password reset," it executes a fixed password recovery flow.

**Model-Based Reflex Agent**
Maintains an internal state of the environment; when the environment is not fully observable, it makes decisions by taking past context into account.

**Goal-Based Agent**
Chooses actions based on how much they bring it closer to a goal. More flexible, but with a higher risk of unexpected behavior; the goal and boundaries must be clearly defined.

**Utility-Based Agent**
Among multiple possible paths, it selects the option with the highest utility—for example, trading off quality, cost, latency, and risk.

**Learning Agent**
Improves its policy or choices over time through feedback or performance data. In production, one must be cautious about contaminated feedback, drift, and uncontrolled changes in behavior.
### Some concepts

- **Rule:** A permanent and mandatory project directive; for example, style guidelines, the test command, or a prohibition on modifying a certain part of the repo.

- **Memory:** Useful information that is preserved between steps or sessions; it should not replace the source of truth.

- **Skill:** A bundle of specialized instructions and workflow for a recurring type of task.

- **Plugin:** A package that adds capabilities to the environment, such as a tool, skill, or connector.

- **MCP:** A standard contract for connecting an AI host to servers that provide tools and context.

**Key distinction:**
- **Rule** says "how you must behave";
- **Skill** says "with what workflow should you perform this specialized task";
- **MCP** says "how to connect to an external capability";
- **Plugin** is the method for packaging and distributing a capability;
- **Memory** retains previous information.

**Security:** minimal access, sandboxing, allowlisting, tool permissions, secret obfuscation, human approval for destructive operations, and validation of all model-generated inputs.



- When we encounter a project with lots and lots of code, **the goal is not to read all the code;** we need to understand what the user does, how the system processes the request, and where the source of truth is.

**Exploration order:**
1. Manifest, README, and build/test commands;
2. Entry point and top-level structure;
3. Routes or triggers;
4. One real user flow;
5. Data model and external integrations;
6. Related tests;
7. Conventions and a similar feature example.

**Build four maps:**
- **Component Map:** systems and their dependencies;
- **Request Map:** execution path of a request;
- **Data Map:** shape, ownership, and lifecycle of data;
- **Change Map:** if X changes, which points are affected?

**Good questions to ask an Agent:** "Where is the entry point for this flow?", "What is the source of truth for this field?", "Which test documents the expected behavior?", "Where has a similar feature been implemented?" Every claim should be supported by a symbol, path, or test.

**An Agent is useful for** searching call sites, comparing history, analyzing logs, and generating useful tests; but the hypothesis must be confirmed with evidence.

Not every multi-step workflow is an "agent." If the path is fixed and predictable in advance, a pipeline or a machine state is usually cheaper, faster, and more reliable. An agent is valuable when the decision for the next step depends on the context and the results at runtime.

### **Components of an Agentic System**

**1. Engine / Reasoning Model:** Language-based decision-making, tool selection, and response generation.

**2. Goal & Instructions:** Objective, role, constraints, and success criteria.

**3. Tools:** Calendar executor, code calculator, database, search, API, etc.

**4. State:** Current task status, messages, tool outputs, and iteration counter.

**5. Memory:**
- Short-term: History of the current execution/conversation.
- Long-term: Stored preferences or knowledge across sessions.

**6. Planner/Router:** Breaking down the goal into subtasks or selecting the appropriate agent/path.

**7. Retriever:** Fetching relevant context from an external source.

**8. Guardrails & Authorization:** Input/output validation, role-based access control, preventing data leakage.

**9. Evaluator/Critic:** Assessing quality or reflection (preferably with a stopping criterion and iteration cap).

**10. Observability:** Tracing every decision, tool call, error, token usage, latency, and outcome.

**11. Stop Conditions:** Reaching a final response, budget caps, timeout, iteration limits, or need for human approval.

---
## Questions
what is harness?

[[Java]]
