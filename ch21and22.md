### Swapping (Chapter 21 and 22)

* How does the virtualization of memory allow an OS to provide the illusion that a process has more memory than is physically available?
* Where is the swap space located?
* How are page faults and present bits related?
* What are the steps that occur in servicing a page fault?
  * What if memory is full?
  * Is this likely?
* What are the steps involved in accessing a memory location if the desired page is paged out?
* What are high-water and low-water marks?
  * Why do we want them?
  * If the page has not been changed since it was last written to disk, do we need to write it again?
  * Do we really need to evict a page to get to the high-water mark or can we simply make sure it is "clean"?
* What is the advantage of doing work in the background?
* What should happen if we run out of swap space?
  * Is this possible? How?
  * Could we prevent it?
* What are memory overlays?
  * How have things improved?

