---
title: Component
publish:
date created: 2026-09-10
tags:
  - frontend
  - basic
  - codeless
---
# Component Architecture and Composition

### What is it?

**Component architecture** is about deciding **how to split your frontend into components** and how those components should communicate.

Instead of putting an entire page into one huge component, you divide it into smaller pieces.

For example, imagine a task-management application:

```
TaskPage
├── TaskHeader
├── TaskFilters
├── TaskList
│   ├── TaskItem
│   ├── TaskItem
│   └── TaskItem
└── CreateTaskButton
```

Each component has a specific responsibility.

### Presentational component

A **presentational component** mainly displays data.

For example:

```
<TaskCard
  title="Fix login bug"
  status="IN_PROGRESS"
/>
```

`TaskCard` doesn't necessarily know where the task came from or how it is saved.

It just receives data and displays it.

Think:

```
Data → Component → UI
```

### Component with logic

A component with logic might fetch tasks:

```
TaskPage
   ↓
fetch tasks from API
   ↓
store tasks
   ↓
give tasks to TaskList
   ↓
TaskList displays them
```

So you might have:

```
TaskPage
  → handles API + state

TaskList
  → displays a list

TaskCard
  → displays one task
```

### Composition

**Composition** means building bigger components by combining smaller components.

For example:

```
<TaskPage>
    <TaskHeader />
    <TaskFilters />
    <TaskList>
        <TaskCard />
        <TaskCard />
    </TaskList>
</TaskPage>
```

Instead of creating one enormous `TaskPage` containing everything.

### Example 1

Bad:

```
Dashboard.vue
  1500 lines
  ├── sidebar
  ├── navbar
  ├── tasks
  ├── users
  ├── forms
  ├── API calls
  └── notifications
```

Better:

```
Dashboard.vue
├── Sidebar.vue
├── Navbar.vue
├── TaskList.vue
├── UserList.vue
├── CreateTaskForm.vue
└── NotificationPanel.vue
```

### Example 2

A reusable button:

```
<AppButton>
  Create Task
</AppButton>
```

You can reuse it:

```
<AppButton>Create Task</AppButton>
<AppButton>Delete Task</AppButton>
<AppButton>Save Changes</AppButton>
```

### Main idea

> **Components should have clear responsibilities and be reusable where it makes sense.**

Don't split components just for the sake of having many files. Split them when doing so makes the code easier to understand, reuse, or maintain.



---
[[Frontend]]
[[My-Journey-In-Codeless]]