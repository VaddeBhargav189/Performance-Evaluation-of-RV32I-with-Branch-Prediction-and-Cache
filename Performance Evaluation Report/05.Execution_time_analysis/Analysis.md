# Execution Time Analysis

## Processor Timing Comparison

| Processor | Clock Period (ns) | Maximum Frequency (MHz) |
|---|---:|---:|
| Baseline RV32I Processor | 2.858 | 349.89 |
| Enhanced RV32I Processor | 6.521 | 153.35 |

## Benchmark Execution Time Comparison

| Benchmark | Baseline CPI | Enhanced CPI | Baseline Execution Time (ns) | Enhanced Execution Time (ns) | 
|---|---:|---:|---:|---:|
| Arithmatic intensive | 1.117599 | 1.000353 | 54322.02 | 110941.79 |
| Branch intensive | 1.492604 | 1.019734| 865982.83 | 1349906.08 |
| Memory intensive | 1.199940 | 1.00600 | 34304.57 | 65620.94 |
