---
title: shadcn
publish: true
date created: 2026-09-10
tags:
  - frontend
  - basic
  - database
  - codeless
---
**shadcn/ui** is a collection of **reusable UI components** for frontend applications.

It gives you things like:

- Buttons
    
- Inputs
    
- Dialogs/modals
    
- Dropdown menus
    
- Cards
    
- Tables
    
- Tabs
    
- Forms
    
- Toasts
    
- Tooltips
    

But there's an important distinction:

> **shadcn/ui is not really a traditional component library.**

Instead of installing a package containing components that you mostly treat as a black box, shadcn gives you **the component's source code**, which gets added to your project so you can modify it.

### Traditional component library

For example, conceptually:

```text
Your project
    ↓
install UI library
    ↓
<Button />
```

The implementation of `Button` lives inside the library.

You generally use its API:

```jsx
<Button>Save</Button>
```

---

### shadcn/ui

With shadcn:

```text
Your project
    ↓
add Button
    ↓
src/components/ui/button.tsx
```

Now the component's code is **in your project**.

You can open it and change it.

```text
src/
└── components/
    └── ui/
        ├── button.tsx
        ├── dialog.tsx
        ├── input.tsx
        └── dropdown-menu.tsx
```

So if you don't like how the button works, you can modify the component yourself.

---

## What does shadcn use?

shadcn/ui is built around technologies such as:

```text
React
   +
Tailwind CSS
   +
Radix UI
   +
TypeScript
```

For example, you might write:

```tsx
<Button variant="destructive">
  Delete
</Button>
```

and get a nicely styled button without having to build all the accessibility and interaction behavior yourself.

---

## Why do people like it?

Imagine you're building your task manager.

Without a UI library, you might have to build:

```text
Button
Modal
Dropdown
Tooltip
Select
Tabs
Toast
Table
```

and handle all their styling, keyboard behavior, accessibility, states, etc.

With shadcn:

```text
shadcn
  ↓
ready-made components
  ↓
copy into your project
  ↓
customize them
```

So you get a **starting point**, rather than being locked into someone else's component implementation.

---

## One important distinction

Don't confuse:

```text
shadcn/ui
```

with:

```text
Tailwind CSS
```

They are different.

**Tailwind** is a CSS utility framework:

```html
<button class="rounded-md px-4 py-2">
```

**shadcn/ui** provides higher-level components:

```jsx
<Button>Save</Button>
```

A simplified picture is:

```text
Your application
       ↓
  shadcn components
       ↓
   Radix behavior
       ↓
   Tailwind styling
       ↓
       CSS
```

### In one sentence

> **shadcn/ui is a set of well-designed, customizable UI component source code that you add directly to your project rather than treating as a black-box component library.**


---
[[Frontend]]
[[My-Journey-In-Codeless]]