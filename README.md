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

<img width="4800" height="3000" alt="duckdb_vs_pandas_trends" src="https://github.com/user-attachments/assets/9aca728d-81d6-4ebf-88a8-31871387b50f" />

---

## ⚙️ Requirements & Usage
To run the benchmark notebook yourself, ensure you have the following Python libraries installed:
```bash
pip install pandas duckdb
```
