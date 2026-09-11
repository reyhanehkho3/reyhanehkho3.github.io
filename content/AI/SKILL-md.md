---
title: SKILL.md
publish:
date created: 2026-09-11
tags:
  - AI
  - Agent
  - codeless
---
`SKILL.md` is usually a **documentation/instruction file for an AI agent or coding tool**.

Think of it as:

> **“Here is how you should perform this particular type of task.”**

### Example

Suppose a project has:

```text
skills/
├── testing/
│   └── SKILL.md
├── database/
│   └── SKILL.md
└── frontend/
    └── SKILL.md
```

The `testing/SKILL.md` might contain instructions such as:

```md
# Testing Skill

When adding a feature:

1. Write tests first.
2. Run the existing tests.
3. Implement the feature.
4. Run the tests again.
5. Add a regression test for fixed bugs.
```

An AI coding agent can read that file when it needs to perform testing-related work.

### Why `SKILL.md`?

It lets you **teach an agent a reusable workflow** without putting all the instructions into every prompt.

For example:

```text
Your project
│
├── source code
├── tests
└── skills/
    ├── testing/SKILL.md
    ├── frontend/SKILL.md
    └── api/SKILL.md
```

Then you can tell the agent:

> "Use the testing skill and add tests for this feature."

The agent reads the relevant `SKILL.md` and follows its instructions.

### `SKILL.md` vs `README.md`

They're different in purpose:

**README.md**

> Explains the project to **humans**.

```text
What is this project?
How do I install it?
How do I run it?
What does it do?
```

**SKILL.md**

> Gives **instructions/workflows to an agent** for performing a specific kind of task.

```text
When doing X:
1. Do A
2. Check B
3. Run C
4. Follow these rules
```

So a useful mental model is:

```text
README.md  → "Understand this project"
SKILL.md   → "Here's how to perform this kind of work"
```

The exact behavior depends on the **agent/tool that uses the `SKILL.md` convention**; `SKILL.md` itself isn't a programming language or a special file type built into Git.


It must have name and description.


 **A `SKILL.md` can describe or point to templates and scripts**, but they are usually separate files.

For example:

```text
my-skill/
├── SKILL.md
├── templates/
│   ├── component.tsx
│   └── test.ts
└── scripts/
    ├── setup.sh
    └── validate.py
```

### `SKILL.md`

The skill instructions might say:

```md
# Frontend Skill

When creating a new component:

1. Use the template in `templates/component.tsx`.
2. Add a test using `templates/test.ts`.
3. Run `scripts/validate.py`.
```

So you can think of it as:

```text
SKILL.md
   │
   ├── instructions
   │
   ├── → templates/
   │      └── reusable starting files
   │
   └── → scripts/
          └── executable automation
```

### Why use them together?

It makes a skill more powerful and consistent.

Instead of telling the agent:

> "Create a React component with these 20 rules."

you can give it a **template** that already follows the rules.

And instead of telling it to manually perform repetitive checks, you can give it a **script**:

```bash
./scripts/validate.sh
```

So:

- **`SKILL.md`** → tells the agent **what to do and how**
    
- **Templates** → give it **reusable starting material**
    
- **Scripts** → let it **automate actions/checks**
    

The important point is that **`SKILL.md` itself doesn't automatically contain templates or scripts**. The skill can include them as supporting resources, depending on the agent/tool's skill system.

We can even have a skill for making skills.

---
[[AI]]
[[Agent]]
[[SKILL-md]]