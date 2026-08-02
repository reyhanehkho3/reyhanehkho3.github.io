---
title: Libraries
publish: true
date created: 2026-08-01
---
## Lombok

- Reduces repeated codes by adding Annotations. Auto generating:
	- Getter
	- Setter
	- Constructor
	- equals
	- hashCode
	- toString
- Installing in Maven:
	```XML
	<dependency>
    <groupId>org.projectlombok</groupId>
    <artifactId>lombok</artifactId>
    <version>1.18.30</version>
    <scope>provided</scope>
	</dependency>
	```
## Apache Commons Lang

- Helper for working with strings and numbers and objects.
- Examples:
	- checking if the string is empty or not.
	- reversing, reducing and replacing in strings.
	- working with numbers and converting.
- install in Maven:
```XML
<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-lang3</artifactId>
    <version>3.12.0</version>
</dependency>

```

## Gson

- Converting JSON into Java and vice versa.
- Install in Maven
```XML
<dependency>
    <groupId>com.google.code.gson</groupId>
    <artifactId>gson</artifactId>
    <version>2.10.1</version>
</dependency>

```
- what is سریال سازی و دسریال سازی?

## Logback

- Advance Log. Like saving logs in file or database.
- Install in Maven:
```XML
<dependency>
    <groupId>ch.qos.logback</groupId>
    <artifactId>logback-classic</artifactId>
    <version>1.4.14</version>
</dependency>

```

## Picocli
- Creating CLI tools and auto-generating documents.
- install in Maven:
```XML
<dependency>
    <groupId>info.picocli</groupId>
    <artifactId>picocli</artifactId>
    <version>4.7.5</version>
</dependency>

```