---
permalink: /about/
title: News
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

## **January 2019**

* We submitted to ECOOP'19 the paper with title "Godot: All the Benefits of
  Implicit and Explicit Futures". The abstract of the paper reads as follows:

  > Godot: All the Benefits of Implicit and Explicit Futures
  >
  > Concurrent programs often make use of future,
  > which are handles to the results of asynchronous operations.
  >  Futures provide an instantly available means to communicate not yet
  >  computed results, and simplify the implementation of operations that
  >  must synchronise on the result of such
  >  asynchronous operations. Futures can be characterised as either
  >    implicit or explicit, depending on the typing discipline used to
  >    type them.
  >
  >  Existing approaches to implementing futures suffer from ``future proliferation'',
  >  either at the type-level or at run-time. The former
  >  manifests itself through the addition of future type wrappers
  > which expose the client to the
  > asynchronous message indirections of an implementation and hinders
  > subtype polymorphism. The latter manifests itself through increased
  > latency, by traversing
  >  nested future structures at run-time.
  >  Many languages suffer both kinds.
  >
  >  Previous work offer partial solutions to these problems of
  >    future proliferation; in this paper we show how these solutions can be
  >    integrated
  >  in an elegant and coherent way which is more expressive than either
  >  system in isolation. We describe our proposal formally, and state
  >  and prove its key properties, in two related calculi, based on the two possible families of future constructs (data-flow futures and control-flow futures). The former relies on static type information to avoid
  >  unwanted future creation and the latter uses an algebraic data type
  >  with dynamic checks. We also discuss how to implement our new system efficiently.

## **November 2018**

