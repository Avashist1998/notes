### Spark

Spark is a distributed computing framework that is used to process data in parallel, it is built on top of the JVM, and it is written in Scala. Most data engineers and scientists use pyspark to interact with spark.

Spark has two sessions:
- Driver (Primary/Master)
- This is the entry point to the spark program, it is used to create the spark context and the spark session.
- Executor (Worker/Slave)
- This is the worker node that is used to execute the tasks.

Spark basically works by creating a graph of the tasks to be executed, and then it is executed by the executors. The graph is a directed acyclic graph (DAG), and it is used to represent the dependencies between the tasks. 

Lazy Evaluation: The tasks are not executed until the action is called.
- This is to avoid unnecessary computations, and allows for more efficient execution.

Basic flow of a spark program:
- Read the data from the source (e.g. CSV, JSON, Parquet, etc.)
- Transform the data (e.g. filter, map, reduce, etc.)
- Write the data to the destination (e.g. CSV, JSON, Parquet, etc.)


### PySpark

PySpark is the python API for Spark, it is built on top of the JVM, and it is written in Python. PySpark is a wrapper around the Spark Java API, and it is used to interact with spark.

Pyspark run the python code in one process but hands off the heavy work to the JVM based Spark driver/executor process.


#### Diagram
```mermaid
+-------------------+          Py4J           +-----------------------+
| Python Process    | <---------------------> | JVM Spark Driver      |
| - PySpark API     |                        | - SparkSession         |
| - Your code       |                        | - Query Optimizer      |
+-------------------+                        +-----------+-----------+
                                                        |
                                                        | distributes tasks
                                    +-------------------+-------------------+
                                                        v
                                    |   JVM Spark Executors (Cluster)       |
                                    |   - Execute tasks                      |
                                    |   - Perform shuffles, joins, etc      |
                                    +----------------------------------------+
```

### Spark RDD


What are the limitation of UDF user define functions 
- Lack of optimization: Catalyst optimizer cannot see into a UDF to optimize it, treating it as a black box
- Serialization overhead using arrow

Spark RDD: Resilient distributed dataset is fundamental data structure in spark
- Resilient are fault tolerant because their linage is tracked
- Immutable: Once a n RDD is create it can not be changed any transformation results in a new RDD
- Lazy Evaluation
- Distributed



### Spark Optimization
The optimization revolves around its Catalyst Optimizer and its distributed architecture.


#### Catalyst Optimizer
- This is the Spark optimization engine which convert the user code (SQL, Python, DataFrame operations) into a execution plan
- Logical Plan Generation: User code is convert into a absract, unresolved logic plan.
- Logic Plan Opitimization: The logic plan is optimized using role based and cost based techniqueues. For example:
    - Predicate Pushdown: Push down the filters to the data source to reduce the data to be processed.
    - Column Pruning: Remove the columns that are not needed to be processed.
    - Join Reordering: Reorder the joins to reduce the number of shuffles.
- Physical Plan Generation: The logical plan is converted into a physical plan which is a set of tasks to be executed on the data. The plan consider factors like data partitions, data types, and data distribution.
- Physical Plan Selection: The engine selects the most efficent physical plan based on cost estimated and statistics.

#### Adaptive Query Execution
At runtime, the optimiation framework adapt the execution plan based on the runtime data and statistics.
- Dynamic coalescing: Combine small tasks into larger ones to reduce the number of tasks and improve the efficiency.
- Dynamic Switch join strategy: Switch between hash join and sort merge join based on the data distribution and size.
- Handle Skewed data: Mitigated performance issue caused by uneven data distribution (Hot key problem).

#### Data Partitioning and Parallelism
Spark will divide the data into smaller chunks and process them in parallel since data is distributed across the cluster. The optimizer will also consider number of partitions and custom partitioner to balance the load and improve the efficiency.

#### Resource Management
- Dynamically allocate resources to the tasks based on the workload and resource availability.
- Memory and CPU setting Tuning: Adjust the memory and CPU settings based on the workload and resource availability.

#### Data Formats and Storage
- Choose data fromats like Parquet, ORC, Avro, etc. based on the data size, type, and access patterns.
- Splitting file formats: Ensure data is split into optimal size for efficient reading and processing.

