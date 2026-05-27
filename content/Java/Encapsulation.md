---
title: Encapsulation
publish: true
date created: 2026-05-24
tags:
  - java
---
In java we have 4 modifiers to manage access.
## public
Visible for all classes.

## private
Only visible to the class it's in.

## default
Only visible to the class and package it's in.

## protected
Only visible to the classes of that package and the classes that inherit from it.
```java
class A{
	protected String str = "Hello";
}
class B{
	a = new A();
	System.out.print(a.str);
}
```
But this wouldn't work because we can't get access to str.



[[Java]]
