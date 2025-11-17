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

### Spark RDD


What are the limitation of UDF user define functions 
- Lack of optimization: Catalyst optimizer cannot see into a UDF to optimize it, treating it as a black box
- Serialization overhead using arrow

Spark RDD: Resilient distributed dataset is fundamental data structure in spark
- Resilient are fault tolerant because their linage is tracked
- Immutable: Once a n RDD is create it can not be changed any transformation results in a new RDD
- Lazy Evaluation
- Distributed
