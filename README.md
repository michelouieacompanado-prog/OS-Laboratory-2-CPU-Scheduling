# OS-Laboratory-2-CPU-Scheduling

Operating Systems Lab 2 — CPU Scheduling Algorithms

**BCA151 Operating Systems Lab · MSU-Iligan Institute of Technology · College of Computer Studies, Department of Computer Applications**

A CPU scheduling simulator written in Python 3 and developed in GitHub Codespaces. It implements five scheduling algorithms, prints a text Gantt chart for each, and computes completion time (CT), turnaround time (TAT), waiting time (WT) and response time (RT).

## Algorithms implemented

| # | Algorithm | Type | Notes |
|---|---|---|---|
| 1 | First-Come, First-Served (FCFS) | Non-preemptive | Arrival order; process ID breaks ties |
| 2 | Shortest Job First (SJF) | Non-preemptive | Shortest burst time first |
| 3 | Priority Scheduling | Non-preemptive | Smaller number = higher priority |
| 4 | Round Robin (RR) | Preemptive | Time quantum of 2 ms (configurable) |
| 5 | Shortest Remaining Time First (SRTF) | Preemptive | Uses a separate dataset with different arrival times |

## Requirements

- Python 3 (no extra packages needed)
- GitHub Codespaces or any terminal with Python 3

## How to run

```bash
python3 cpu_scheduling.py
```

If `python3` is not available, try:

```bash
python cpu_scheduling.py
```

The program prints, for each algorithm, the Gantt chart, a table of per-process metrics (AT, BT, PR, CT, TAT, WT, RT), and the average WT, TAT and RT.

## Changing the experiment settings

- **Round Robin quantum:** edit the last section of `cpu_scheduling.py`, for example
  `ps, g = round_robin(PROCESSES, quantum=4)`
- **Process data:** edit the `PROCESSES` list (used by FCFS, SJF, Priority and Round Robin) or the `SRTF_PROCESSES` list (used by SRTF) near the top of the file.

## Formulas

| Metric | Formula |
|---|---|
| Turnaround Time (TAT) | CT − AT |
| Waiting Time (WT) | TAT − BT |
| Response Time (RT) | First CPU start − AT |
| Average metric | Sum of metric values ÷ number of processes |

## Datasets

**Original dataset** (FCFS, SJF, Priority, Round Robin):

| Process | AT | BT | Priority |
|---|---|---|---|
| P1 | 0 | 8 | 2 |
| P2 | 0 | 4 | 1 |
| P3 | 0 | 2 | 4 |
| P4 | 0 | 6 | 3 |

**SRTF dataset:**

| Process | AT | BT | Priority |
|---|---|---|---|
| P1 | 0 | 8 | 2 |
| P2 | 1 | 4 | 1 |
| P3 | 2 | 2 | 4 |
| P4 | 3 | 1 | 3 |

**Modified dataset (Step 23)** — used for the second comparison, arrival times kept at 0:

| Process | AT | BT | Priority |
|---|---|---|---|
| P1 | 0 | 6 | 3 |
| P2 | 0 | 3 | 4 |
| P3 | 0 | 7 | 1 |
| P4 | 0 | 2 | 2 |

## Sample results

**Original dataset (Round Robin q = 2; SRTF on its own dataset)**

| Algorithm | Average WT | Average TAT | Average RT |
|---|---|---|---|
| FCFS | 8.50 ms | 13.50 ms | 8.50 ms |
| Non-preemptive SJF | 5.00 ms | 10.00 ms | 5.00 ms |
| Non-preemptive Priority | 8.50 ms | 13.50 ms | 8.50 ms |
| Round Robin (q = 2) | 9.00 ms | 14.00 ms | 3.00 ms |
| SRTF (separate dataset) | 2.75 ms | 6.50 ms | 0.25 ms |

**Modified dataset (Step 23)**

| Algorithm | Average WT | Average TAT | Average RT |
|---|---|---|---|
| FCFS | 7.75 ms | 12.25 ms | 7.75 ms |
| SJF | 4.50 ms | 9.00 ms | 4.50 ms |
| Priority | 7.75 ms | 12.25 ms | 7.75 ms |
| Round Robin (q = 2) | 8.50 ms | 13.00 ms | 3.00 ms |
| SRTF (separate dataset) | 2.75 ms | 6.50 ms | 0.25 ms |

**Round Robin quantum experiment (original dataset)**

| Quantum | CPU allocations | Average WT | Average TAT | Average RT |
|---|---|---|---|---|
| 1 | 20 | 9.50 ms | 14.50 ms | 1.50 ms |
| 2 | 10 | 9.00 ms | 14.00 ms | 3.00 ms |
| 4 | 6 | 9.00 ms | 14.00 ms | 5.50 ms |

## Repository contents

| File | Description |
|---|---|
| `cpu_scheduling.py` | The CPU scheduling simulator |
| `LAB_REPORT.md` | Laboratory report: Gantt charts, calculations, experiments, answers and conclusions |
| `screenshots/` | Screenshots of the program running in Codespaces |
| `README.md` | This file |

## Author

- Name: _Miche Louie B. Acompañado_
- Course & Year: _BSCA 3RD YEAR_
- Subject: BCA151 Operating Systems Lab — Lab Activity 2
