# Intelligent Task Orchestration Strategies for GPU

This project simulates GPU job scheduling strategies using Python to evaluate their efficiency in managing computational workloads. The goal is to analyze and compare the performance of various scheduling policies in terms of average waiting time and fairness in a constrained GPU environment.

## Overview

We implemented and compared three scheduling strategies:

### Implemented Policies

| Strategy              | Description |
|------------------------|-------------|
| FIFO (First-In, First-Out) | Jobs are executed in order of arrival. Simple but may cause long queues if early jobs are long. |
| BinPack | Attempts to pack jobs into the earliest available GPUs. Efficient in resource usage but not fairness-aware. |
| Least Attending Scheduler (LAS) | Prioritizes users with the lowest cumulative GPU usage, promoting fairness over time. |

Note: Although other strategies like Round Robin and Fair Share were initially planned, they were excluded in the final version.

## Simulation Setup

- Simulated job queue includes:
  - `arrival_time`
  - `duration`
  - `gpu_required` (1 or 2)
  - `priority`
  - `user` (used by LAS)
- Cluster: 3 GPUs
- Number of jobs: 50
- Environment: CPU-based simulation (Google Colab)

## Results (Latest Run)

| Strategy         | Avg Waiting Time (s) |
|------------------|----------------------|
| Least Attending  | **1.15**             |
| BinPack          | 30.90                |
| FIFO             | 33.58                |

### Observations

- **Least Attending** significantly reduced waiting times by balancing long-term user usage.
- **BinPack** minimized idle GPU time through efficient job packing.
- **FIFO**, while simple, showed the highest delay due to lack of prioritization or optimization.

## Technologies Used

- Python (Pandas, NumPy, Matplotlib)
- Jupyter Notebook / Google Colab
- No actual GPU hardware; CPU-only logic-based simulation


## Future Work

- Explore preemption penalties and fairness aging
- Extend simulation to real GPU environments using Run:ai or Kubernetes

