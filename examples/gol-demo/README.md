# Game of Life Distributed Agent Demo

## Overview

Example setup to run distributed Game of Life agents using the real-time container-like runtime. 

The agent used in this example is linked as a **submodule** to allow independent development and version control:

[https://github.com/Gotoline-one/javaConway_.001/](https://github.com/Gotoline-one/javaConway_.001/)

## Example CLI Run on how it will work with rt-contrainer-cli 

```bash
rt-container-cli --cpus 2,3 --mem 256m --sched SCHED_FIFO --app ./gol-demo/javaConway --params "board=4x4 region=1"
rt-container-cli --cpus 4,5 --mem 256m --sched SCHED_FIFO --app ./gol-demo/javaConway --params "board=4x4 region=2"
'''

## Requirements 

[X] PREEMPT_RT Patch kernel 
[X] Cgroups and namespace enagled 
[ ] RT container runtime (prototype when completed)
