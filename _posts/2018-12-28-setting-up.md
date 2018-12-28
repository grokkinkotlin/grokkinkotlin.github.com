---
title: "Setting Up"
layout: post
---

I'm working on a MacBook Pro which is running MacOS Mojave (10.14.2).

I downloaded the latest binary release (`go1.11.4`) from the [Golang site](https://golang.org/dl/) and installed it at the default location (`/usr/local/go`).

I tested my install by following the [documentation at golang.org](https://golang.org/doc/install#testing).

Based on a recommendation from a friend I started to follow the steps laid out in ["How to Start a Go Project in 2018"]().  This entailed; explicitly setting the `GOPATH` environment variable explicitly (I added `export $GOPATH="/Users/[my username]/go"` to the bottom of my `~/.zshrc` file), adding the `$GOPATH/bin` directory to my `$PATH` (I added `export PATH="$PATH:$(go env GOPATH)/bin"` to the bottom of my `~/.zshrc` file).

