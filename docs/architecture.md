# Real-Time Container-like System for Distributed Agents

## Introduction

This project proposes a lightweight, real-time container-like runtime for distributed agents operating on real-time enabled Linux kernels. The goal is to bridge the gap between modern containerization techniques and hard/soft real-time system requirements, supporting integration with proven industrial real-time components like BC635/BC637 time cards and MIL-STD-1553 data buses. By supporting automated testing, hardware emulation, and CI/CD pipelines, this system aims to offer a practical, flexible, and research-friendly platform for modern system designers and embedded engineers.

---

## Project Goal

Design a lightweight, real-time-aware container system optimized for low-latency, distributed applications (e.g., Game of Life) running on RT-enabled Linux kernels, with quantitative performance guarantees measurable for research and practical systems. This system will also explore integration with proven real-time technologies such as BC635/BC637 time cards and MIL-STD-1553 data buses, ensuring compatibility with established industrial and aerospace timing and communication standards in a containerized environment. Additionally, this platform would serve as an ideal and practical tool for systems designers seeking to emulate real hardware within a fully integrated CI/CD pipeline, enabling automated testing and validation in a controlled, repeatable environment.

---

## System Architecture

| Layer | Components |
| ----- | ---------- |
|       |            |

| **User Applications**    | Game of Life RT Agent (First App), Custom RT-aware agents (future)                                                                                                    |
| ------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **RT Container Runtime** | RT Container Orchestrator CLI/API, Agent Launcher/Supervisor, Real-time Scheduling Control, Resource Allocator (CPU, Mem, Net)                                        |
| **OS System Layer**      | Cgroups Interface (CPU, Mem, I/O), Namespaces (PID, Net, Mount, User), Scheduling Policies (SCHED\_FIFO, SCHED\_RR), RT System Call Wrappers (chroot, unshare, clone) |
| **Kernel Level (RTOS)**  | PREEMPT\_RT Linux Kernel, Cgroups/Namespaces Kernel Modules, IRQ Management, (Optional) Isolated Net Stack per Agent (NetNS)                                          |
| **Hardware Layer**       | Raspberry Pi, Embedded Boards, VMs, Bare Metal, CPUs, Real-time Network (if used), BC635/BC637 Time Cards, 1553 Bus Hardware                                          |

---

## System Layers Breakdown

| Layer                    | Purpose                                               | Example Components                               |
| ------------------------ | ----------------------------------------------------- | ------------------------------------------------ |
| **User Applications**    | RT-enabled distributed apps running on your system    | Game of Life agent, other future apps            |
| **RT Container Runtime** | RT orchestration layer for "container-like" control   | Supervisor/Launcher, CLI/API, batcher            |
| **OS System Layer**      | Kernel features exposed via system calls / interfaces | Cgroups, Namespaces, Schedulers                  |
| **Kernel (RTOS)**        | Low-latency RT Linux kernel w/ proper isolation       | PREEMPT\_RT patched Linux                        |
| **Hardware Layer**       | Physical/virtual machines executing agents            | Pi, ARM boards, Intel, VMs, Time Cards, 1553 Bus |

---

## Programming Layer Mapping

| Functionality                                 | Programming Level                                     | Notes                                             |
| --------------------------------------------- | ----------------------------------------------------- | ------------------------------------------------- |
| Real-time kernel, IRQ isolation               | Kernel                                                | PREEMPT\_RT, kernel config                        |
| Cgroups and namespaces management             | Systems-level (Low-level syscalls, libsystemd, Go, C) | Direct kernel interface for process/resource mgmt |
| Scheduling control (SCHED\_FIFO, R limits)    | Systems-level (Syscalls, C)                           | Priority and scheduling API                       |
| Agent launcher, resource allocator            | Systems-level / User-space (Rust, Go, C)              | Core orchestration runtime                        |
| RT container manager CLI / API                | User-space application (Rust, Go, Python)             | Command-line or RESTful control                   |
| Distributed agents (Game of Life)             | User-space application (Java, C, Python, Rust)        | First test application                            |
| Systemd integration (optional for boot/start) | System-level service config (Systemd unit)            | Boot/start control, resilience                    |

---

## Key Design Principles

| Principle                              | Description                                                                                                              |
| -------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| **Real-Time First**                    | Agents guaranteed RT scheduling when possible (SCHED\_FIFO/RR).                                                          |
| **Lightweight**                        | Minimal overhead; avoid full Docker/Podman stack.                                                                        |
| **Daemonless (Optional)**              | Possible to run without background daemons (fully on-demand agents).                                                     |
| **Secure and Isolated**                | Use namespaces to prevent agent interference.                                                                            |
| **Distributed Ready**                  | Agents can coordinate over network (UDP/TCP), isolated per namespace if needed.                                          |
| **Observability-Ready**                | Expose real-time metrics (latency, CPU/mem usage, scheduling success) for research.                                      |
| **Portable to embedded (Pi, ARM)**     | Minimal system requirements, suitable for embedded, edge.                                                                |
| **Compatible with proven RT systems**  | Support integration with BC635/BC637 time cards, 1553 bus hardware, and other real-time systems.                         |
| **CI/CD and Hardware Emulation Ready** | Designed to enable automated testing and validation workflows that emulate real hardware in a full-stack CI/CD pipeline. |

---

## First Deliverable Example (Prototype)

```bash
# Start 4 Game of Life agents on isolated CPUs, 256MB each, with real-time priority
rt-container-cli --cpus 2,3 --mem 256m --sched SCHED_FIFO --app ./gol-agent --params "board=4x4 region=1"
rt-container-cli --cpus 4,5 --mem 256m --sched SCHED_FIFO --app ./gol-agent --params "board=4x4 region=2"
...
```

---

## Future Work

- Prototype and test initial RT container launcher.
- Integrate BC635/BC637 time card interfaces.
- Develop MIL-STD-1553 bus agent communication layer.
- Measure system latency and determinism under controlled workloads.
- Explore distributed Game of Life as a demonstrator for scaling and synchronization.
- Package system as a reusable RT container orchestration tool.

---

## Conclusion

This system provides a research-ready, lightweight, real-time container-like runtime for distributed agents that need low latency and deterministic behavior. It blends kernel-level RT tuning, container isolation features (cgroups, namespaces), and custom user-space orchestration. The system is designed to be extensible, with Game of Life as a first demonstrator for quantitative analysis. Furthermore, the system will support integration with industrial real-time components such as BC635/BC637 time cards and MIL-STD-1553 data buses, ensuring compatibility with established real-time systems in aerospace and defense. By supporting full-stack CI/CD integration with automated testing and hardware emulation, this platform offers a practical and forward-looking solution for modern systems designers.

---

## License

MIT License. See LICENSE file for details.

