---
tags: [CS 484 Parallel Programming, school]
title: CS 484 Parallel Programming
created: '2020-01-29T17:44:57.790Z'
modified: '2020-02-19T19:59:42.432Z'
---

# CS 484 Parallel Programming 


# Week 1
### Early History of Computers
First tubes -> integrated circuits 

### Moore's Law
- Single instruction is exec in 1 clock cycle
- A lot of transistors = Chip
- Moore's law became a self-fulfilling prophecy 
- Increased freq. created hot chips. Pentium Pro and similar 
- Number of transistor: 
    - 10-14 nanometers
- Clock speed. A single program exec. 
- Smaller transistors = greater clock speeds
- Max we will get to 30-50 billion transistors per chip. What next? 

### End of Moore's Law and Parallelism 
- Put more cores/processors on chips. 
- Use parallelism to run things faster
- Maybe 8 is all you need. 
- Killler Parallel Apps are faster. 
- Example areas: Search, data centers, ML, video processing. 

### Future
- Quantum Computing? 
- Multicore Computers
- GPGPUs 
- Small Clusters
- Programs need to become parallel 
- Future is hard to predict. 

### Memory Access
- Transfer data between memory and processors
- DRAM. Large, inexpensive. About 50ns latency. 2 GHz single core clock. 
- 3D stacking memory to increase bandwidth. 
- cache helps with temporal and spatial locality
- You can stack caches. L1, L2, and L3. 


# Week 2

Quiz

What is/are disadvantages of a long cache line? Both

What is the cache hit ratio? fraq found in mem



What is the arithmetic intensity in FLOPs/word for the following loop (all variables are double precision floating point numbers): 1

How many load operations happen in each iteration of the following loop: Not 4,5,3

How many cache misses will result from the following code? Assume that N is a multiple of the cache line size w, that the cache is a fully associative LRU cache of size N*w, and that both arrays’ initial addresses are at the start of a cache line. = N^2/w + N/w

Which of the following has better cache performance? Assume that the cache is a fully associative LRU cache of size greater than N*w (where w is the number of words per cache line) and arrays are stored in row major order. i,j


# Week 3

- 3.1.1 Vectorization
  - "Vectorization" (simplified) is the process of rewriting a loop so that instead of processing a single element of an array N times, it processes (say) 4 elements of the array simultaneously N/4 times.
  - Maybe computations are the same. 
  - Create a vector of flooting point units. Cheap, less than 1 square mm on the chip. 
  - The compiler vectorizes code most of the time. 
  - Most compilers create a report. 
  - Get feedback from compiler on why some functions didn't vectorize. 

- 3.1.2 Tools
  - Performance Counters: PAPI
  - Used for CPU designers but opened for developers. 
  - Cache hit ratio and similar performance metrics. 
  - (Just) Timer to time things? Make sure it's low overhead. 
  
- 3.1.3 gprof
  - Profiling = Collect data on execution characteristics. 
  - Get metrics about program execution like RAM, loops, timings, function calls, and more. 
  - 


- 3.2.1 Shared Memory Multiprocessors
  - Shared Memory multiprocessor and caches
  - CPUs share memory (DRAM)
  - Cache controllers know which data is used by each CPU. 
  - Cache controllers watch every transaction on the bus. 
  - MSI protocol. 
  - Cache traffic "serving" latest version of cache can be bottloneck
  - Data written by one core and used by another causes cache traffic. 
 
- 3.2.2 Shared Address Space Programming: Basics
  - A process is a programming action. It has an address space in virtual memory. 
  - VM has a heap, stack, and grobal variables. 
  - With two cores, there a two caches. It's like the Node event loop. 
  - Processes alternate between CPUs. 
  - Each progress contains multiple threads
  - Each thread has their own stack but same address space (VM)
  - Threads should run on one fixed core. 
  - Hyperthreading. Each core can be seem as two. 
  - Memory: L1 cache private to core or two, L2 may be private or shared, L3 shared across all processors. 
  - One memory controller per chip. 

- 3.2.4 OpenMP: History and Parallel Loops
  - Created in 1997
  - User decides what to execute in parallel. 
  - OpenMP pragma always begin with `omp`
  - It provies feedback but programmer controls it. 
  - Must compile with OpenMP options
  - `-fopenmp` for gcc oro `-openmp` for intel. 

- 3.2.5 OpenMP: History and Parallel Loops (Part 2)
  - How to decide if a loop is parallel? Basic rule. Will the results always be the same when running in one process/thread? 
  - Floating point issues. Adding numbers in different order may give you slightly different rusults. This is important when asking when a loop can be parallelized. 

- 3.2.6 OpenMP: History and Parallel Loops (Part 3)
  - Written program that as 99% parallel is a bad idea. Hard to debug. Make sure it's always 100% parallel friendly. 
  - How to know if a loop is parallel: 


# Week 4

