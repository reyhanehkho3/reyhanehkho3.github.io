---
title: CPU
publish: true
date created: 2026-11-11
tags:
  - basic
  - hardware
---
AMD64 and ARM64 are two different CPU architectures. They determine what kind of processor a computer uses and which compiled software it can run.

The main difference is how the CPU is designed.

## 1. AMD64 (x86_64)

AMD64 = x86-64

- Originally developed by AMD.
    
- Uses the x86 instruction set, extended to 64-bit.
    
- Common in traditional desktop PCs, laptops, and servers.
    
- Used by Intel and AMD processors.
    

Examples:

- AMD Ryzen processors
    
- AMD EPYC server processors
    
- Intel Core processors
    
- Intel Xeon processors
    

Despite the name AMD64, Intel CPUs also support AMD64.

## 2. ARM64 (AArch64)

ARM64 = 64-bit ARM architecture

- Based on ARM's instruction set.
    
- Designed with power efficiency in mind.
    
- Common in smartphones, tablets, and increasingly laptops and servers.
    

Examples:

- Apple M1, M2, M3, M4, M5
    
- Qualcomm Snapdragon processors
    
- AWS Graviton
    
- Ampere server processors
    

## 3. What's the practical difference?

|Feature|AMD64|ARM64|
|---|---|---|
|Architecture|x86-64|ARM|
|Power efficiency|Generally lower|Generally higher|
|Performance|Excellent|Excellent|
|Compatibility|Broad traditional PC software support|Requires ARM-compatible software or emulation|
|Common usage|PCs and servers|Phones, Macs, servers|

## 4. Why do you see these options when downloading software?

For example, when downloading Docker images or Linux applications, you might see:

linux/amd64

(Most traditional PCs)

Software compiled for AMD64 processors.

--

linux/arm64

ARM devices

Software compiled for 64-bit ARM processors.

If you download the wrong architecture, the application might not run, unless an emulation layer is available.

## 5. How do you check which one your Ubuntu uses?

Run:

```
uname -m
```

Possible results:

```
x86_64    → AMD64
aarch64   → ARM64
```

You can also run:

```
lscpu
```

Look for `Architecture`.

One important thing to remember: AMD64 doesn't mean you must have an AMD processor. An Intel processor can be AMD64 too.

---
[[Backend]]