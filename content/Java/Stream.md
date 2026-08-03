---
title: Stream
publish: true
date created: 2026-05-28
tags:
  - java
---
## Optional
- When using Streams, the stream might not have a result, e.x it might be empty. Java uses `Optional` to see if there any result.
```java
Optional<Integer> max = numbers.stream()
				.max(Integer::compareTo);
max.ifPresent(System.out::println);
//if any number is found, it's gonna be printed. If not, Optional returns empty that can be managed with ifPresent.
//we can alse use `orElse()`
```



---
[[java]]