- 4.1.1 Open MP: Basics of Parallel For
  - OpenMP directives are expressed as pragmas.
  - Parallel for Construct to specify a loop can run in parallel
  - `daxpy` 
  - Execution: master thread enters saxpy function
    - Master thread creates worker threads and makes a team to execute code. 
  - Number of threads can be controlled. Usually threads = number of cores. 
  - OMP_NUM_THREADS for env var and `omp_set_num_threads()` function which overrides env var. 
  - Loop scheduling: Determines which iterations run in which thread. Can be controlled. 
  
- 4.1.2 OpenMP: Enabling Parallelization
  - Each thread has own copy of private variables
  - master thread doesn't have access to the private variable after loop terminates. Hard to know what to keep. 
  - firtprivate: list of variables to keep by master thread. First copy.
  - lastprivate: keep last iteration variables. 
  
- 4.1.2 OpenMP: Enabling Parallelization
  - Each thread has it's own stack. We can create variables for each parallel execution in that. 
  - `private` can be used to declare a list of private variables for each thread. `temp` example. 
  - Stack variables are thread private. 
  - Each 

- 4.1.4 OpenMP: Enabling Parallelization (Part 2)
  - Sum over an array. 
  - Not parallel but maybe it can? 
  - It can with `reduction`. Adds to sum then master thread adds all values at end. 
  - `#pragma omp parallel for reduction(+:sum)`
  - Data sharing options:
    - private
    - shared
    - default: private|shared|none
    - reduction
    - firstprivate
    - lastprivate

- 4.1.5 Restructuring for Parallelization
  - Several methods like restructuring into multiple loop or simple algebra. 

- 4.2.1 Loop Schedules
  - Default assigns loops to any thread
  - Assignment can be controlled with a schedule. 
  - Dynamic schedule
  - Idea: every time a thread goes to ask for work, it is given a chunk of iterations
  - `schedule` class. `schedule (kind)`. Kind = static divided evenly, static chunk, dynamic chunk divided into chunks RR fashion, guided size decreases exp from an impl dependant value to chunk.
  - Static has low overhead, better spatial locality. 
  - Dynamic will balance load well but high overhead to sync. Spatial location is destroyed
  - `pragma omp parallel for schedule(dynamic, 16`
  
- 4.2.2 Beyond Loops: The Parallel Construct
  - `parallel` directive allows programmer to say what each thread does. 
  - `#pragma omp parallel [clause]`
  - Num of threads can be changed
  - Code with `parallel` is much longer and complicated but gives programmer more control. 
  
- 4.2.4 Beyond Loops: The Parallel Construct (Part 3)
  - 


# Week 5
- 5.1.1 Synchronization Constructs: Critical, Atomic, and Locks
  - Different threads need to coordinate with each other in a parallel program 
  - Types: 
    - Mutual exclusion: Shared data may result in data inconsistency
    - Event Synchronization: Code sections executed by different threads need to be sequenced in some particular order.  
  - Critical section: `#pragma omp critical`. No other thread is allowed to execute any code inside any critical section. 
    - Threads are made to wait if they encouter this directive. 
    - Can be named and it means restriction applies only to those sections that share the name. 
    - Unnamed critical sections are global lock.
    -  
- 5.1.2 Synchronization Constructs: Critical, Atomic, and Locks II
  - Critical sections are expensive. 
  - There are many variants of atomic directives
  - Atomic `capture` clause. Atomically change a variable and captue it's old or new value into another variable.  
  - Lock routines: Much lower level. It's like a note, telling everyone you are using the room. Lock threads. 
  - Library locks: Very flexible, no restrictions on where they can be placed. 
  - Deadlocks: A bunch of threads are waiting on each other in a circular fashion. 

- 5.1.3 Case Study: Finding Primes
  - Find the first million prime numbers

- 5.1.4 Additional Coordination Constructs
  - Sections: Provide another way of creating a team of threads. 
  - barrier: make everyone wait. This can be thought of as an event synch construct. 
  - master: code that is only to be executed by master thread.
  - single: similar to master but can be executed by any single thread. 
  
- 5.1.5 Example: Prefix Sum - Recursive Doubling with Barriers
  - Prefix sum problem. 
  - Sequantial algo is slow
  - Recursive dubling works but not perfect. 

- 5.1.7 More Synchronization
  - Simple processors are easier to work with but slow. 
  - Computer architects added caches 
  - Also added registers. This improved speed. 
  - Variables can be stored in registers. 
  - Sequential consistency: A desired property of parallel programming systems. The execution of a parallel program should be same as the sequential one. 
  - How to deal with lack of sequential consistency? 
    - Give up resister and write buffers? No way!
    - OpenMP provides a way to flush data. 
  - `flush` is especially useful or point-to-point synchronization. For one thread to signal to another that some event or data is ready. 
  
- 5.1.8 More Synchronization II
  - The ordered clause: Makes the block of code wait for previous iteration to finish its ordered block. 
  - `#pragma omp parallel for ordered`
  - depends clause with ordered directive: Allows you to specify dependence in a more general precise way. 
  - the depends block of code has to wait for the source to complete before it continues. 
  

- 6.1.1 Performance Issues
  - Using OpenMP is not that simple. Code needs to be restructured. 
  - Jacobi Relaxation algorithms 
  - 



