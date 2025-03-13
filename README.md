# Real-Time Container-like Runtime for Distributed Agents

## Overview

A lightweight, real-time-aware container system designed for distributed agents in embedded and industrial environments. This project bridges real-time Linux (PREEMPT_RT) and container orchestration for high-performance, low-latency applications.

## Features

- Real-time scheduling (SCHED_FIFO/SCHED_RR)
- Resource isolation (CPU, memory, I/O)
- Namespace isolation (PID, Net, Mount, User)
- Extensible CLI and runtime management
- Compatible with BC635/BC637 time cards and 1553 bus hardware
- CI/CD and hardware-in-the-loop simulation ready

## First Application

- Distributed, real-time **Game of Life** agents

## Directory Structure

| Directory          | Purpose                                      |
|--------------------|----------------------------------------------|
| `src/`             | Source code for CLI, agents, runtime         |
| `docs/`            | Design documents, diagrams, research papers  |
| `examples/`        | Example setups, demo configurations          |
| `tests/`           | Unit and integration test cases              |

## License

Apache 2.0 License — see LICENSE file for details.

## Contact

Interested in contributing or collaborating? Open an issue or reach out!
