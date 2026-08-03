---
title: Spring Boot
publish: true
date created: 2026-05-28
tags:
  - java
  - springboot
---
### 🚀 The Accelerator: Spring Boot

Spring Boot is an "opinionated" extension of the Spring Framework. Its main goal is to drastically reduce the boilerplate code and configuration required to set up a Spring application. It does this through **auto-configuration** and **starter dependencies**.

- **Purpose**: To enable you to get a production-ready application up and running with minimal effort, adhering to the principle of "convention over configuration".
    
- **Configuration**: Minimizes manual configuration. It automatically configures your application based on the dependencies you include. It provides `application.properties` or `.yml` files for simple, centralized settings.
    
- **Deployment**: Comes with an **embedded web server** (like Tomcat, Jetty, or Undertow). You can package your application as a self-contained JAR file and run it with a simple `java -jar` command, which is ideal for microservices and cloud-native development.
    
- **How to Think of It**: It's the **quick-start** tool that simplifies Spring development, making it perfect for new projects and microservices.


### Spring Boot VS. Spring Framework
A simple way to see the difference is in how you add dependencies for a web application.

- **With Spring Framework**, you must manually specify each required dependency and its version in your build file, like `spring-web` and `spring-webmvc`.
    
- **With Spring Boot**, you just add one **starter dependency** like `spring-boot-starter-web`. This one entry pulls in all the necessary dependencies (including the embedded Tomcat server) with compatible versions, saving you a lot of time and potential version conflict headaches.


In almost all cases today, Spring Boot is the default and recommended way to start any new Spring project because it is simply an easier and faster way to use the powerful Spring Framework.

---
[[java]]