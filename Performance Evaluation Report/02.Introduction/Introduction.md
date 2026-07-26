# 3.1 Introduction

## Overview

This performance evaluation compares two implementations of a **5-stage pipelined RV32I processor**:

1. **Baseline RV32I Processor**
2. **Enhanced RV32I Processor**

The enhanced processor extends the baseline architecture with **branch prediction and cache memory**. The objective is to quantify how these architectural enhancements affect processor performance while also considering their impact on timing and hardware implementation.

Rather than evaluating the processors only through functional simulation, this analysis uses execution statistics and post-implementation timing results to study the relationship between **CPI, execution cycles, clock period, execution time, branch behavior, and cache performance**.

---

## Processor Configurations

### Baseline RV32I Processor

The baseline processor is a **5-stage pipelined RV32I implementation** and serves as the reference architecture for the evaluation.

It provides the performance baseline against which the impact of the architectural enhancements is measured.

### Enhanced RV32I Processor

The enhanced processor is based on the same underlying pipeline architecture with two additional performance-oriented features:

* **Branch Prediction** – reduces the number of pipeline penalties caused by control hazards by predicting the outcome of branch instructions.
* **Cache Memory** – reduces the performance impact of memory accesses by exploiting locality and serving frequently accessed data from faster on-chip storage.

The enhanced architecture is evaluated against the baseline processor to determine whether the reduction in pipeline penalties translates into improved overall execution performance.

---

## Evaluation Methodology

Both processor implementations are evaluated using the **same benchmark workloads**.

Each benchmark is executed on both processors, and hardware performance counters are used to record execution statistics. This provides a direct comparison of processor behavior under equivalent workloads.

The evaluation is performed at two levels:

**Architectural Performance**

Execution behavior is analyzed using cycle count, instruction count, CPI, stalls, flushes, branch prediction statistics, and cache statistics.

**Implementation Performance**

Post-implementation timing analysis is used to determine the critical-path delay, clock period, and achievable operating frequency of each architecture.

Considering both levels is important because an architectural enhancement may reduce the number of execution cycles while simultaneously increasing the critical-path delay.

---

## Performance Counters

Hardware performance counters are integrated into the processor to collect runtime statistics during benchmark execution.

The measured events include:

| Counter               | Description                                                |
| --------------------- | ---------------------------------------------------------- |
| Cycle Count           | Total clock cycles required to execute the benchmark       |
| Instruction Count     | Number of instructions completed during execution          |
| Branch Count          | Total number of branch instructions encountered            |
| Correct Predictions   | Number of correctly predicted branches                     |
| Incorrect Predictions | Number of incorrectly predicted branches                   |
| Cache Hits            | Number of memory accesses successfully served by the cache |
| Cache Misses          | Number of memory accesses not found in the cache           |

These counters provide the raw data used throughout the performance evaluation.

---

## Evaluation Metrics

### Cycles Per Instruction (CPI)

CPI measures the average number of clock cycles required to complete an instruction.

**CPI = Total Execution Cycles / Instructions Executed**

A lower CPI generally indicates more efficient pipeline utilization.

### Execution Time

CPI alone does not represent the complete processor performance because the two implementations may operate with different clock periods.

Execution time is therefore evaluated using:

**Execution Time = Instruction Count × CPI × Clock Period**

This accounts for both architectural efficiency and the timing characteristics of the implemented design.

### Branch Prediction Accuracy

The effectiveness of branch prediction is evaluated using the number of correct and incorrect predictions.

**Prediction Accuracy = Correct Predictions / Total Predictions × 100**

Branch behavior is also analyzed alongside pipeline flushes to determine the effect of branch prediction on control-hazard penalties.

### Cache Hit Rate

Cache effectiveness is evaluated using cache hit and miss statistics.

**Cache Hit Rate = Cache Hits / (Cache Hits + Cache Misses) × 100**

This provides a measure of how effectively the cache serves memory accesses during each benchmark.

---

## Benchmark Methodology

A set of benchmark programs is used to exercise different aspects of processor behavior.

| Benchmark   | Workload Type        | Primary Purpose                                        |
| ----------- | -------------------- | ------------------------------------------------------ |
| Benchmark 1 | Arithmetic-intensive | Evaluate computation and pipeline performance          |
| Benchmark 2 | Branch-intensive     | Evaluate branch prediction and control-hazard behavior |
| Benchmark 3 | Memory-intensive     | Evaluate memory behavior and cache effectiveness       |

Each benchmark is executed on both processor configurations using the same program and input conditions.

This allows changes in performance to be attributed to the architectural differences between the baseline and enhanced processors rather than differences in workload.

---

## Timing Evaluation

Both processor implementations are synthesized and implemented using **Xilinx Vivado**.

Post-implementation timing analysis is used to obtain:

* Critical-path delay
* Logic delay
* Routing delay
* Timing slack
* Maximum achievable clock frequency

Timing analysis is necessary because the additional cache and branch prediction hardware may increase the critical path even when they improve CPI.

The timing results are therefore combined wit
