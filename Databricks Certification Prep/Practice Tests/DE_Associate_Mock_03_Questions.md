# Databricks Certified Data Engineer Associate: Mock Exam 03

**Questions only. Answers are in a separate file, so don't open it until you've finished.**

- 45 scored multiple-choice questions
- 90-minute time limit (about 2 minutes per question)
- Question counts follow the May 4, 2026 exam guide weights:

| Section | Topic | Weight | Questions |
|---|---|---|---|
| 1 | Databricks Intelligence Platform | 6% | 3 |
| 2 | Data Ingestion and Loading | 21% | 9 |
| 3 | Data Transformation and Modeling | 22% | 10 |
| 4 | Working with Lakeflow Jobs | 16% | 7 |
| 5 | Implementing CI/CD | 10% | 5 |
| 6 | Troubleshooting, Monitoring, and Optimization | 10% | 5 |
| 7 | Governance and Security | 15% | 6 |

Pick one answer per question unless it says otherwise.

---

## Section 1: Databricks Intelligence Platform

**1.** Which statement correctly describes the Databricks control plane and data plane?

- A. The control plane hosts the workspace UI and metadata, while compute runs in the data plane in your cloud account.
- B. The data plane hosts the workspace UI, while compute runs in the control plane.
- C. Both the control plane and the data plane run only in Databricks-owned accounts.
- D. Compute runs in the control plane, and the data plane stores only logs.

**2.** In the medallion architecture, which layer stores data as it was ingested, with minimal changes?

- A. Silver
- B. Gold
- C. Bronze
- D. Platinum

**3.** Where does Delta Lake keep the transaction log for a table?

- A. `_metadata`
- B. `_checkpoint`
- C. `_tmp`
- D. `_delta_log`

---

## Section 2: Data Ingestion and Loading

**4.** Which Auto Loader option tells the stream the format of the source files?

- A. `format`
- B. `cloudFiles.format`
- C. `fileFormat`
- D. `source.format`

**5.** Which clause specifies the source file format in a `COPY INTO` statement?

- A. `FORMAT`
- B. `TYPE`
- C. `USING`
- D. `FILEFORMAT`

**6.** When an Auto Loader record contains data that doesn't match the schema, where is that data stored by default?

- A. The `_rescued_data` column
- B. The `_corrupt_record` column
- C. The `_errors` table
- D. The checkpoint folder

**7.** Which code continuously reads a Kafka topic as a streaming DataFrame?

- A. `spark.read.format("kafka").load()`
- B. `spark.read.csv("kafka")`
- C. `spark.readStream.format("kafka").load()`
- D. `COPY INTO kafka_table`

**8.** You want Auto Loader to process all files that are currently available, then stop. Which trigger does this?

- A. `trigger(processingTime="0 seconds")`
- B. `trigger(continuous="1 second")`
- C. `trigger(manual=True)`
- D. `trigger(availableNow=True)`

**9.** Which Unity Catalog object is used to store non-tabular files such as images, PDFs, or CSVs for governed access?

- A. Volume
- B. Schema
- C. Share
- D. Connection

**10.** An inferred schema has the wrong type for one column. You want to keep inference for the rest of the columns. Which Auto Loader option helps?

- A. `cloudFiles.schemaHints`
- B. `cloudFiles.hints`
- C. `inferSchema = false`
- D. `schemaOverride`

**11.** You append a DataFrame with an extra column to a Delta table that doesn't have that column. Schema evolution is not enabled. What happens?

- A. The extra column is dropped silently.
- B. The write fails with a schema mismatch error.
- C. The table is converted to a view.
- D. The extra column is stored as JSON in a hidden column.

**12.** Which SQL statement adds rows from a query to an existing table?

- A. `INSERT INTO`
- B. `COPY TABLE`
- C. `APPEND ROWS`
- D. `LOAD ROWS`

---

## Section 3: Data Transformation and Modeling

**13.** Which window function assigns consecutive ranks with no gaps after ties?

- A. `row_number`
- B. `rank`
- C. `ntile`
- D. `dense_rank`

**14.** Which DataFrame method turns the distinct values of a column into new columns?

- A. `pivot`
- B. `unpivot`
- C. `melt`
- D. `transpose`

**15.** Which function returns the first non-null value among its arguments?

- A. `greatest`
- B. `least`
- C. `coalesce`
- D. `concat`

**16.** Which function extracts a substring that matches a regular expression pattern?

- A. `regexp_replace`
- B. `regexp_extract`
- C. `split`
- D. `substr`

**17.** Which function converts a string to a date using an explicit format?

- A. `cast_date`
- B. `date_format`
- C. `parse_date`
- D. `to_date`

**18.** Which join type returns rows from the left table that have no match in the right table?

- A. `left_anti`
- B. `left_semi`
- C. `cross`
- D. `full_outer`

**19.** Which operation reduces the number of partitions without a full shuffle?

- A. `coalesce`
- B. `repartition`
- C. `broadcast`
- D. `cache`

**20.** Which SQL statement adds a new column to an existing Delta table?

- A. `UPDATE t SET new_col = NULL`
- B. `MODIFY t new_col INT`
- C. `ALTER TABLE t ADD COLUMNS (new_col INT)`
- D. `INSERT COLUMN new_col INTO t`

**21.** In a Lakeflow Spark Declarative Pipeline, which expectation action stops the pipeline update when a rule is violated?

- A. `ON VIOLATION DROP ROW`
- B. `ON VIOLATION FAIL UPDATE`
- C. `ON VIOLATION WARN`
- D. `ON VIOLATION IGNORE`

