---
title: HTML & CSS
publish: true
date created: 2026-06-03
tags:
  - frontend
---
## HTML
- HyperText Markup Language
- It tells the web browser what content is on the page.
### Syntax
- HTML uses **tags** enclosed in angle brackets (`< >`). Most tags come in pairs: an opening tag to start the element, and a closing tag (with a forward slash `/`) to end it.
```html
<h1>This is a Main Heading</h1>
<p>This is a paragraph of text on the website.</p>
<button>Click Me!</button>
```

It defines the **structure/content** of a webpage.

Think of HTML as the skeleton of the page.

```
<h1>My Tasks</h1>
<p>Welcome back!</p>
<button>Logout</button>
```

This creates:

```
My Tasks
Welcome back!

[ Logout ]
```

### Example 1

A login form:

```
<form>
  <input type="email">
  <input type="password">
  <button>Login</button>
</form>
```

### Example 2

A task:

```
<div>
  <h2>Learn APIs</h2>
  <p>Study HTTP requests and responses.</p>
</div>
```

**Simple idea:**

> HTML = What exists on the page?


## CSS
- CSS is a **style sheet language**. It takes the raw structure of HTML and makes it look visually appealing. Without CSS, every website would look like a plain Microsoft Word document from 1995.
- CSS works by targeting HTML elements and applying rules to them using **selectors** and **declarations**.

### Syntax
```CSS
/* This targets all <p> tags and changes their look */
p {
  color: darkblue;
  font-size: 16px;
  line-height: 1.5;
}

/* This targets a button and changes its background color */
button {
  background-color: #ff4757;
  color: white;
  border-radius: 5px;
}
```


---
[[Frontend]]