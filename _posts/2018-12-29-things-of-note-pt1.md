---
title: "Things of Note - Part 1"
layout: post
---
## High-Level
As a newer language, Golang benefits from many language developments which went before it.  I pull out some of these which are of particular note in separate sections below, but the "just plain handy" list includes: a package system, first-class functions, lexical scope, a system-call interface, and immutable strings (from The Go Programming Language, pp xiv by Donovan, A. and Kernighan, B.).  It also includes in the platform linting, dependency management, testing, packaging and more.  

## Presumes monorepo-style SCM
## Optimised for large teams

## Managed runtime
Golang takes note of the development in managed runtimes which found popularity with the development of languages such as Java and C# (and their many JRE- and CLR- platform cousins).  Golang also has a managed runtime.  That means you get garbage collection which is a major boon.  The downside is that it's not suitable for real-time projects (although I remember real-time Java so I'm not sure these kind of things are impossible; rather they are likely to require a different style of coding.)

## Cross-platform
The Golang platform is available on many platforms (Unix, MacOs, and Windows) and chip architectures (including ARM). This goes a long way towards ensuring that your code is very likely to be compilable on multiple platforms unchanged. 

## Time-to-Compile
Golang is a compiled language.  But not only that, the designers have focussed on keeping compile-time as low as possible.  If you're coming from a Scala background, that's reassuring.

## Bundling dependencies

## Network-Centric
Golang "takes note of the importance of locality" (from The Go Programming Language, pp xiv by Donovan, A. and Kernighan, B.) but also has first-class concepts for remote communication.

## NOT Object-Oriented