---
title: "Quartz Setup"
publish: true
date created: 2026-05-11
---
This is an explanation of how I sat up this site using [Quartz][https://github.com/jackyzha0/quartz.git]. (I use Arch btw)
I was going to use nodejs and npm so I had to make sure that I had them installed. Before that, I updated my system so that they would work properly:

```
sudo pacman -Syu
```

Fun fact, when I was trying to update my system, I got errors as "invalid or corrupted package". To fix this, I updated my keyring:

```
sudo pacman -Sy archlinux-keyring && sudo pacman -Su
```

As being in Iran suggests, I didn't have access to the global Internet, so I used Arvan's mirror:

```
Server = https://mirror.arvancloud.ir/archlinux/$repo/os/$arch
```

Then:

```
sudo pacman -S nodejs
```

```
sudo pacman -S npm
```

First, I cloned its github page:

```
git clone https://github.com/jackyzha0/quartz.git
```

Then entering the quartz folder:

```
cd quartz
```

Installing dependencies:

```
npm i
```

This showed some options while create my digital garden:

```
npx quartz create
```

Now building it:

```
npx quartz build --serve
```

So far I could see how it turned out clicking on:

```
http://localhost:8080
```

Since Quartz is to upload .md files (or at least that's what I think) I use obsidian to write new posts. Going to the content folder, I saw that there is an index file, and following its structure, I wrote other posts and going to `quartz.config.ts` allowed me to change the title. 
