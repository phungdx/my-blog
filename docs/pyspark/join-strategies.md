# Join Strategies in Spark

Apache Spark provides several join strategies to efficiently combine datasets. The choice of strategy depends on data size, partitioning, and available resources.

## 1. Broadcast Hash Join
- **When used:** One dataset is small enough to fit in memory.
- **How it works:** The smaller dataset is broadcast to all worker nodes, and each node joins it with its partition of the larger dataset.
- **Pros:** Fast, avoids shuffling large data.
- **Cons:** Limited by memory size.

## 2. Shuffle Hash Join
- **When used:** Both datasets are large, but at least one can fit in memory after shuffling.
- **How it works:** Both datasets are shuffled on the join key, and a hash table is built for one side.
- **Pros:** Efficient for medium-sized data.
- **Cons:** Involves shuffling, which can be expensive.

## 3. Sort Merge Join
- **When used:** Both datasets are large and already sorted or can be sorted efficiently.
- **How it works:** Datasets are shuffled and sorted on the join key, then merged.
- **Pros:** Scales to very large datasets.
- **Cons:** Sorting and shuffling can be costly.

## 4. Cartesian Join
- **When used:** No join keys are specified.
- **How it works:** Every row of one dataset is joined with every row of the other.
- **Pros:** Rarely used intentionally.
- **Cons:** Extremely expensive; avoid if possible.

## Choosing a Strategy
- Spark automatically selects the join strategy based on data size and configuration.
- You can influence the strategy using hints (e.g., `broadcast()`), or by tuning Spark settings.

## References
- [Spark SQL Join Strategies Documentation](https://spark.apache.org/docs/latest/sql-performance-tuning.html#join-strategies)