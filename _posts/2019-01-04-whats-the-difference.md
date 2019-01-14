---
title: "`x`, `&x` and `*x`; what's the difference?"
layout: post
---
{% newthought "This was a longer post;" %}  But I lost it.  This is a summary to flush what remains from my mental buffers.

Pointers and pointer arithmatic is new to me{% sidenote 'sn-id-whatever' "Although I'm more than conversant with references, the poorer cousin from Javaland" %} so grokking them as and when they come up is important.

There's a lot in the two appearances of the concept in Donovan and Ritchie's The Go Programming Language (2016).{% sidenote 'sn-id-whatever' "On page 24, and again on pages 32-34" %}.  I wanted to go slightly slower than they did, and make a few points super-clear.

They show us what's happening with this code (page 32):

    x := 1
    p := &x         // p(ointer) of type *int (pointer to an int). Points to x
    fmt.Println(*p) // prints "1"

When I first read this I thought (incorrectly) that `&x` and `*x` were variables.  Wrong.  The `x` here is the variable.  The `&` is an operator, which obtains the pointer value - the memory address.  We can start with our printing again and prove it:

	x := 1
    fmt.Println(x)  // prints "1"
    fmt.Println(&x) // prints "0xc0000180a0" 

The other misconception I had was that `*x` acted on `x`.  It doesn't.  If you try that you get a compilation error (which makes a lot more sense when you realise the `*` is also an operator).  You need to call it on a pointer type (e.g. of type `*int`) and it will give you back the variable that this points to.  Let's do some more printing, starting at the beginning yet again, and prove it:

    x := 1
    fmt.Println(x)  // prints "1"
    fmt.Println(&x) // prints "0xc0000180a0"
    fmt.Println(*x) // prints "1"
    p := &x         // p(ointer) of type *int (pointer to an int). Points to x
    fmt.Println(p)  // prints "0xc0000180a0"
    fmt.Println(*p) // prints "1"

So to summarise, pointers are a single new thing, which you can work with using two operators; the first, `&`, gets the pointer of type `*type` from the variable.  The second, `*` gets the variable from the pointer.

As a conclusion, there is one thing which doesn;t sit entirely well with me and that's the fact that `&` gets you something of type `*type` rather than `&type`. Its a small thing, but may have been at the root of my mis-grokking of all this.