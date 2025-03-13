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

## License

Apache 2.0 License — see LICENSE file for details.

---

