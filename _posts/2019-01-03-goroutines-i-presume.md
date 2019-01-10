---
title: "Goroutines, I presume"
layout: post
---
{% newthought "It's in Chapter 1" %} of Donovan and Ritchie's "The Go Programming Language" (2016) that we first encounter the famous goroutine.

We learn that everything we've done leading up to this point has been running within a goroutine - the default, `main` one.  Suddenly we see we can create more using the `go` keyword. That's cool, but on their own, goroutines can never be super-useful.  When we connect them together however; then all kinds of madness could ensue.  

We do this connecting via channels which we create using the keyword `make`.{% sidenote 'sn-id-whatever' "Not to be confused with the UNIX `make` command." %}  Channels allow us to pass values (NOTE: not references) of a specified type to other goroutines.

To me, the syntax seemed a little hairy at first sight, and that's what I'm going to pick at a tiny bit in this post.  

We're told that:

> when one goroutine attempts to send or receive on a channel, it blocks until another goroutine attempts the corresponding receive or send operation, at which point the value is transferred and both goroutines proceed.
<cite>Donovan and Ritchie, The Go Programming Language, (2016) pp.18</cite>

In order to achive this we have to "`make`" our channel

	ch := make(chan string)

We also have to create new goroutines

    go fetch(url, ch) // start a goroutine

And from each of these new goroutines send a value on channel `ch`

    ch <- fmt.Sprint(err) // send to channel ch

Which are received (and printed) by channel `main`

	fmt.Println(<-ch) // receive from channel ch

So why do I say "hairy"?  I'll admit, I used to hate symbols like "`<-`" and "`<=`"{% sidenote 'sn-id-whatever' "Back in [my Scala days](https://scalaeyeforthejavaguy.blogspot.com/2013/11/many-legibility-wins-and-few-losses.html)." %} but I got over that.  What seems a little arbitrary here{% sidenote 'sn-id-whatever' "perhaps I'm just being hyper-sensitive knowing that `gofmt` is watching my every move." %}" is the space _before_ the arrow in constructs like `ch <-` but the lack of one _after_ it, for example, in `<-ch`. It feels to me like they should both be either one thing or the other format-wise. 

However, I've been on the programming block long enough to know that differences like this are rarely accidental. Rather, they typically point to something far more fundamental which I'm just not aware of yet.  I'm going to keep my eye on things as I read on, and follow up this post if / when I discover anything pertinent.