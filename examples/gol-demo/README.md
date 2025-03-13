# Game of Life Distributed Agent Demo

## Overview

Example setup to run distributed Game of Life agents using the real-time container-like runtime.

## Example CLI Run

```bash
rt-container-cli --cpus 2,3 --mem 256m --sched SCHED_FIFO --app ./gol-agent --params "board=4x4 region=1"
rt-container-cli --cpus 4,5 --mem 256m --sched SCHED_FIFO --app ./gol-agent --params "board=4x4 region=2"
