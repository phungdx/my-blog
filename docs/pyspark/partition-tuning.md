# Partition Tuning in Spark

Partition tuning is crucial for optimizing the performance of Spark jobs. It involves adjusting the number and size of partitions to balance workload and resource utilization.

## Why Partition Tuning Matters

- **Parallelism:** More partitions allow better parallel processing.
- **Resource Utilization:** Proper partitioning prevents resource underutilization or excessive overhead.
- **Shuffle Efficiency:** Reduces data movement and network I/O during shuffles.

## Key Concepts

- **Default Partitioning:** Spark uses a default number of partitions (e.g., 200 for shuffles).
- **Repartitioning:** Use `repartition()` to increase partitions (causes a full shuffle).
- **Coalescing:** Use `coalesce()` to decrease partitions (minimizes shuffling).

## Best Practices

- **Input Size:** Aim for partition sizes of 100–200 MB for optimal performance.
- **Cluster Resources:** Match partitions to the number of available cores.
- **Avoid Small Files:** Too many small partitions/files can degrade performance.

## Example

```python
# Increase partitions
df = df.repartition(100)

# Decrease partitions
df = df.coalesce(10)
```

## Monitoring

Use the Spark UI to monitor stages and tasks, and adjust partitioning as needed.

## References

- [Spark Tuning Guide](https://spark.apache.org/docs/latest/tuning.html)
- [Partitioning in Spark](https://spark.apache.org/docs/latest/rdd-programming-guide.html#rdd-partitions)