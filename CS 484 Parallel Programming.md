---
tags: [CS 484 Parallel Programming, school]
title: CS 484 Parallel Programming
created: '2020-01-29T17:44:57.790Z'
modified: '2020-01-30T00:49:44.948Z'
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









