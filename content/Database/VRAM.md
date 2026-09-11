---
title: VRAM
publish: true
date created: 2026-09-11
tags:
  - database
  - etc
---
 **VRAM** stands for **Video Random Access Memory**.

It's the memory used primarily by your **GPU (graphics card)**.

### RAM vs VRAM

```text
CPU
 ↓
RAM
 ↓
General application data

GPU
 ↓
VRAM
 ↓
Graphics / GPU data
```

For example, if you have a GPU with **8 GB VRAM**, that 8 GB is dedicated high-speed memory available to the GPU.

### What uses VRAM?

Things like:

- Game textures
    
- 3D models
    
- Frame buffers
    
- Shaders
    
- High-resolution graphics
    
- AI/ML models
    
- Video processing
    

For a game:

```text
Game
 ↓
GPU
 ↓
VRAM
 ├── Textures
 ├── Models
 ├── Shaders
 └── Frame data
```

### Why does VRAM matter?

Suppose a game needs:

```text
10 GB VRAM
```

but your GPU only has:

```text
8 GB VRAM
```

The GPU may need to move some data between VRAM and system RAM, which can significantly hurt performance.

That's why you might see games saying:

```text
VRAM usage: 7.5 / 8 GB
```

### VRAM vs RAM

A simple analogy:

> **RAM is the workspace for your CPU.**  
> **VRAM is the workspace for your GPU.**

And **VRAM is not the same thing as RAM**—an "8 GB GPU" doesn't mean your computer has 8 GB of total memory. Your computer might have:

```text
System RAM: 32 GB
GPU VRAM:    8 GB
```

for a total of 40 GB of physical memory, but they serve different purposes.

---
[[Database]]