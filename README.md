# Intelligent Task Orchestration Strategies for GPU

This project simulates lightweight GPU scheduling strategies using Python to evaluate job waiting times and resource utilization in a constrained GPU environment. Inspired by principles from real-world orchestrators like Run:ai, it focuses on understanding trade-offs between simplicity, fairness, and efficiency.

## Overview

We implemented and compared three GPU scheduling strategies:

### Implemented Policies

| Policy  | Description |
|---------|-------------|
| FIFO (First-In, First-Out) | Jobs are executed strictly in the order of arrival. Simple, but can cause long delays if early jobs are long. |
| BinPack | Tries to pack jobs into the earliest available GPUs. Minimizes GPU idleness by tightly filling available slots. |
| LAS (Least Attending Scheduler) | Tracks historical GPU usage per user and prioritizes users with the lowest cumulative consumption to promote fairness. |

Note: Originally planned strategies like Round Robin and classic Fair Share were excluded from the final implementation.

## Simulation Setup

- Synthetic job queue with:
  - `arrival_time` (based on exponential distribution)
  - `duration` (job runtime)
  - `gpu_required` (1 or 2)
  - `priority` and `user` (used for LAS)
- Cluster configuration: 3 GPUs
- Total jobs: 50

System utilization (ρ) is also computed for performance benchmarking.

## Key Result Example

| Strategy | Avg Waiting Time (s) |
|----------|----------------------|
| BinPack  | ~3368                |
| FIFO     | ~3482                |
| LAS      | Varies depending on user distribution |

## Technologies

- Python 3
- Google Colab (CPU-only environment)
- Pandas, NumPy, Matplotlib



