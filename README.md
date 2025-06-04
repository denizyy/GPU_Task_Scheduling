# Intelligent Task Orchestration Strategies for GPU

This project simulates GPU job scheduling strategies using Python to evaluate their efficiency in managing computational workloads. The goal is to analyze and compare the performance of various scheduling policies in terms of average waiting time and fairness in a constrained GPU environment.

## Implemented Policies

| Strategy                    | Description |
|----------------------------|-------------|
| FIFO (First-In, First-Out) | Jobs are executed in order of arrival. Simple but may cause long queues if early jobs are long. |
| BinPack                    | Attempts to pack jobs into the earliest available GPUs. Efficient in resource usage but not fairness-aware. |
| Least Attending (LAS)     | Prioritizes users with the lowest cumulative GPU usage, promoting fairness over time. |

Note: Although other strategies like Round Robin and Fair Share were initially planned, they were excluded from the final version.

## Simulation Setup

- Two simulation scenarios based on different mean job durations:
  - `GPU_Scheduling_MeanTime_40.ipynb`: Mean duration = 40 seconds
  - `GPU_Scheduling_MeanTime_50.ipynb`: Mean duration = 50 seconds
- Each job has the following attributes:
  - `arrival_time`, `duration`, `gpu_required`, `priority`, `user`
- Cluster: 3 GPUs
- Number of jobs: 50
- Environment: CPU-based simulation (Google Colab)

## Results

### Mean Duration = 40 seconds

| Strategy         | Avg Waiting Time (s) |
|------------------|----------------------|
| Least Attending  | 1.15                 |
| BinPack          | 30.90                |
| FIFO             | 33.58                |

### Mean Duration = 50 seconds

| Strategy         | Avg Waiting Time (s) |
|------------------|----------------------|
| Least Attending  | 4.55                 |
| BinPack          | 58.38                |
| FIFO             | 61.28                |

## Observations

- Least Attending significantly improved waiting time in both scenarios by promoting fairness.
- BinPack provided efficient GPU usage but was affected more as job durations increased.
- FIFO, while simple, was the least efficient in terms of average waiting time.

## Technologies Used

- Python (Pandas, NumPy, Matplotlib)
- Jupyter Notebook / Google Colab
- CPU-only simulation (no real GPU hardware involved)

## Future Work

- Explore preemption penalties and fairness aging mechanisms
- Extend the simulation to real GPU cluster environments using platforms such as Run:ai or Kubernetes