* I presented "Building a compiler: It is all about monads!" at
  [@PartialConf](http://partialconf.com/lineup#kiko-fernandez), where I explain
  how one can create a typechecker with a clean design using monads and monads
  transformers.

## **October 2018**

* I presented the paper
  "The impact of opt-in gamification on students' grades in a software design course".
  ([link to pre-print](https://www.researchgate.net/publication/328115773_The_impact_of_opt-in_gamification_on_students'_grades_in_a_software_design_course))

  Abstract:

  > An achievement-driven methodology strives to give students more control of their learning with enough flexibility to engage them in deeper learning. We observed in the course Advanced Software Design, which uses the achievement-driven methodology, that students fail to get high grades, which may hamper deeper learning. To motivate students to pursue and get higher grades we added gamification elements to the course. To measure the success of our gamification implementation, students filled out a questionaire rating the enjoyment and motivation produced by the game. We built a statistical regression model where enjoyment and motivation explain 55% of the variation in grades. However, only the relationship between motivation and grade is significant, which implies that notivation drives the overall effect of the model. The results suggest that the more the students were motivated by the game, the higher their grades on the course (and vice versa). This implies that if gamification indeed motivates students, then it makes them go beyond what is expected.

* Meeting with Ludovic Henrio, Einar B. Johnsen, Dave Clarke and Tobias Wrigstad
  to discuss the difference between control-flow futures and data-flow futures,
  which was identified by Ludovic Henrio. At the end of the meeting, we are going
  to join efforts to highlight the difference between these futures and constructs
  to allow these futures to co-exist together. We will possibly produce an implementation
  in the Encore language.

## **September 2018**

* ~~Launched the book ICO for "GRASP principles for the Object-oriented mind"~~

* Talk submitted to PartialConf has been accepted. The abstract is written below:

  > Building a compiler: it is all about monads
  >
  > Writing compilers is a difficult task and consists of
  > semantics-preserving transformations, from one phase
  > of the compiler to the next, until the compiler outputs the target code.
  >
  > Monads can help compiler-writers to create a clean design.
  > For example, the Encore compiler
  > uses a type checking monad, which is made up of the Reader, Error and State monads.
  >
  > This talks shows why monads make your code cleaner and why you would want
  > to use these three basic monads.

## **August 2018**

* Paper submitted to EduSymp'18 has been accepted. The abstract is written below:

  > An achievement-driven methodology strives to give students more control of their
  > learning with enough  exibility to engage them in deeper learning.
  >
  > We observed in the course Advanced Software Design, which uses the achievement-driven methodology,
  > that students fail to get high grades, which may hamper deeper learning.
  > To motivate students to pursue and get higher grades we added gamication elements to the course.
  >
  > To measure the success of our gamication implementation, students  filled out a
  > form rating the enjoyment and motivation produced by the game. We built a statistical
  > regression model where enjoyment and motivation explain 55% of the variation in grades.
  > However, only the relationship between "Motivation" and "Grade" is significant,
  > which implies that "Motivation" drives the overall effect of the model. The results
  > suggest that the more the students were motivated by the game, the higher their
  > grades on the course (and vice versa). This implies that if gamication indeed motivates students, then
  > it makes them go beyond what is expected.

* Send an abstract to Partial Conf 2018.

#### **July 2018**

* My proposed presentation to LambdaWorld'18 Cadiz was rejected.

* I submitted the gamification approach that we took during the course Advanced Software Desgin
  to [EduSymp'18](http://www.edusymp.org/2018/). It was the first time that I have
  worked with [Janina Hornbach](http://katalog.uu.se/profile/?id=N14-1034),
  it was really fun and I am really happy with the result. Hopefully,
  we will be able to carry on the future work of the paper :)

  The abstract can be found below
  (and the paper will be available once we know if it got accepted):

  > An achievement-driven methodology strives to give some degree of control of the students' learning with enough flexibility to engage them in deeper learning.
  >
  > We observed that, in the course Advanced Software Design, students fail to get high grades and, in turn, deeper learning.
  > To motivate students to pursue and get higher grades we added gamification elements to the course.
  >
  > To measure the success of our gamification implementation,
  > students filled out a form rating the enjoyment and motivation produced by the game.
  > We built a statistical regression model where enjoyment and motivation explain 55\% of the variation in grades.
  > However, only the relationship between "Motivation" and "Grade" is significant, which implies that "Motivation" drives the overall effect of the model.
  > The results suggest that the more the students were motivated by the game, the higher their grades on the course.
  > This implies that gamification indeed motivates students and makes students go beyond what is expected.

#### **June 2018**

* I had a meeting with Anna Eckerdal and got feedback on an educational paper
that uses an opt-in gamification approach. <!--                                            If we manage to submit to [EduSymp](http://www.edusymp.org/2018/), -->
<!-- [MINT](http://mint.uu.se/) (scholarships and grants managed by Anna Eckerdal) -->
<!-- could give me a grant to cover the symposium and travel costs. -->

* Our team ([Dave Clarke](https://www.it.uu.se/katalog/davcl820),
  [Elias Castegren](https://www.it.uu.se/katalog/elica697),
  [Phuc Vo](https://www.it.uu.se/katalog/voph710) and
  [me](https://www.it.uu.se/katalog/frafe664)) received
  best COORDINATION 2018 paper and best DisCoTec 2018 paper award.

* I will be the new publicity chair for DisCoTec 2019.

* My proposed presentation to ClojuTRE'18 was rejected. My abstract can be found below:

> **Monoids and Monads: The secret weapon to a parallel abstraction**
>
> Why should you consider monoids when designing a parallel abstraction?
> Why monads play an important role in this setting?
> What are the benefits of using monoids and monads?
>
> In this talk, I will save you from creating a non-composable and non-parallelisable library design. To do this, I will show you why your next parallel abstraction is going to use monoids and monads, drawing examples from the (experimental) library ParT. ParT is a functional parallel abstraction that allows the developer to create and coordinate complex parallel workflows, such as asynchronous pipelines of (possibly speculative) parallel computations.
> Join me and let's ParT with monoids and monads!

#### **May 2018**

* The paper *Forward to a Promising Future* has been accepted to COORDINATION and has received the *Best conference paper* award.

* Submission of talk to clojuTRE'18 where I would like to present the functional abstraction *ParT* to the nordic Clojure community.

* Submission of talk to LambdaWorld'18 (Cádiz) where I would like to present the importance of monoidal and monad structures when designing a parallel abstraction.

#### **March 2018**

* Poster presentation of our work *Motivating students with Opt-in gamification* at TUK'18 in Uppsala. We present the opt-in gamification methodology used in the course *Advanced Software Design*. It lead to interesting discussions with professors from other engineering areas. [Poster link here.](public/papers/TUK18Poster.pdf)

#### **February 2018**

* Submission of the paper *Forward to a Promising Future* to COORDINATION.

#### **November 2017**

* The paper *A Survey of Active Object Languages* has been published at the
ACM Computing Surveys (CSUR) journal. This was a great effort from leading researchers working in active objects languages. We provide an overview of different active object languages and compare and contrast their differences.


#### **September 2017**

* Presentation of the work *Affine Killing (extended abstract*) at TyDe'17. This paper extends previous work on the functional abstraction ParT and sketches a solution to the problem of stopping asynchronous parallel speculative tasks in the ParT abstraction. YouTube video recording [available here.](https://youtu.be/pSzZMu33awc)
