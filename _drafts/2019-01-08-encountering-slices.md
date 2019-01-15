---
title: "Encountering Slices"
layout: post
---
{% newthought "" %}

Slices currently feel like the solution to a problem I've not yet felt the pain of.  That's not to say the problem isn't there; I'm just not aware of it yet.

Is this because in systems programming the data you're close to and manipulate more is of a different kind?  Or of a different structure? Or more unpredictable? Or more raw? Or is performance more a concern from the outset? I guess I'll have to wait and see.

For my learning purposes, what follows is a series of facts about them, strung together in some kind of train-of-thought;

Literals are initialised without a size (unlike array literals).

They can extend (within the cap).

They're not comparable out of the box (so we can't use `==`).  While the standard golang libraries provide a function to compare byte slices thats the only one; the rest you need to build yourself.{% sidenote 'sn-id-whatever' "Is this because the rest aren't that frequently needed? I'll have to wait and find out." %}"

Digging into why you can't directly compare them is instructive. Firstly;
> Unlike array elements, the elements of a slice are indirect, making it possible for a slice to contain pointers to contain itself. <cite>The Go Programming Language (2016), Donovan and Ritchie, pp. 87</cite>

And secondly;
> because slice elements are indirect, a fixed slice may contain different elements at different times as the content of the underlying array are modified. <cite>The Go Programming Language (2016), Donovan and Ritchie, pp. 87</cite>

Let's be explicit about what "indirect" is.  Slices are like windows onto a subset of an underlying data type - an Array.  Without arrays they don't exist. They don't have any storage themselves - they just contain a pointers to an array - and then add on characteristics such as `len` and `cap`.

It may be instructive at this point to bring in some ways of categorising things.   

_Composite types_ are types created by combining the basic types (Integers, String etc.) in various ways.

Arrays (and Structs) are a subset of Composite Type, called _Aggregate Types_ . They are concatenations of other values in memory.

Slices, while they are Composite Types are not Aggregate Types, and must have zero or one underlying Array type. If it has no underlying Array type then checking against `nil` with the comparison operator `==` (the only usage of this operator valid for Slices) will be `true`.  This is the zero-value of Slices.

A slice can be empty if it has an underlying array, but the `len` will then be zero. 

> To use slices directly its important to bear in mind that although the elements of the underlying array are indirect , the slices pointer, `len` and `cap` are not. <cite>The Go Programming Language (2016), Donovan and Ritchie, pp. 91</cite>

Which leads me to a question which I intend to explore in a later post; do slices need to point to contiguous elements of their undelying array? {% sidenote 'sn-id-whatever' "I assume so, but it's always best never to assume I've found." %}

### Addendum
Slices can be used to implement stacks. But why not just have a Stack data type?  It seems strange coming from the Java language with such a rich set of collections types, to arrive in goland [sic] where I find myself with just a pen knife and a compass.  It's different, but thats why I'm here; to find out why.