---
title: RAG
publish: true
date created: 2026-08-13
tags:
  - AI
  - Agent
  - codeless
---
**Definition:** A method in which relevant information is retrieved from an external source before or during response generation and provided to the model.

**Simply put:** Instead of relying only on what the model already knows, **it first finds relevant information and then answers based on it**.

**Examples:**

1. Question about internal company documentation → search Docs → answer.
2. Question about project code → retrieve relevant files → analyze.
3. Question about company policies → search Policies → answer.


---

To understand **RAG** (Retrieval-Augmented Generation), it helps to start with a simple problem.

**The Problem:** Large Language Models (like ChatGPT) are incredibly smart, but they have a major flaw: **their knowledge is frozen in time.** They only know what they learned during training. If you ask about today's news, a private company document, or a specific email, the AI will either make something up (a "hallucination") or say it doesn't know.

**The Solution:** RAG is a technique that fixes this by giving the AI a "cheat sheet" to read *before* it answers.

---

### The 3-Step Process of RAG

Imagine you are taking a closed-book history test, and suddenly the teacher lets you use your textbook. Here is how RAG works:

**Step 1: Retrieve (Finding the right pages)**
When you ask the AI a question, it doesn't just guess. First, it takes your question and searches through a large database (like a company's internal files, a legal document library, or the live internet). It finds the 5 to 10 most relevant pieces of text that contain the answer.

**Step 2: Augment (Adding the cheat sheet)**
The AI takes your original question and literally pastes the retrieved text right in front of it. So, the new prompt becomes: *"Using only the following provided texts, answer this question: [Your Question]"*

**Step 3: Generate (Producing the final answer)**
The AI reads the provided context and generates a fluent, natural-sounding answer based *specifically* on that data. If the data isn't there, the AI says "I don't know" rather than making something up.

---

### Why is RAG a Big Deal?

RAG completely changed how businesses use AI. Here is why:

| Without RAG (Traditional AI) | With RAG |
| :--- | :--- |
| **Outdated knowledge** (Trained on data from 2023). | **Up-to-the-minute knowledge** (Can query live databases or today's news). |
| **"Black Box"** (You don't know where it got the info). | **Verifiable** (It can cite the source document, like "According to page 4 of the contract..."). |
| **Expensive to retrain** (Retraining an AI costs millions of dollars). | **Cheap to update** (Just add a new PDF to the database; no retraining needed). |
| **Hallucinates** on niche topics. | **Grounded** in facts provided by you. |

---

### A Real-World Example

- **Without RAG:** You ask, *"What is the company vacation policy?"* The AI hallucinates and says, *"Employees get 30 days."* (Wrong).
- **With RAG:** You ask the same question. The system searches your company's internal HR drive, finds the "Employee Handbook 2026.pdf," reads the vacation section, and answers: *"According to the 2026 handbook, employees get 15 days of PTO."* (Correct, and you can click the link to verify).

---

### How it Works Technically (In Plain English)

To search a massive database in a fraction of a second, RAG uses **embeddings** (mathematical representations of text). 

1. The system converts your question into a "vector" (a long list of numbers).
2. It compares this to millions of other vectors in its database to find the closest mathematical match (this is called **semantic search**—it finds *meaning*, not just exact keywords).
3. It returns the matching text chunks and feeds them to the AI.

---

### Quick Summary of Use Cases
- **Customer Support:** Chatbots that answer questions based on your specific product manuals.
- **Healthcare:** AI that summarizes a specific patient's medical history without guessing.
- **Finance:** Analysts asking questions about quarterly earnings reports buried in 500-page PDFs.

**The golden rule of RAG:** It doesn't make the AI *smarter*; it gives the AI *access to the right book at the right time*.


### **Agentic RAG vs. Ordinary RAG**

In ordinary RAG, retrieval is performed almost always and through a fixed path. In Agentic RAG, however, the agent decides:

- Is retrieval needed at all?
- Which source should be used?
- Should the query be rewritten?
- Is the result sufficient and relevant?
- Is a fallback to SQL, web search, or human input needed?

**Example fallback flow:**
Internal KB → relevance check → rerank → if insufficient: approved web/API → cite → answer




### **An important security pitfall in RAG**

Authorization must be applied *before* retrieval (or with metadata filtering). Retrieving relevant documents does not mean the user is authorized to see them, we must not retrieve confidential documents in the first place, rather than hoping the prompt won't expose them. Also, the retrieved text is untrusted input and may contain prompt injection.

---
[[AI]]
[[Agent]]
[[My-Journey-In-Codeless]]


