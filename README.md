# Benchmark Comparison: DuckDB vs Pandas

> **Author:** Anurag Kumar Pal  
> **Date:** September 5, 2026  
> **Description:** Comprehensive runtime benchmarking comparison between **DuckDB** and **Pandas** across varying dataset sizes (50k to 4M rows) for core data wrangling operations.

---

## 📋 Table of Contents
1. [Overview](#overview)
2. [Tested Operations & Dataset Sizes](#tested-operations--dataset-sizes)
3. [Key Findings & Conclusions](#key-findings--conclusions)
4. [Summary Benchmark Results Table](#summary-benchmark-results-table)
5. [How to Run / Requirements](#how-to-run--requirements)

---

## 🔍 Overview
This benchmark evaluates the performance tradeoffs between **Pandas** (in-memory DataFrame manipulation) and **DuckDB** (in-process SQL OLAP database engine using lazy evaluation) across four major data wrangling tasks:
* **Loading Datasets:** CSV parsing and ingestion performance from 50k up to 4M records.
* **Sorting (`ORDER BY`):** Sorting overhead by specific columns across different scale tiers.
* **Aggregation (`GROUP BY` + `AVG`/`MAX`):** Grouping and summarizing performance.
* **Row-Wise Transformations:** Column transformations and calculations applied per row.

---

## 📊 Key Findings & Conclusions

1. **Dataset Loading:** 
   * **DuckDB** significantly outperforms Pandas when loading large datasets, scaling efficiently as volumes increase from 500k to 4M rows.
2. **Aggregations:** 
   * **Pandas** maintains faster aggregation performance across all dataset sizes, consistently outperforming DuckDB from small files up to heavy volumes (4M rows).
3. **Row-Wise Transformations:** 
   * **Pandas** is quicker on smaller scopes (up to 500k rows), whereas **DuckDB** takes the efficiency lead when handling larger datasets ($1.5M+$ rows).
4. **Sorting Operations:** 
   * Performance varies depending on size, with Pandas showing strong performance at lower row counts while DuckDB excels at scale for specific queries.

---

## 📈 Summary Benchmark Results

| Operation | Dataset Size | Pandas Wall Time (s) | DuckDB Action Time (s) | Delta (Pandas - DuckDB) (s) |
| :--- | :--- | :---: | :---: | :---: |
| **Loading** | 50k rows | 0.28 | 0.21 | +0.07 |
| | 100k rows | 0.77 | 0.28 | +0.49 |
| | 500k rows | 6.16 | 1.22 | +4.94 |
| | 1.5M rows | 8.75 | 3.03 | +5.72 |
| | 4M rows | 97.00 | 64.02 | +32.98 |
| **Sorting** | 50k rows | 0.04 | 0.38 | -0.34 |
| | 100k rows | 0.05 | 0.19 | -0.14 |
| | 500k rows | 0.25 | 0.41 | -0.16 |
| | 1.5M rows | 2.17 | 0.43 | +1.74 |
| | 4M rows | 8.23 | 38.80 | -30.57 |
| **Aggregating** | 50k rows | 0.01 | 0.19 | -0.18 |
| | 100k rows | 0.01 | 0.12 | -0.11 |
| | 500k rows | 0.03 | 0.38 | -0.35 |
| | 1.5M rows | 0.20 | 0.41 | -0.21 |
| | 4M rows | 0.43 | 12.65 | -12.22 |
| **Row-Wise Transformation** | 50k rows | 0.02 | 0.14 | -0.12 |
| | 100k rows | 0.04 | 0.11 | -0.07 |
| | 500k rows | 0.14 | 0.15 | -0.01 |
| | 1.5M rows | 0.33 | 0.13 | +0.20 |
| | 4M rows | 0.76 | 0.24 | +0.52 |

---

## ⚙️ Requirements & Usage
To run the benchmark notebook yourself, ensure you have the following Python libraries installed:
```bash
pip install pandas duckdb
```
