# RV32I Processor Performance Analysis

## Overview

This project presents a **performance evaluation of a 5-stage pipelined RV32I processor**, comparing a baseline implementation with an enhanced processor incorporating **branch prediction and cache memory**.

The project evaluates the impact of these architectural enhancements through **timing, performance, execution-time, branch, and cache analysis**.

---

## Architectures Evaluated

### Baseline Processor

The baseline architecture is a **5-stage pipelined RV32I processor** implementing:

**Instruction Fetch → Instruction Decode → Execute → Memory → Write Back**

It includes the required **hazard detection, forwarding, stalling, and control-hazard handling logic** and serves as the reference design for all performance comparisons.

The baseline processor was developed as a separate RTL project. Its dedicated repository contains the complete **RTL implementation, testbench, simulation results, implementation results, and documentation**.

The version used for this performance study is included in the `Baseline_Processor` directory.

### Enhanced Processor

The enhanced architecture is derived from the same 5-stage pipelined processor and introduces two major architectural improvements:

* **Cache Memory** to improve memory-access performance.
* **Branch Prediction** to reduce the performance penalty associated with control hazards.

The enhanced processor maintains the same fundamental pipeline organization, allowing the impact of these features to be evaluated against the baseline architecture.

The corresponding RTL files used in this study are included in the `Enhanced_Processor` directory.

---

## Evaluation Approach

Both processor configurations execute the **same benchmark programs** under a common evaluation setup.

Hardware performance counters are used to collect execution statistics directly from the processors. The collected data is used to calculate and compare performance metrics across the baseline and enhanced architectures.

In addition to execution-level analysis, both designs are synthesized and implemented using **Xilinx Vivado** to evaluate their timing characteristics and FPGA hardware cost.

This enables the project to study not only the performance gains introduced by the enhancements, but also the associated **timing and resource trade-offs**.

---

## Project Structure

The project is organized into three main parts:

### 1. Baseline RV32I Processor

The baseline processor serves as the reference design for the performance evaluation.

This section contains the RTL files used for the baseline implementation and provides a link to the original processor repository containing the complete **RTL design, testbench, simulations, implementation results, and documentation**.

### 2. Enhanced RV32I Processor

The enhanced processor extends the baseline architecture with:

* **Branch Prediction**
* **Cache Memory**

This section contains the RTL files used for the enhanced implementation and provides a link to its dedicated repository containing the complete **RTL design, testbench, simulations, implementation results, and documentation**.

### 3. Performance Evaluation

The baseline and enhanced processors are evaluated and compared across several aspects.

#### 3.1 Introduction

Defines the evaluation setup, processor configurations, target device, benchmarks, and methodology used to ensure a consistent comparison.

#### 3.2 Timing Analysis

Evaluates the post-implementation timing characteristics of both processors, including:

* Critical path delay
* Timing slack
* Maximum operating frequency
* Critical path comparison

#### 3.3 Performance Analysis

Compares the runtime behavior of the two processor implementations using collected performance statistics, including:

* Total cycles
* Instructions executed
* CPI
* Stall cycles
* Pipeline flushes

#### 3.4 Execution Time Analysis

Combines the measured execution performance with the achievable clock frequency to evaluate the actual execution time of both processor configurations.

#### 3.5 Branch Analysis

Evaluates the effectiveness of branch prediction in the enhanced processor using metrics such as:

* Branch count
* Correct predictions
* Incorrect predictions
* Prediction accuracy
* Effect on pipeline flushes

#### 3.6 Cache Analysis

Evaluates the behavior and effectiveness of the cache using:

* Cache hits
* Cache misses
* Cache hit rate
* Impact on processor performance

---

## Evaluation Metrics

The comparison considers both architectural performance and hardware implementation characteristics:

* **Cycles Per Instruction (CPI)**
* **Execution Cycles**
* **Execution Time**
* **Branch Prediction Accuracy**
* **Cache Hit Rate**
* **Critical Path Delay**
* **Maximum Clock Frequency**
* **FPGA Resource Utilization**

---

## Tools & Technologies

**Verilog HDL · RISC-V RV32I · Xilinx Vivado · FPGA Implementation · Static Timing Analysis · Performance Benchmarking · Computer Architecture**

---

## Objective

The objective of this project is to quantitatively evaluate the impact of **branch prediction and cache memory** on a pipelined RV32I processor and analyze the resulting trade-offs between **execution performance, timing, and hardware complexity**.
