---
title: Inheritance
publish: true
date created: 2026-05-24
tags:
  - java
---
**If a parent and its child class have a method or attribute by the same name, which one will have priority when called?**
	In this case the child is in priority. In order to access the attributes and methods of the parent class we can use `super`. 
	
```java
class A{
	int a = 0;
}
class B extends A{
	int a = 2;
	public B(){
		System.out.println(a);
		System.out.println(super.a);
	}
}
```
 The fist print will print 2 and the second one will print 0. 
 [[Java]]