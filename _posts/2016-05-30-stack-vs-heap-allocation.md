---
title: "Stack vs Heap allocation. Is it worth it?"
date: 2016-05-30
permalink: /posts/2016/05/stack-vs-heap-allocation/
tags:
  - allocation
  - performance
---

Is it worth to allocate things in the stack instead of in the heap?
I kind of new the answer, but I didn't know how much.
Allocating things in the stack is super-cheap and,
in most cases, uses a single instruction while allocating things
in the heap is quite expensive (expensive system calls).
Let's do a simple example that proves this:

In the code below, I have created three implementations of the fibonacci series.
In the first implementation, I allocated a `long long` in the heap
(function `fibonacci` and helper function `fib`). The second
implementation allocates a `long_stack` struct
(contains two `long long`) in the stack (functions `fib3` and `fibonacci3`).
The third implemnentation allocates a `long long` in the stack
(functions `fib2` and `fibonacci2`). With these simple 3 functions
we are going to measure how much time it takes to compute the
50th number in the fibonacci series.

The results couldn't be clearer:

1. Total time when allocating in the heap: 2.740 ms
2. Total time when allocating in the stack (struct): 0.450 ms
2. Total time when allocating in the stack: 0.340 ms

This represents a 6x speedup over the allocation in the heap.

```c
#include <stdlib.h>
#include <stdio.h>
#include <sys/time.h>

static int NUMBER = 50;

typedef struct long_s {
  long long num;
} long_s;

typedef struct long_stack {
  long long p;
  long long n;
} long_stack;


long long fib(long_s *p, long_s *n, int remaining){
  if(remaining==0){
    return n->num;
  }else{
    long_s *nn = malloc(sizeof *nn);
    *nn = (long_s){.num = p->num + n->num};
    return fib(n, nn, remaining-1);
  }
}

long long fib2(long long p, long long n, int remaining){
  if(remaining==0){
    return n;
  }else{
    long long nn = p + n;
    return fib2(n, nn, remaining-1);
  }
}

long long fib3(long_stack s, int remaining){
  if(remaining==0){
    return s.n;
  }else{
    return fib3((long_stack){.p=s.n, .n=s.n+s.p}, remaining-1);
  }
}

long long fibonacci(int initial){
  long_s* prev = malloc(sizeof* prev);
  long_s* next = malloc(sizeof* next);
  *prev = (long_s) {.num = 1};
  *next = (long_s) {.num = 1};
  return fib(prev, next, initial-2);
}

long long fibonacci2(int initial){
  return fib2((long long)1, (long long)1, initial-2);
}

long long fibonacci3(int initial){
  return fib3((long_stack){.n = 1, .p = 1}, initial-2);
}

void chronos(struct timeval t1, struct timeval t2){
  double elapsedTime;
  // compute and print the elapsed time in millisec
  elapsedTime = (t2.tv_sec - t1.tv_sec) * 1000.0;      // sec to ms
  elapsedTime += (t2.tv_usec - t1.tv_usec) / 1000.0;   // us to ms

  printf("Elapsed time: %e\n", elapsedTime);
}

int main(){
  struct timeval t1, t2;

  // Example that allocates in the heap
  gettimeofday(&t1, NULL);
  for(unsigned int i=0; i<1000; i++){
    fibonacci(NUMBER);
  }
  gettimeofday(&t2, NULL);
  chronos(t1, t2);

  // Example that allocates in the stack a long
  gettimeofday(&t1, NULL);
  for(unsigned int i=0; i<1000; i++){
    fibonacci2(NUMBER);
  }
  gettimeofday(&t2, NULL);
  chronos(t1, t2);

  // Example that allocates a struck in the stack
  gettimeofday(&t1, NULL);
  for(unsigned int i=0; i<1000; i++){
    fibonacci3(NUMBER);
  }
  gettimeofday(&t2, NULL);
  chronos(t1, t2);
}
```
