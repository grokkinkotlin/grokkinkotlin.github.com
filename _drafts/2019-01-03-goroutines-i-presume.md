---
title: "Goroutines, I presume"
layout: post
---
{% newthought "It's in Chapter 1" %} of Donovan and Ritchie's "The Go Programming Language" (2016) that we first encounter the famous goroutines.

We learn that everything we've done leading up to it has been within a goroutine - the default, `main` one.  Now we see that we can create more using the `go` keyword.

On their own, goroutines might not be over-useful, but when we connect them together; then all kinds of madness could ensue.  We do this via channels which we create using the keyword `make`.{% sidenote 'sn-id-whatever' "Not to be confused with the UNIX `make` command." %}  Channels allow us to pass values (NOTE: not references) of a specified type to other goroutines.

The syntax seems a little hairy at first sight.  We're told that:

> when one goroutine attempts to send or receive on a channel, it blocks until another goroutine attempts the corresponding receive or send operation, at which point the value is transferred and both goroutines proceed.
<cite>Donovan and Ritchie, The Go Programming Language, (2016) pp.18</cite>

In order to achive this we have to "`make`" our channel

	ch := make(chan string)

We also have to create new goroutines

    go fetch(url, ch) // start a goroutine

And from each of these goroutines send a value on channel `ch`

    ch <- fmt.Sprint(err) // send to channel ch

Which are received (and printed) by channel `main`

	fmt.Println(<-ch) // receive from channel ch

So why do I say "hairy"?  I'll admit, I used to hate symbols like "`<-`" and "`<=`" but I got over that.  What seems a little arbitrary here (and perhaps I'm just being hyper-sensitive knowing that `gofmt` is watching my every move) is the space _before_ the arrow in constructs like `ch <-` but the lack of a space _after_ it, for example, `<-ch`.

I'm not saying it's bad (and this post is a great example of my blogging something to make it really solid in my head before moving on) but I'll be watching as I keep reading to see if there is a point to this.