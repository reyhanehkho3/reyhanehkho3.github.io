---
title: Polymorphism
publish: true
date created: 2026-05-28
---
- Polymorphism doesn't exists on the attributes of an object in a class in the runtime.
```java
class Shape{
	public String name = "something"
	public void message(){
		System.out.println("Hola")
	}
}
class Circle extends Shape{
	public String name = "round";
	@Overvide
	public void message(){
		System.out.println("Niha");
	}
}

public class Test{
	public static void main(String args[]){
		Shape p = new Circle();
		System.out.println(s.name);
		p.message();
		Circle s = new Circle();
		System.out.println(s.name);
		s.message();
	}
}
```
The output:
```
something
Niha
round
Niha
```



[[Java]]