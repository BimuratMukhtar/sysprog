# CSS307 System Programming, Fall 2017 Log Page

## Final Exam Questions

* [Dialogue](ch01.md)
* [Introduction to OS](ch02.md)
* [Dialogue](ch03.md)
* [Processes](ch04.md)



### Chapter 26

* How does the thread creation interface presented in this chapter differ from `fork()`?
* Say we had a new syscall, `thread_fork()`, that made a new thread that started at the return of this call. How would this differ from `fork()`?
* Do we need to flush the _TLB_ when context switching between threads in the same process?
* What is a _race condition_?
* How are _race conditions_ and _critical sections_ related?
* How does _mutual exclusion_ prevent race conditions?
* How does _atomicity_ prevent race conditions?
* Why are atomic instructions an impractical solution, by themselves, to prevent race conditions?
  * would need an atomic operation for every possible use case: add to a queue, insert into a  b-tree, etc..
* What does it mean for a program to be deterministic?
* What does it mean for a program to be indeterminate?

### Chapter 27

### Chapter 28

* Why do we need locks?
* What are the possible states of a _lock_?
* What are the semantics of a call to `lock()`?
* What are the semantics of a call to `unlock()`?
* What three metrics do we use to measure the quality of a _lock_?
* What are the drawbacks of implementing locks by _disabling interrupts_?
  * OS loses control
  * does not work with multiprocessors
  * slow to disable interrupts

* What is _spin waiting_?

* How does a spin lock work?
  * What does it require from the hardware?
    * test-and-set or compare-and-swap
  * What are the drawbacks?
    * starvation possible
    * wasted CPU resources
* How do _test-and-set_ and _compare-and-swap_ differ?
* What is the advantage of ticket locks over simple spinlocks?
  * no starvation
  
* Why does the code in Fig. 28.9 (locks with queues) test-and-set `guard` instead of `flag`?

```C
typedef struct{
  int flag;
  int guard;
  queue_t * q;
} lock _t;

void lock_init(lock_t * m) {
  m->flag  = 0;
  m->guard = 0;
  queue_init(m->q);
}
...

```

* Why is spin waiting in the `QueueLock` better than spin waiting in general?
  * limited to spin waiting on lock that guards the queue, not the general lock
* What does `park` & `unpark` do in `Solaris`?
* What would happen if we released the `guard` lock after the `park(...)` in `QueueLock`?
* Could we use a `compare-and-swap` in `QueueLocks` instead of `test-and-set`?
* What is the advantage of two-phase locks?
