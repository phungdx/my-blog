---
date: 2026-03-15
categories:
  - Pyspark
---
Sometimes you run into issues with spark such as OOM, shuffle spill, etc. Here are some tips to optimize your spark job.

## 1. Broadcast join

- Use broadcast join when one of the tables is small (less than 100MB).
- You can use `spark.sql.autoBroadcastJoinThreshold` to set the threshold.
- You can also use `broadcast()` function to broadcast a table.

## 2. Partition pruning

- Partition pruning is a technique to reduce the amount of data read from disk.
- It is done by filtering the data based on the partition columns.