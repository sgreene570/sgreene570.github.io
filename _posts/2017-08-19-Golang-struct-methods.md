---
layout: post
title:  "Writing Struct Methods in Golang"
date:   2017-08-19 10:05:04 -0600
categories: jekyll update
---

Coming from C, I naturally assumed that writing a struct function in Go
would be as easy as creating a function pointer. Instead, struct _methods_ can
be specified with an additional type in any function declaration.

Say for example, we have the following struct:

```Go
type Point struct {
   x   int
   y   int
}
```

To write a Point method, simply add the Point type to the method declaration:

```Go
func (p Point) InvertPoint() {
    temp := p.x
    p.x = y
    p.y = temp
}
```

While it does take some getting used to, I personally find go struct methods to 
be easier to work with than function pointers in C.  When writing structs in C,
you have to declare all of your function pointers (and therefore, how many struct methods
you have) within the struct itself.  In Go, a struct can have as many methods as
needed regardless of what the struct says.
