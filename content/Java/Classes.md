---
title: Classes
publish: true
date created: 2026-05-28
---
## Inner Classes / nested classes
It lets us to put the related classes together in a group and have a cleaner code.

First we need to make an object from the outer class and then use to to make an object from the inner class.
```java
class Outer{
	//code for the outer class
}
class Inner{
	//code for the inner class
}
public class Test{
	public static void main(String args[]){
		Outer s = new Outer();
		Outer.Inner i = s.new Inner();
		//the rest of the code
	}
}
```

One of the privileges of this kind of structure is that we can get access to the attributes and methods of the outer class.
```java
class Outer{
	String s = "Hello";
}
class Inner{
	public String message(){
		return s;
	}
}
public class Test{
	public static void main(String args[]){
		Outer s = new Outer();
		Outer.Inner i = s.new Inner();
		System.out.println(s.message);
	}
}
//output: Hello
```

[[java]]