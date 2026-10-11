# Mock Exam 03: Answer Key

**Only open this after you've submitted your answers.**

These questions were written for practice. They are not official exam questions. Check each explanation against docs.databricks.com before relying on it.

| # | Ans | Why | # | Ans | Why |
|---|---|---|---|---|---|
| 1 | A | The control plane runs the UI and metadata. Compute runs in the data plane in your cloud account. | 24 | A | "At least one failed" runs a task only when an upstream task fails. |
| 2 | C | Bronze keeps data close to its ingested form. | 25 | C | Repair run re-runs only failed tasks and their dependents. |
| 3 | D | The transaction log lives in `_delta_log`. | 26 | D | For each tasks loop over a list of items. |
| 4 | B | `cloudFiles.format` sets the source file format for Auto Loader. | 27 | B | Maximum concurrent runs limits overlapping runs of a job. |
| 5 | D | `FILEFORMAT` specifies the source format in `COPY INTO`. | 28 | C | A shared job cluster is referenced by multiple tasks to avoid repeated startup. |
| 6 | A | Mismatched data goes to `_rescued_data` by default. | 29 | A | Timeout stops a task that runs too long. |
| 7 | C | `spark.readStream` with the Kafka format reads a topic continuously. | 30 | B | The CLI reads profiles from `~/.databrickscfg`. |
| 8 | D | `availableNow` processes all currently available data, then stops. | 31 | D | `databricks bundle run` runs a bundle's job or pipeline after deploy. |
| 9 | A | Volumes govern non-tabular files in Unity Catalog. | 32 | A | `mode: development` prefixes resource names and pauses schedules. |
| 10 | A | `cloudFiles.schemaHints` overrides types for specific columns and keeps inference for the rest. | 33 | A | Versioning bundle definitions in Git and deploying from CI is the repeatable pattern. |
| 11 | B | Without schema evolution, a Delta append with a new column fails with a schema mismatch. | 34 | B | Switching branches is done in the Git folder UI. |
| 12 | A | `INSERT INTO` appends rows from a query to a table. | 35 | A | Query profile shows operator-level detail for a SQL query. |
| 13 | D | `dense_rank` gives consecutive ranks with no gaps after ties. | 36 | C | Spill and very large tasks point to shuffle partition sizing. |
| 14 | A | `pivot` turns distinct column values into new columns. | 37 | B | `OPTIMIZE` compacts small files. |
| 15 | C | `coalesce` returns the first non-null argument. | 38 | A | Predictive optimization runs maintenance automatically on managed tables. |
| 16 | B | `regexp_extract` pulls out a pattern match. | 39 | B | Keep work distributed. Writing results to a table avoids collecting data on the driver. |
| 17 | D | `to_date` converts a string to a date with a given format. | 40 | B | `dbutils.secrets.get` reads a secret from a secret scope. |
| 18 | A | `left_anti` returns left rows with no match on the right. | 41 | A | Lineage shows upstream and downstream dependencies. |
| 19 | A | `coalesce` reduces partitions without a full shuffle. | 42 | D | `MODIFY` allows inserting, updating, and deleting rows. |
| 20 | C | `ALTER TABLE ... ADD COLUMNS` adds a column. | 43 | B | The object owner or a metastore admin can grant privileges. |
| 21 | B | `ON VIOLATION FAIL UPDATE` stops the update when a rule is violated. | 44 | C | A storage credential plus an external location grants access to external storage. |
| 22 | A | `AUTO CDC INTO` applies change-feed inserts, updates, and deletes to a target. | 45 | A | Audit logs and system tables record who accessed which objects. |
| 23 | B | `dbutils.widgets.get` reads a job parameter in a notebook. | | | |

**Score:** ___ / 45

**Scoring guide:** 36 or more is a strong result. Below 36, check which section you missed most.

**Review by section:** Count your misses in each section. A miss rate above about 30% means that section needs a targeted deep dive before the exam.

**Note on this mock:** Questions 1–45 are a different set from Mock 02, so use Mock 03 as a fresh check after your Mock 02 review. Two questions are the most worth verifying in the docs: Q22 (the current name of the CDC construct in Lakeflow Spark Declarative Pipelines) and Q32 (the exact behavior of `mode: development`).
