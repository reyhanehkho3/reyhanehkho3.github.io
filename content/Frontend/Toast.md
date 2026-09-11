---
title: Toast
publish:
date created: 2026-09-11
tags:
  - frontend
  - codeless
---
A **toast** is a small temporary notification that appears on the screen to tell the user that something happened.

For example:

```text
┌─────────────────────────────┐
│ ✓ Post created successfully │
└─────────────────────────────┘
```

It usually disappears automatically after a few seconds.

### Common uses

```text
✓ Saved successfully
✓ Password changed
✓ Post created

✕ Failed to save
⚠️ Session expired
```

It's called a **toast** because it briefly "pops up" and then disappears.

---

## What is Sonner?

**Sonner** is a **React library for creating toast notifications**.

Instead of building the toast UI and behavior yourself, you can do something like:

```jsx
import { toast } from "sonner";

toast.success("Post created successfully");
```

Or:

```jsx
toast.error("Failed to create post");
```

Sonner handles things like:

- displaying the notification
    
- positioning it
    
- animations
    
- automatically dismissing it
    
- multiple notifications
    
- success/error styles
    

### Typical setup

You usually add a `<Toaster />` somewhere near the root of your application:

```jsx
import { Toaster } from "sonner";

function App() {
  return (
    <>
      <Toaster />
      <YourApp />
    </>
  );
}
```

Then anywhere in your app:

```jsx
toast.success("Saved!");
```

### Toast vs Sonner

The important distinction is:

```text
Toast
  ↓
UI pattern / concept

Sonner
  ↓
Library that implements toast notifications
```

So if a project says:

> "Use Sonner for notifications"

it basically means:

> **Use Sonner to show temporary toast messages to the user.**


---
[[My-Journey-In-Codeless]]
[[Frontend]]