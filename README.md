# Real-Time Container-like System for Distributed Agents

## Introduction

This project proposes a lightweight, real-time-aware container system optimized for low-latency, distributed applications running on RT-enabled Linux kernels. The goal is to bridge the gap between modern containerization techniques and hard/soft real-time system requirements, supporting integration with industrial real-time components like BC635/BC637 time cards and MIL-STD-1553 data buses. The system supports automated testing, hardware emulation, and CI/CD pipelines. Partial integration with BC635/BC637 time cards and 1553 bus hardware will be explored based on sponsorship availability and time constraints.

## Expected Timeline for MS CS Capstone Proposal

### Phase 1: Guided Research (1 Month)

| Week | Focus Area                                       | Deliverable                                    |
|------|--------------------------------------------------|------------------------------------------------|
| 1    | Background research on RTOS + PREEMPT_RT kernel  | Annotated bibliography, summary report on PREEMPT_RT, cgroups, namespaces, and real-time constraints |
| 2    | Study of containerization in real-time context  | Comparative analysis of Docker, Podman, LXC, and need for RT-specific containerization |
| 3    | Research on BC635/BC637 time cards and 1553 bus | Preliminary integration feasibility study report |
| 4    | Design iteration based on research insights    | Refined system architecture draft, identified technical risks and solutions |

### Phase 2: Execution Plan (3 Months)

| Month | Focus Area                                             | Deliverable                                     |
|-------|--------------------------------------------------------|-------------------------------------------------|
| 1     | Prototype RT Container Runtime (core orchestration CLI) | Working prototype CLI to launch isolated RT agents; demo with simple shell agent |
| 1     | Integrate Game of Life as distributed agent            | Game of Life demo running under RT container framework |
| 2     | Add metrics collection for latency and performance     | Runtime metrics engine: CPU/mem, scheduling latencies, agent status collection |
| 2     | Begin hardware integration study for time cards/1553   | Initial proof-of-concept: API mock for BC635/BC637 and 1553 agent placeholder (depending on sponsorship and time) |
| 3     | Distributed agent coordination with RT networking      | Proof-of-concept for inter-agent communication (UDP/TCP under net namespaces) |
| 3     | Benchmarking and final performance evaluation          | Test results on RT scheduling, resource isolation, and inter-agent communication |
| 3     | Final write-up and defense preparation                 | Final capstone paper, presentation slides, system diagrams |

## Summary of Phases

- **Month 1 (Guided Research)**: Focused on literature, real-time kernel and hardware integration studies, and refining system architecture.
- **Months 2-4 (Execution)**: Focus on building core system, adding agent, proving real-time coordination and monitoring, and preparing final deliverables for capstone defense.

## Capstone Deliverables

- Functional RT container runtime capable of launching, isolating, and managing agents.
- Game of Life distributed agent adapted to runtime as proof of concept.
- Metrics engine for real-time performance tracking.
- Optional: Partial BC635/BC637 and MIL-STD-1553 integration stubs (dependent on sponsorship and time constraints).
- Final capstone report and oral defense.

## Working with Submodules

This repository uses **Git submodules** to integrate external projects like the Game of Life agent under active development.

### Cloning with Submodules

When cloning this repository for the first time, use:

```bash
git clone --recurse-submodules https://github.com/YOUR_USERNAME/rt-container-system.git
```

If you already cloned the repository without submodules, you can initialize them afterward with:

```bash
git submodule update --init --recursive
```

### Pulling Updates for Submodules

To pull the latest changes from submodules:

```bash
git submodule update --remote
```

If you are working on both the main project and a submodule, make sure to commit changes properly inside each repository and update the reference in the main repo:

```bash
cd examples/gol-demo/javaConway
# make changes, commit, push in submodule repo
cd ../../../
git add examples/gol-demo/javaConway
git commit -m "Update Game of Life agent submodule to latest commit"
git push
```

### Notes

- Submodules allow us to keep agent development modular and reusable.
- Click on the submodule link in GitHub to view or contribute directly to the agent project.

## License

Apache 2.0 License — see LICENSE file for details.

---
