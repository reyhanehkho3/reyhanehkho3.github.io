---
title: Reflection
publish: true
date created: 2026-08-01
tags:
  - java
---
A procedure to go through and fix a class in runtime. It is used to test and debug codes in many IDEs. `java.lang.Class` has many method that can be used to have information about a class, debug and change the runtime behavior of a class. `java.lang` and `java.lang.reflect` present some classes for Reflection in java.
### Examples:
- `public String getName()`: name of the class. 
- `public static Class forName(String className)`: finds the class and returns an object by the type of that Class. (also can throw an exception)
- `public Object newInstance()`: returns a new instance of a class.
- `getConstructors()`: returns an array of constructors with Public access.
- `getDeclaredMethods()`: the methods of the class. By using this method and `invoke()` we can run the methods of a class. (used for running private methods of a class via Reflection)
- `getDeclaredClasses()`: the classes inside this class.


### Note:
We can break Encapsulation with Reflection. So the security is in danger. It is also slow. 



---
[[java]]