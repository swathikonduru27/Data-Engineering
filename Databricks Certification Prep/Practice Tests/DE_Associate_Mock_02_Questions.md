# Databricks Certified Data Engineer Associate: Mock Exam 02

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

**1.** Which component provides the unified governance layer for data and AI assets, including catalogs, schemas, permissions, and lineage?

- A. Delta Lake
- B. Unity Catalog
- C. Spark Structured Streaming
- D. Databricks Connect

**2.** Which technology adds ACID transactions and time travel on top of Parquet files in cloud object storage?

- A. Parquet alone
- B. Delta Lake
- C. The Hive metastore
- D. CSV storage

**3.** A nightly ETL job runs on a schedule and has no interactive use. Which compute option best fits this workload?

- A. An all-purpose cluster that stays running between jobs
- B. Job compute, which starts for the run and terminates afterward
- C. A single-node all-purpose cluster used for development
- D. A shared interactive cluster used by notebook users

---

## Section 2: Data Ingestion and Loading

**4.** A team runs `COPY INTO` daily on a folder of CSV files. What is the key property of `COPY INTO` that matters here?

- A. Re-running it reloads every file and creates duplicate rows
- B. It tracks files it has already loaded, so re-running skips them
- C. It requires a streaming checkpoint location
- D. It only loads Parquet files

**5.** Which Auto Loader option stores the inferred schema and tracks schema changes over time?

- A. `checkpointLocation`
- B. `schemaLocation`
- C. `mergeSchema`
- D. `inferSchema = false`

**6.** An Auto Loader stream uses `cloudFiles.schemaEvolutionMode = "addNewColumns"`. A new column appears in incoming files. What happens?

- A. The new column is silently ignored.
- B. The stream fails once with an unknown-field error, the new schema is recorded, and a restart picks up the new column.
- C. The target table rejects all writes until someone updates it manually.
- D. The new column is written only to `_rescued_data`.

**7.** A source directory receives millions of files per day. Which Auto Loader listing mode is recommended for this volume?

- A. Directory listing
- B. File notification mode (`cloudFiles.useNotifications = true`)
- C. Loading each file individually with a Python loop
- D. Full-directory rescans with `COPY INTO`

**8.** What does a Lakeflow Connect managed connector provide?

- A. A managed connection to a supported source, with ingestion landing into Unity Catalog tables
- B. Custom JDBC code that you write and maintain
- C. File uploads only
- D. Streaming only from Kafka

**9.** A bronze table has a string column `payload` containing JSON. Which Spark SQL function parses it into a struct using a defined schema?

- A. `from_json`
- B. `explode`
- C. `pivot`
- D. `collect_set`

**10.** A data engineer needs to explore a small CSV file quickly, and the file should be governed. What is the best approach?

- A. Upload it to a Unity Catalog volume and read it from there
- B. Keep it only on the driver's local disk
- C. Commit it to a Git folder as data
- D. Email it to the team and load it from a local copy

**11.** A notebook pulls data from a REST API every hour and writes to a Unity Catalog table. What is the most appropriate way to schedule it?

- A. A scheduled Lakeflow Jobs task that runs the notebook
- B. Running the notebook manually each hour
- C. A cron job on a personal laptop
- D. A shell loop inside a cluster's init script

**12.** Files arrive continuously, in the tens of thousands per hour, and must be loaded incrementally. Which approach is best?

- A. Running `COPY INTO` manually when someone remembers
- B. Auto Loader
- C. A pandas loop over the files
- D. A JDBC connection that reads the files row by row

---

## Section 3: Data Transformation and Modeling

**13.** Which PySpark code removes rows with a null `order_id` and casts `amount` to double?

- A. `df.na.drop()`
- B. `df.filter(F.col("order_id").isNotNull()).withColumn("amount", F.col("amount").cast("double"))`
- C. `df.select("*")`
- D. `df.cast("amount")`

**14.** A report needs every customer, including customers with no orders. Which join type should you use between `customers` and `orders`?

- A. Inner join
- B. Left join from `customers`
- C. Cross join
- D. Left join from `orders`

**15.** When is a broadcast join appropriate in Spark?

- A. When both tables are very large
- B. When one side is small enough to fit in executor memory, below `spark.sql.autoBroadcastJoinThreshold`
- C. Only in streaming queries
- D. Never, when reading Delta tables

**16.** In Spark SQL, which keyword combines two result sets and keeps duplicate rows?

- A. `UNION`
- B. `UNION ALL`
- C. `INTERSECT`
- D. `EXCEPT`

**17.** Which function turns an array column into one row per element?

- A. `explode`
- B. `collect_list`
- C. `array_distinct`
- D. `flatten`

**18.** You need one row per `order_id`, keeping the row with the latest `updated_at`. Which approach does this?

- A. `distinct()` across all columns
- B. `row_number()` over `(partition by order_id order by updated_at desc)`, filtered to 1
- C. `groupBy("order_id").count()`
- D. Sorting by `updated_at` only

**19.** What does `approx_count_distinct` give you compared with an exact `countDistinct`?

- A. An exact count at a higher cost
- B. An approximate count at lower compute cost
- C. A count that includes nulls
- D. It works only in SQL, not in DataFrames

**20.** A BI team needs precomputed results of an aggregate query, refreshed on a schedule. Which object fits?

- A. A standard view
- B. A materialized view
- C. A temporary view
- D. A common table expression

**21.** A source table receives new rows continuously. A Lakeflow Spark Declarative Pipeline should process only the new rows each run. Which object fits best?

- A. A materialized view
- B. A streaming table
- C. A standard view
- D. A managed external table

**22.** A pipeline must drop rows where `amount <= 0` and record how many rows were dropped. Which expectation syntax does this?

