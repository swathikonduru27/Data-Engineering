# Mock Exam 02: Answer Key

**Only open this after you've submitted your answers.**

These questions were written for practice. They are not official exam questions. Check each explanation against docs.databricks.com before relying on it.

| # | Ans | Why | # | Ans | Why |
|---|---|---|---|---|---|
| 1 | B | Unity Catalog is the governance layer (catalogs, schemas, permissions, lineage). | 24 | A | If/else condition tasks branch on earlier task results. |
| 2 | B | Delta Lake adds ACID transactions and time travel. | 25 | B | File arrival triggers start a job when new files land. |
| 3 | B | Job compute starts for the run and terminates afterward, which is cheapest for scheduled work. | 26 | B | Table update triggers fire when an upstream table changes. |
| 4 | B | `COPY INTO` is idempotent: it tracks loaded files and skips them on re-runs. | 27 | B | Tasks with no dependency between them can run in parallel. |
| 5 | B | `schemaLocation` stores the inferred schema and its changes. | 28 | B | Data-driven triggers suit irregular arrivals. |
| 6 | B | With `addNewColumns`, the stream fails once, records the new schema, and works after restart. | 29 | A | The pipeline task runs a Lakeflow Spark Declarative Pipeline inside a job. |
| 7 | B | File notification mode scales better than directory listing for high volume. | 30 | B | Commit & Push sends committed changes to the remote branch. |
| 8 | A | Managed connectors are Databricks-managed ingestion into Unity Catalog tables. | 31 | A | Bundle targets with variables and overrides handle per-environment values. |
| 9 | A | `from_json` parses a JSON string with a schema. | 32 | A | `bundle validate` checks the bundle configuration before deploy. |
| 10 | A | Unity Catalog volumes keep the file governed. | 33 | A | `databricks.yml` defines a bundle's resources, targets, and variables. |
| 11 | A | A scheduled Lakeflow Jobs task is the managed, repeatable option. | 34 | B | A CI job validating and deploying to the prod target is the repeatable pattern. |
| 12 | B | Auto Loader is built for continuous, high-volume incremental file ingestion. | 35 | A | The Lakeflow Jobs run history view compares runs. |
| 13 | B | It filters nulls and casts types in one step. `na.drop()` drops all null rows, which is too broad. | 36 | B | One task with far more shuffle read than the median indicates skew. |
| 14 | B | A left join from `customers` keeps customers with no orders. | 37 | A | Spill (memory and disk) in stage metrics shows memory pressure. |
| 15 | B | Broadcast joins suit a small side that fits in executor memory. | 38 | A | Liquid clustering (`CLUSTER BY`) replaces manual partitioning and `ZORDER`. |
| 16 | B | `UNION ALL` keeps duplicates. `UNION` removes them. | 39 | A | Startup and library errors show in the cluster event log and driver logs. |
| 17 | A | `explode` produces one row per array element. | 40 | B | Dropping a managed table deletes its metadata and data files. |
| 18 | B | `row_number()` over a partitioned, ordered window keeps the latest row per key. | 41 | B | External tables keep their files when dropped. |
| 19 | B | `approx_count_distinct` trades exactness for lower cost. | 42 | B | Read access needs `USE CATALOG`, `USE SCHEMA`, and `SELECT`. A single `SELECT` isn't enough. |
| 20 | B | Materialized views store precomputed results and refresh on a schedule. | 43 | A | Row filters restrict visible rows by group. |
| 21 | B | Streaming tables process new rows incrementally. | 44 | A | Column masks change a column's value per user. |
| 22 | A | `EXPECT ... ON VIOLATION DROP ROW` drops invalid rows and records metrics. | 45 | A | ABAC policies apply central row and column rules across tagged data. |
| 23 | A | Max retries re-runs a failed task. | | | |

**Score:** ___ / 45

**Scoring guide:** 36 or more is a strong result. Below 36, check which section you missed most.

**Review by section:** Count your misses in each section. A miss rate above about 30% means that section needs a targeted deep dive before the exam.
