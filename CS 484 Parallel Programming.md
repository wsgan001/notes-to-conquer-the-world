---
tags: [cs484-parallel-programming, school]
title: CS 484 Parallel Programming
created: '2020-01-29T17:44:57.790Z'
modified: '2020-01-29T17:50:02.573Z'
---

# CS 484 Parallel Programming 


## Week 1
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
