---
title: "Introduction to affine types in Encore"
date: 2017-06-09
permalink: /posts/2017/06/affine-types/
tags:
  - type systems
  - review
---

[^encore]: [Parallel Objects for Multicores: A Glimpse at the Parallel Language Encore](https://link.springer.com/chapter/10.1007%2F978-3-319-18941-3_1)
[^kappa]: [Reference Capabilities for Concurrency Control](http://drops.dagstuhl.de/opus/volltexte/2016/6099/)
[^ParT]: [ParT: An Asynchronous Parallel Abstraction for Speculative Pipeline Computations](https://link.springer.com/chapter/10.1007%2F978-3-319-39519-7_7)
[^in-place]: [A Type System for Bounded Space and Functional In-Place Update—Extended Abstract](https://link.springer.com/chapter/10.1007%2F3-540-46425-5_11)

An affine type system allows either an unlimited number of aliases or no aliases at all. The [Encore](https://github.com/parapluu/encore) language has a more powerful type system [[^encore]] [[^kappa]]  that can encode affine types.

In Encore, an affine type is defined by an affine (*mode*) annotation, `read` or `lin`, followed by a type. For instance:

```ruby
def readLine(f: read File): read String
  val f2 = f
  f2.readLine()
end
```

The formal arguments of this function states that  `readLine` takes a `File`  which may have aliases (and can be aliased) and returns a `String` that can be aliased as well, since it has the `read` annotation. In Encore, the `read` annotation also implies that the variable pointer, `f`, cannot modify to what it points to (similar to `const` in C language).

If we modify the function to:

```ruby
def readLine(f: lin File): read String
  var f2 = f
  f2.readLine()
end
```

the `lin` annotation guarantees that the `File` has to be treated linearly -- no aliasing is allowed. The type system forbids aliasing and the program above is rejected because `f2`  is an alias of `f`.
Let's re-write the program so that it typecheks:

```ruby
def readLine(f: lin File): read String
  var f2 = consume(f)
  f2.readLine()
end
```

This new version typechecks, although it may seem as if `f2` is aliasing `f`. Nonetheless, the `consume` keyword nullifies `f` and the assignment makes `f2` to be the only one with access to the contents of the file.

## Why are linear references important?

For parallel and concurrent languages, a linear reference guarantees that the user of the reference is  the only one who has access to it and cannot be affected by (nor affect) other threads -- guarantees **data-race freedom** and **runtime thread-local reasoning**.

In a functional setting (and functional abstractions), the runtime has enough information to do in-place updates.  In the beginning of the 90s (maybe a bit earlier), this was mentioned quite often in the literature but there was no work that further developed the idea. Martin Hoffman used it for the first time in his paper "A Type System for Bounded Space and Functional In-Place Update" in ESOP'00[[^in-place]].

Linear references are important for the Encore language because Encore has many different abstractions to express concurrency and parallelism: actors and tasks[[^encore]], hot objects and ParT types[[^ParT]]. My current work focuses on formalising the ParT types in an affine type system. Afterwards, ParT types will use this optimisation to save memory and some other optimisations that I dare not to comment on until I know for sure that they do work.
