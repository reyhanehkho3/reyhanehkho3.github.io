---
title: Constructor
publish: true
date created: 2026-05-24
tags:
  - java
---
Inside the constructor of a class we can call another constructor of that class, using `this()`, and it will be called based on the parameters in gets as input. 

```java
class Student{
	public int Age;
	public int grade;
	public int classNumber;
	public Student(int Age, int grade){
		this.Age = Age;
		this.grade = grade;
	}
	public Student(int classNumber){
		this.(0,0);
		this.classNumber = classNumber;	
	}
}
```

[[Java]]