- A. `CONSTRAINT valid_amount EXPECT (amount > 0) ON VIOLATION DROP ROW`
- B. `CHECK amount > 0 DELETE`
- C. `ASSERT amount > 0`
- D. `ON ERROR SKIP amount > 0`

---

## Section 4: Working with Lakeflow Jobs

**23.** Which task setting automatically re-runs a failed task?

- A. Max retries
- B. Timeout
- C. Concurrency
- D. Tags

**24.** A job must choose which downstream path to run based on the result of an earlier task. Which task type supports this?

- A. If/else condition task
- B. Notebook task
- C. Python wheel task
- D. Dashboard task

**25.** A job should start whenever new files land in a cloud storage location. Which trigger type fits?

- A. Scheduled (cron)
- B. File arrival
- C. Manual
- D. Continuous with a 1-second interval

**26.** A downstream job should run only after an upstream Unity Catalog Delta table receives new data. Which trigger type fits?

- A. Scheduled every 5 minutes
- B. Table update
- C. File arrival
- D. Manual

**27.** In a job's task graph, Task B depends on Task A, and Task C has no dependencies. Which statement is true?

- A. Task C waits for Task B.
- B. Tasks A and C can run in parallel.
- C. All tasks always run in sequence.
- D. Task B runs before Task A.

**28.** Data arrives at irregular times. Which trigger choice fits best?

- A. An hourly scheduled trigger
- B. A data-driven trigger (file arrival or table update)
- C. A manual trigger
- D. A continuous trigger that checks every second

**29.** Which task type runs a Lakeflow Spark Declarative Pipeline as part of a job?

- A. Pipeline task
- B. SQL task
- C. Dashboard task
- D. Script task

---

## Section 5: Implementing CI/CD

**30.** You have committed changes in a Databricks Git folder and want to send them to the remote branch. Which action do you use?

- A. Pull
- B. Commit & Push
- C. Clone
- D. Sync only

**31.** A bundle deploys the same code to dev and prod. The catalog name differs per environment. Which feature handles this?

- A. Bundle targets with variables and overrides
- B. Hardcoding the catalog name in each notebook
- C. Notebook widgets only
- D. Spark configuration files

**32.** Before deploying a bundle, which CLI command checks the configuration for errors?

- A. `databricks bundle validate`
- B. `databricks workspace list`
- C. `databricks clusters start`
- D. `databricks fs cp`

**33.** Which file defines a bundle's resources, targets, and variables?

- A. `databricks.yml`
- B. `requirements.txt`
- C. `pyproject.toml`
- D. `.gitignore`

**34.** Your team wants every merge to `main` to validate and deploy the bundle to production automatically. Which setup is best?

- A. Engineers edit notebooks directly in the prod workspace.
- B. A CI job runs `databricks bundle validate` and then `databricks bundle deploy -t prod`.
- C. Notebooks are copied to prod by email.
- D. Deployment runs only in dev.

---

## Section 6: Troubleshooting, Monitoring, and Optimization

**35.** You want to compare the current run duration of a job with its historical runs. Where do you look?

- A. The Lakeflow Jobs run history view
- B. Unity Catalog lineage
- C. The notebook revision history
- D. The cluster event log only

**36.** In the Spark UI, one stage has most tasks finishing in under 30 seconds, but a single task runs for over 10 minutes and has far more shuffle read than the median. What is the most likely cause?

- A. Disk spill caused by a missing cache
- B. Data skew
- C. Too few executors in the cluster
- D. A missing schema

**37.** Which Spark UI metric shows that data was written to disk because memory was insufficient?

- A. Spill (memory and disk) in stage metrics
- B. Job ID
- C. Storage tab only
- D. Executor count

**38.** Which feature replaces manual partitioning and `ZORDER` for clustering data on query columns?

- A. Liquid clustering (`CLUSTER BY`)
- B. Bloom filters only
- C. Partitioning by every column
- D. Caching

**39.** A cluster fails to start with a library installation conflict. Where should you look first?

- A. The cluster event log and driver logs
- B. Unity Catalog lineage
- C. The Git folder history
- D. A dashboard

---

## Section 7: Governance and Security

**40.** You drop a managed table in Unity Catalog. What happens?

- A. Only the metadata is removed, and the data files stay in storage.
- B. The metadata and the underlying data files are removed.
- C. The statement fails while the table has data.
- D. The table moves to the recycle bin and never expires.

**41.** Another system writes to the same storage path, and dropping the table should keep those files. Which table type should you choose?

- A. Managed table
- B. External table
- C. Temporary view
- D. Streaming table

**42.** Which pair of statements gives the `analysts` group read access to tables in the `main.sales` schema?

- A. `GRANT SELECT ON TABLE main.sales.orders TO analysts`
- B. `GRANT USE CATALOG ON CATALOG main TO analysts` and `GRANT USE SCHEMA, SELECT ON SCHEMA main.sales TO analysts`
- C. `REVOKE ALL ON SCHEMA main.sales FROM analysts`
- D. `DENY SELECT ON SCHEMA main.sales TO analysts`

**43.** You need to restrict which rows a user sees based on group membership. Which feature does this?

- A. Row filter
- B. Column mask
- C. Liquid clustering
- D. `VACUUM`

**44.** Non-privileged users should see a masked Social Security number, while privileged users see the full value. Which feature does this?

- A. Column mask
- B. Row filter
- C. Delta time travel
- D. Z-ordering

**45.** You need one central policy that masks every column tagged as PII across many schemas. Which feature does this?

- A. Attribute-based access control (ABAC) policy
- B. A separate GRANT on each table
- C. Manual column edits in each table
- D. Copying the data into a restricted schema

---

**End of exam.** Record your score and each question you're unsure about, then check the answer key.
