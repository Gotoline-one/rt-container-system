# Real-Time Kernel Flags for Raspberry Pi — RT-Game of Life Project

This topic explores compiling real-time (RT) flags for the Linux kernel on a Raspberry Pi.  
Combined with kernel development books, this should serve as the foundation for building a real-time OS (RTOS) environment and related projects.

## REFERENCES

1. [Cornell University CS1114 Section 9: The Game of Life
March 27th, 2013](https://www.cs.cornell.edu/courses/cs1114/2013sp/sections/S09_gameoflife.pdf)

2. Reference thread: [Raspberry Pi Forum - Real-Time Kernel](https://forums.raspberrypi.com/viewtopic.php?t=344994)

3. [gameoflife lexicon](https://bitstorm.org/gameoflife/lexicon/)

4. Wiki [Main GoL Wiki](http://www.conwaylife.com/wiki/Main_Page)

---

## To-Do List

### 1. RTOS and Kernel
- [ ] Build an RTOS base on the Raspberry Pi.

### 2. Real-Time Game of Life (RT-GoL) in C
- [ ] Develop a network-based **Real-Time Game of Life** in C.  
  - [ ] **UDP**: Stream current board information.  
  - [ ] **TCP**: Control channel for interrupts/handles on a specific time scale (target: 10Hz initially).  

### 3. Board-to-Board Protocol
- [ ] Reach Goal: Implement a **board sharing protocol** for communication between multiple Pi-based RT-GoL instances.  
- [ ] Research if **multicast** would be effective for sensing other instances or maintaining sync at defined tick/rate intervals.  

### 4. Minimum Viable RT-Container
- [ ] Reach-Reach Goal: Develop a **minimal RT-container** for Conway's Game of Life using **cgroups** and **namespaces**, to explore how many instances can be run on a single RT-optimized Pi.  

### 5. Hardware Extensions
- [ ] Optional: Add **hardware interface** to integrate Meshtastic boards with Pi "out of the box."  

---

### Notes
This roadmap may expand as research continues, particularly in the areas of real-time networking and containerization under constrained environments like the Raspberry Pi.