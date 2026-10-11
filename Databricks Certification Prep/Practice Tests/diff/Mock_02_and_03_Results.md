# Mock Exam Results: Mock 02 and Mock 03

Graded against the answer keys in the parent folder. Score: 36+ is a strong result.

## Summary

| Mock | Score | Missed questions |
|---|---|---|
| Mock 02 | 42 / 45 | 5, 7, 17 |
| Mock 03 | 37 / 45 | 5, 6, 10, 14, 15, 18, 19, 39 |

Combined: 79 / 90 (about 88%).

## Mock 02: Section Breakdown

| Section | Topic | Weight | Score | Miss rate |
|---|---|---|---|---|
| 1 | Databricks Intelligence Platform | 6% | 3 / 3 | 0% |
| 2 | Data Ingestion and Loading | 21% | 7 / 9 | 22% |
| 3 | Data Transformation and Modeling | 22% | 9 / 10 | 10% |
| 4 | Working with Lakeflow Jobs | 16% | 7 / 7 | 0% |
| 5 | Implementing CI/CD | 10% | 5 / 5 | 0% |
| 6 | Troubleshooting, Monitoring, and Optimization | 10% | 5 / 5 | 0% |
| 7 | Governance and Security | 15% | 6 / 6 | 0% |

### Mock 02 Misses

| # | Your answer | Correct | Topic |
|---|---|---|---|
| 5 | D | B | `schemaLocation` stores the inferred schema and its changes (Auto Loader) |
| 7 | A | B | File notification mode scales better than directory listing for high volume |
| 17 | D | A | `explode` produces one row per array element |

## Mock 03: Section Breakdown

| Section | Topic | Weight | Score | Miss rate |
|---|---|---|---|---|
| 1 | Databricks Intelligence Platform | 6% | 3 / 3 | 0% |
| 2 | Data Ingestion and Loading | 21% | 6 / 9 | 33% |
| 3 | Data Transformation and Modeling | 22% | 6 / 10 | 40% |
| 4 | Working with Lakeflow Jobs | 16% | 7 / 7 | 0% |
| 5 | Implementing CI/CD | 10% | 5 / 5 | 0% |
| 6 | Troubleshooting, Monitoring, and Optimization | 10% | 4 / 5 | 20% |
| 7 | Governance and Security | 15% | 6 / 6 | 0% |

### Mock 03 Misses

| # | Your answer | Correct | Topic |
|---|---|---|---|
| 5 | C | D | `FILEFORMAT` specifies the source format in `COPY INTO` |
| 6 | D | A | Mismatched data goes to `_rescued_data` by default |
| 10 | D | A | `cloudFiles.schemaHints` overrides types for specific columns |
| 14 | D | A | `pivot` turns distinct column values into new columns |
| 15 | A | C | `coalesce` (function) returns the first non-null argument |
| 18 | B | A | `left_anti` returns left rows with no match on the right |
| 19 | C | A | `coalesce` (DataFrame method) reduces partitions without a full shuffle |
| 39 | A | B | Write results to a table instead of collecting them on the driver |

## Patterns

- **Auto Loader and `COPY INTO` options** caused misses in both mocks (Mock 02 Q5, Q7; Mock 03 Q5, Q6, Q10). Ingestion is the top review priority.
- **`coalesce` has two meanings** and was missed in both forms (Mock 03 Q15, Q19). Keep the column-function and DataFrame-method meanings separate.
- **Transformation functions** account for the remaining Mock 03 misses (Q14 `pivot`, Q18 `left_anti`), and Mock 02 Q17 `explode` was a basic slip.

## Next Steps

1. Review Auto Loader and `COPY INTO` options against docs.databricks.com.
2. Review SQL and DataFrame functions: `coalesce`, `pivot`, `left_anti`, `explode`.
3. Retake the missed questions without looking at the answers.
4. Take a fresh set of questions on ingestion and transformation.
