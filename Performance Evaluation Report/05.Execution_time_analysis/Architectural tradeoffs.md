# Architectural Trade-offs

The enhanced RV32I processor introduces **branch prediction and cache memory** to reduce pipeline penalties and improve execution performance. While these enhancements improve the processor at the architectural level, they also introduce additional hardware and affect the timing characteristics of the design.

This section discusses the trade-offs observed between **CPI, execution time, critical-path delay, and implementation complexity**.

## CPI vs. Execution Time

CPI alone does not determine the actual execution time of a processor.

The execution time can be expressed as:

**Execution Time = Instruction Count × CPI × Clock Period**

The enhanced processor improves CPI by reducing penalties associated with **control hazards and memory accesses**. However, the additional cache and branch prediction logic increases the critical-path delay of the processor, resulting in a larger minimum clock period.

Therefore, the CPI improvement does not translate proportionally into execution-time improvement.

In other words, the enhanced processor may require **fewer clock cycles to execute a workload**, but each clock cycle can take longer than in the baseline processor.

This demonstrates an important architectural trade-off:

> **Reducing the number of execution cycles does not necessarily produce an equivalent reduction in execution time when the clock period also changes.**

The final performance therefore depends on both the **architectural efficiency (CPI)** and the **achievable clock frequency** of the implementation.

---

## Timing Trade-off

The enhanced processor has a longer critical path compared with the baseline processor due to the additional hardware and interconnections.

Timing analysis shows that most of the increase in critical-path delay is caused by **routing delay**, while the increase in **logic delay is relatively small**.

This suggests that the main timing overhead comes from the physical placement and routing of the additional connections rather than from the computational delay of the added logic itself.

| Delay Component     | Baseline | Enhanced | Increase |
| ------------------- | -------: | -------: | -------: |
| Logic Delay         |   2.148ns |   2.224ns |    0.076ns |
| Routing Delay       |    0.695ns |   3.993 ns |    3,298ns |
| Total Data Delay    |    2.843ns |   6.217 ns |    3.374ns |
| Total Critical path Delay |   2.858ns |   6.521ns |    3.663ns |

The increase in logic delay is relatively small, while routing contributes the majority of the additional critical-path delay. This indicates that the timing penalty is largely associated with the physical placement and interconnection of the added hardware rather than the added logic alone.

## Architectural Trade-off Summary

| Aspect              | Baseline Processor | Enhanced Processor             | Trade-off                                                      |
| ------------------- | ------------------ | ------------------------------ | -------------------------------------------------------------- |
| CPI                 | Higher             | Lower                          | Enhanced architecture reduces pipeline penalties               |
| Execution Cycles    | Higher             | Lower                          | Fewer cycles are required for benchmark execution              |
| Clock Period        | Lower              | Higher                         | Enhanced design has a longer critical path                     |
| Maximum Frequency   | Higher             | Lower                          | Increased critical-path delay limits operating frequency       |
| Logic Complexity    | Lower              | Higher                         | Cache and branch prediction require additional hardware        |
| Routing Complexity  | Lower              | Higher                         | Additional connectivity increases routing overhead             |
| Overall Performance | Reference          | Improved depending on workload | Cycle reduction must compensate for the increased clock period |

The enhanced architecture therefore represents a trade-off between **cycle-level performance improvement and timing overhead**.

---

## Future Work

Future optimization will focus on reducing the **routing delay of timing-critical paths** in the enhanced processor.

Potential directions include improving module placement, reducing long interconnect paths, restructuring timing-critical datapaths, and applying FPGA physical optimization techniques.

Since the increase in logic delay introduced by the architectural enhancements is relatively small compared with the routing overhead, reducing routing delay could allow the enhanced processor to retain the CPI benefits of **cache memory and branch prediction** while achieving a higher maximum operating frequency.

This would improve execution time without removing the architectural features responsible for reducing pipeline penalties.