**22.** You need to apply inserts, updates, and deletes from a change feed into a target table in a Lakeflow Spark Declarative Pipeline. Which construct does this?

- A. `AUTO CDC INTO`
- B. `COPY INTO`
- C. `OPTIMIZE`
- D. `VACUUM`

---

## Section 4: Working with Lakeflow Jobs

**23.** A notebook task needs the value of a job parameter. Which call reads it?

- A. `spark.conf.get`
- B. `dbutils.widgets.get`
- C. `os.environ`
- D. `sys.argv`

**24.** A cleanup task should run only when at least one upstream task has failed. Which run condition does this?

- A. At least one failed
- B. All done
- C. All succeeded
- D. Always skip

**25.** A job run failed in one of its tasks. You want to re-run only the failed task and the tasks that depend on it. Which feature does this?

- A. Restart the whole job
- B. Clone the job
- C. Repair run
- D. Pause the schedule

**26.** Which task type runs a task once for each item in a list?

- A. If/else condition task
- B. Notebook task
- C. Run job task
- D. For each task

**27.** You want to prevent two runs of the same job from overlapping. Which job setting controls this?

- A. Timeout
- B. Maximum concurrent runs
- C. Max retries
- D. Tags

**28.** Three tasks in one job should use the same cluster to avoid repeated startup time. What should you configure?

- A. A separate cluster per task with its own startup
- B. Only interactive all-purpose clusters
- C. One shared job cluster, referenced by all three tasks
- D. Serverless compute for each notebook manually

**29.** A task hangs and never finishes. Which task setting stops it after a set duration?

- A. Timeout
- B. Max retries
- C. Tags
- D. Concurrency

---

## Section 5: Implementing CI/CD

**30.** Where does the Databricks CLI store its connection profiles by default?

- A. `~/.bashrc`
- B. `~/.databrickscfg`
- C. `/etc/hosts`
- D. `requirements.txt`

**31.** Which CLI command runs a job or pipeline that is defined in a bundle, after deployment?

- A. `databricks bundle start`
- B. `databricks job run`
- C. `databricks bundle exec`
- D. `databricks bundle run`

**32.** Which bundle target setting marks an environment as development, which prefixes resource names and pauses schedules?

- A. `mode: development`
- B. `env: dev`
- C. `stage: dev`
- D. `profile: dev`

**33.** Which practice keeps Databricks job definitions versioned alongside the code?

- A. Store bundle definitions in Git and deploy them from CI
- B. Edit jobs only in the UI
- C. Export notebooks as zip files and email them
- D. Keep job JSON files on a laptop

**34.** You want to work on a different branch inside a Databricks Git folder. What do you do?

- A. Clone the repository into a new workspace
- B. Switch branches in the Git folder UI
- C. Delete the folder and re-create it
- D. Export the notebooks

---

## Section 6: Troubleshooting, Monitoring, and Optimization

**35.** Which tool shows an operator-level breakdown of a slow SQL query?

- A. Query profile
- B. Unity Catalog lineage
- C. Audit logs
- D. Catalog Explorer

**36.** Many shuffle stages spill to disk, and individual tasks are very large. Which Spark setting should you review first?

- A. `spark.ui.port`
- B. `spark.app.name`
- C. `spark.sql.shuffle.partitions`
- D. `spark.driver.host`

**37.** A Delta table has thousands of small files, and reads are slow. Which command compacts them?

- A. `VACUUM`
- B. `OPTIMIZE`
- C. `DESCRIBE HISTORY`
- D. `ANALYZE TABLE`

**38.** Which feature runs maintenance such as `OPTIMIZE` and `VACUUM` automatically for Unity Catalog managed tables?

- A. Predictive optimization
- B. Manual vacuum scheduling
- C. Hive-style partitioning
- D. Caching

**39.** A notebook calls `toPandas()` on a very large DataFrame and the driver runs out of memory. What is the best fix?

- A. Call `toPandas()` on the full table and increase the driver size without limit
- B. Keep the work distributed and write the results to a table
- C. Call `collect()` on every row
- D. Use a single-node cluster for the whole dataset

---

## Section 7: Governance and Security

**40.** A notebook needs a database password. Which approach keeps it out of the code?

- A. Hardcode it in the notebook
- B. Read it with `dbutils.secrets.get` from a secret scope
- C. Print it in a cell output
- D. Write it to the job log

**41.** Which Unity Catalog feature shows upstream and downstream dependencies for tables and columns?

- A. Lineage
- B. Partition pruning
- C. Z-ordering
- D. Caching

**42.** Which privilege allows a user to insert, update, and delete rows in a table?

- A. `SELECT`
- B. `USE SCHEMA`
- C. `CREATE TABLE`
- D. `MODIFY`

**43.** Who can grant privileges on a Unity Catalog object?

- A. Any workspace user
- B. The object owner or a metastore admin
- C. Only account admins
- D. Only the cluster owner

**44.** Which pair of objects lets Unity Catalog access an external cloud storage path?

- A. Cluster policies only
- B. Secret scope only
- C. A storage credential with an external location
- D. A workspace folder and its permissions

**45.** An auditor needs to see who accessed which tables in Unity Catalog. Where should they look?

- A. Unity Catalog audit logs and system tables
- B. Spark UI logs
- C. Notebook revision history
- D. Cluster event log

---

**End of exam.** Record your score and each question you're unsure about, then check the answer key.
