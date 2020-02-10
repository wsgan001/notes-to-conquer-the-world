---
tags: [CS 484 Parallel Programming, school]
title: CS 484 Parallel Programming
created: '2020-01-29T17:44:57.790Z'
modified: '2020-02-10T03:30:23.207Z'
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
  - 






