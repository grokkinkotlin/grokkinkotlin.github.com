---
title: "Encountering Slices"
layout: post
---
{% newthought "" %}

These feel like the solution to a problem I've not yet felt the pain of.  That's not to say the problem isn't there, but I'm not aware of it.

Is this because the data you're close to and manipulate more in Systems Programming is of a different kind?  Of a different structure?

Literals - initialised without a size (unlike array literals)

Sizes can extend (within cap)

Not comparable (so can't use `==`).  The standard libs provide a func to compare byte slices, but the rest you need to build yourself.  (Because it's not frequently needed?)

Why not? Firstly;
> Unlike array elements, the elements of a slice are indirect, making it possible for a slice to contain pointers to contain itself. <cite>The Go Programming Language (2016), Donovan and Ritchie, pp. 87</cite>

And secondly;
> because slice elements are indirect, a fixed slice may contain different elements at different times as the content of the underlying array are modified.

Lets be explicit about what "indirect" is.  Slices are like windows onto a subset of an underlying data type - an Array.  Without arrays they don't exist. They don't have any storage themselves, just pointers, and characteristics such as `len` and `cap`.


Composite types are types created by combining the basic types in various ways.

Arrays (and Structs) are _Aggregate Types_ - they are concatenations of other values in memory.

Slices are not, and must have zero or one underlying array types. If it has no underlying array type then checking against `nil` with the comparison operator '==' (the only usage of this operator valid for Slices) will be `true`.  This is the zero-value of slices.  

A slice can be empty if it has an underlying array, but the len is zero.  Then it is empty.


> To use slices directly its important to bear in mind that although the elements of the underlying array are indirect , the slices pointer, len and cap are not. <cite>The Go Programming Language (2016), Donovan and Ritchie, pp. 91</cite>

So do slices need to point to contiguous elements of their undelying array?

Slices can be used to implement stacks. But why not just have a Stack data type?