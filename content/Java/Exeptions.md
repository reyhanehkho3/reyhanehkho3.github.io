---
title: Exeptions
publish: true
date created: 2026-05-28
---
### **Checked Exceptions**

- **Must be handled** at compile time (try-catch or throws)    
- Extend `Exception` class (but not `RuntimeException`)
- Represent **recoverable** conditions
- Enforced by the compiler

### **Unchecked Exceptions**

- **Not required** to be handled at compile time
- Extend `RuntimeException`
- Represent **programming errors** or unrecoverable conditions
- Compiler doesn't enforce handling

[[java]]