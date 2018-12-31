---
title: "Hello 世界"
layout: post
---
{% newthought "I'm starting my Golang journey" %} with Donovan and Kernighan's "[The Go Programming Language](https://www.gopl.io/)" (2016).  Why? Becuase it's a text which not only starts at the point where I currently find myself skills-wise (long-term dev experience with Java and heavy sojourns into other languages but nothing to speak of in the systems-programming space) but it also reminds me of the first ever programming book I bought; "[The C Programming Language](https://www.cprogramming.com/books/ritchie.html)" by Kernighan and Ritchie.  {% sidenote 'sn-id-whatever' "It made little sense to me at the time, and the C code I wrote was _terrible_, but the nostalgia is still strong, and Kernighan (and Donovan) can write on languages very clearly." %}

Donovan and Kernighan start thier journey into Golang with the standard "Hello ..." construct, and immediately there is a lot to take note of.

## The Golang Toolchain
Golang is compiled.  You go that with the `go` command and its sub-commands.  There seem to be many of them, but here we see `run` and `build` (which builds a platform-specific executable that can be run without the `go` environment being installed.)

## Unicode
You can see from the title of this post that we're bidding hello in Japanese.  Support for Unicode is native in Golang.  Nothing new having come from the Java world, but nice to know.

## Packages and Standard Libraries
Everygthing is packaged.  Our code is packaged, and so are the Standard Libraries which are `import`ed.  So far so unexpected. 

However there is a concept that is new to me; there is a special package called `Main` which contains entry points to your Golang programs. When complied, `Main` packages create standalone, executable programs.

## Clean Syntax
No semicolons required!

## Clean Style
It is Golang style to run `gofmt` and `goimport` on your code.  That ensures all Golang code looks the same, and that there are no rogue (i.e. unused) imports.