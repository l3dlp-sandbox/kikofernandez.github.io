---
title: "Integrating Task Parallelism with Actors"
date: 2016-10-12
permalink: /posts/2016/10/integrating-task-and-actors/
tags:
  - paper
  - review
---

This is a summary of the OOPSLA'12 paper [Integrating Task Parallelism with Actors](http://dl.acm.org/citation.cfm?doid=2384616.2384671)

## Integrating task parallelism with actors

In this paper, the authors show how to integrate tasks and actors while preserving the common properties of the actor model. This means, they preserve the sequential dispatch of one message at a time (per actor) but allow parallelism within the body of a method call, e.g.

```
class Actor
  def main(): void
    finish {
      async { ... }
      async { ... }
    }
```

They introduce two new constructs `pause()` and `resume()` that can be used inside `async`s whenever the task modifies the internal state of the actor. For instance:

```
class Actor
  def main(): void
    async {  ... };
    pause(); -- returns void but prevents actor from processing messages
    async {
      ...  -- here I can update internal state of the actor
      resume();
      -- after the call to `resume`, I should not update internal state
      -- of the actor as the actor may be processing messages
    }
```

In the example above, the spawned tasks are not captured by a `finish` statement, which means that they live even after the `main()` method has finished. For this reason, the user needs to specify that the actor should not process messages when the task updates the internal state. These new constructs could cause deadlocks and data races if not used properly.

The authors provide two implementations (one in Java and one in Scala) of this model. However, I failed to grasp the idea of _lingering tasks_ and _Data-Driven Controls_ -- both are implementation details -- and will not comment on these.
