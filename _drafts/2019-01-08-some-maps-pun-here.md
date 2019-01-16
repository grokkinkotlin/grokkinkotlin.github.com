---
title: "[Some Maps Pun Here]"
layout: post
---
{% newthought "It's Maps now" %} and there are a few notable nuggets here too.

NUGGET:

> A map lookup using a key that isn't present returns a zero value for its type <cite>The Go Programming Language (2016) Donovan and Ritchie, pp. 94</cite>

Nice, but how do we tell if a map element is really there or not?  Accessing elements actually returns a tuple, the first element of which is the element value (or zero value) and the second is a Boolean.  The Boolean is `true` if the provided key matched, and `false` if you've just got the default, empty value.  That seems pretty cool and something I can imagine will be useful.

NUGGET:

> A map element is not a variable, and we cannot take it's address. <cite>The Go Programming Language (2016) Donovan and Ritchie, pp. 94</cite>

The reason for this is the map might need to rehash, and move things around for its own purposes.  If you have a memory reference to an element, this will most likely then point to nothing / the wrong thing after the rehashing.  To avoid this, you're not allowed to use the `&` operation to get the pointers to the elements.

This one is more of a :thinkingface: for me. I'm still trying (struggling?) to see the benefits of pointers. They seem like a break in encapsulation. But then I know from Scala / functional circles that not everyone things of encapsulation as the Holy Grail of programming.  Pushing myself out of my comfort zone is why I'm on this journey so I'm going to store it in the memory banks and move on.

NUGGET: 

As with Slices, Maps cannot be compared with each other.  Yet again, the only legal comparison is with `nil`.  

It seems again that this is what I consider a core library leaving me with a bunch of work to do, caused by design decisions elsewhere in the language.  It feels like a loss to not have this, but then I've not really come across the potential benefits which might be significant.  At this point however it feels as if my cognitive load when working with Maps is going to be higher than I'm used to.  And it's not just Maps;

NUGGET:

> Go does not provide a set type, but since the keys of a map are distinct, a map can serve this purpose. <cite>The Go Programming Language (2016) Donovan and Ritchie, pp. 96</cite>

This seems really wierd to me.  At this stage the standard collections support feels very strange.  We don't have a Stack implementation either as I learned earlier in my reading.  It really is a strange new world this Goland [sic].