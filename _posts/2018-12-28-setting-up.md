---
title: "Setting Up"
layout: post
---

## Hardware, OS and Shell

I'm working on a MacBook Pro which is running MacOS Mojave (10.14.2).  My shell of choice is Z, made all glorious by [oh-my-zsh](https://ohmyz.sh/).

## Installation

I downloaded the latest binary release (`go1.11.4`) from the [Golang site](https://golang.org/dl/) and installed it at the default location (`/usr/local/go`).

I tested my install by following the [documentation at golang.org](https://golang.org/doc/install#testing).

## Configuration

Based on a recommendation from a friend I started to follow the steps laid out in ["How to Start a Go Project in 2018"](https://boyter.org/posts/how-to-start-go-project-2018/).  

This entailed; 

Explicitly setting the `GOPATH` environment variable explicitly (I added `export $GOPATH="/Users/[my username]/go"` to the bottom of my `~/.zshrc` file), 

Adding the `$GOPATH/bin` directory to my `$PATH` (I added `export PATH="$PATH:$(go env GOPATH)/bin"` to the bottom of my `~/.zshrc` file).

It seems that the defaults of this setup has changed over the course of Golang's evolution because an old book I have from 2012; "The Way to Go" by Ivo Balbert; mentions a bunch of other variables which are still in the go environment but seem to have less precedence.  Ivo also wants me to have my Golang programs in a different location, and finally, he kicks everything off by cloning the language source and building it.  Luckily this isn't mandatory.