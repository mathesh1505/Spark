# SPARK
# Hadoop Introduction: 
Hadoop is an open-source framework designed to store and process large volumes of data (Big Data) efficiently across a cluster of computers.It follows a distributed computing model, meaning work is divided among many machines, enabling faster and scalable processing.
# Key Roles of Hadoop in Distributed Computing:
# Distributed Storage
* Hadoop stores data using HDFS (Hadoop Distributed File System).
* Data is split into blocks and stored across multiple nodes, ensuring scalability.
# Distributed Processing
* Uses MapReduce for parallel processing.
* Tasks are divided into smaller sub-tasks and executed concurrently across nodes.
# Fault Tolerance
* Automatic data replication ensures system works even if nodes crash.
# Scalability
Easily expand by adding more nodes without major system redesign.
# Cost Effective
Uses inexpensive commodity hardware.
* HDFS (Storage Layer)
* YARN (Resource Management Layer)
* MapReduce (Processing Layer)
# Historical Context and Evolution:
The idea of Hadoop originated from Google’s research on large-scale data processing.
Google published two influential papers:
GFS – Google File System (2003)
MapReduce programming model (2004)
# Spark Introduction:
Apache Spark is an open-source, distributed data processing engine designed for fast computation of large-scale data.It supports in-memory processing, making it significantly faster than Hadoop MapReduce.
# Spark Architecture Overview:
Key Components of Spark Architecture
Spark follows a master-slave distributed architecture with the following components:
# Driver Program
* Main application that runs the user code
* Converts code into tasks
* Sends tasks to executors
# Cluster Manager
* Allocates resources to applications
* Types:
* Standalone
* YARN
* Mesos
* Kubernetes
# Executors
* Worker processes running on cluster nodes
* Execute tasks assigned by the driver
* Store data in memory
# Workers
* Nodes that run executors
# RDD (Resilient Distributed Dataset)
* Fundamental data structure in Spark
* Immutable, distributed data collection
# Interaction Between Components During Execution
Step-by-Step Workflow
# Submit Application
* User submits Spark code
* Driver begins execution
# Driver Program Starts
* Creates SparkContext
* Communicates with Cluster Manager
# Resource Allocation
* Cluster Manager allocates resources
* Launches executors on workers
# Task Distribution
* Driver sends tasks to executors
# Execution
* Executors run tasks in parallel
* Store intermediate data in memory
# Data Storage
* Results are stored in executors (cache) or disk
# Completion
* Executors return results to driver
* Driver produces final output
# Shutdown
* Resources are released
# Driver (Main Program)
* The Driver is the program where your main() function runs.
* Creates SparkSession
* Converts code → DAG
* Sends tasks to executors
* Collects results
# Executors:
* Run tasks in parallel
* Store data in memory for fast processing
* Report results back to the Driver
* Example
* If your dataset has 1GB and 4 executors:
* Spark splits data into 4 partitions
* Each executor processes one partition
# Cluster Manager (Resource Allocator)
* Cluster Manager allocates CPU, memory, and machines to Spark.
# Core components
# RDD (Resilient Distributed Dataset):
RDD is the fundamental data structure in Spark.Immutable (cannot be changed once created).Distributed across the cluster.Suitable for low-level transformations
* Uses of RDD:
* When you need fine control over data
* When working with unstructured data (text, logs)
* When transformations are complex and need custom functions
* Best for low-level operations
# Spark Core:
The base engine of Apache Spark.Every other Spark module (SQL, Streaming, MLlib, GraphX) is built on top of Spark Core.
* Spark Core Includes:
* Task scheduling
* Memory management
* Fault tolerance
* Interacting with storage systems
* RDD creation and operations
# Spark SQL:
A Spark module used for structured data processing.
* It provides:
* DataFrames (like tables)
* SQL queries
* Integration with Hive
* Catalyst Optimizer → improves performance
# Spark Streaming:
A module for processing real-time data streams.
* Examples of streaming sources:
* Kafka
* Socket
* Flume
* File streams
* It have Two Types:
* DStream API (older)
* Structured Streaming (modern, recommended)
# MLlib (Machine Learning Library):
Spark’s machine learning library used for:
* Classification
* Regression
* Clustering
* Recommendation
* Feature engineering
* Pipelines
# GraphX:
GraphX is Spark’s graph processing API used for:
* Social network analysis
* PageRank
* Graph traversal
* Finding connections between entities
# DataFrame:
Distributed collection of data in rows and columns (like a SQL table)Built on top of RDDs
Has schema
Uses Catalyst Optimizer → very fast
Best API for Python, Scala, Java
# Dataset:
Extension of DataFrame with type-safety.Available only in Scala & Java, NOT in Python
* Mix of:
* RDD (strong typing)
* DataFrame (optimization)
# Converting RDD to DataFrame:
<img width="1077" height="952" alt="Screenshot 2025-11-20 181042" src="https://github.com/user-attachments/assets/b74dbd60-41e0-4b0a-a64b-2946b0229ece" />

# Converting DataFrame to RDD:
<img width="1076" height="714" alt="Screenshot 2025-11-20 182744" src="https://github.com/user-attachments/assets/393f8c41-3de3-40c6-8865-1f6d9ae97598" />

# Transformations:
Transformations are operations that produce a new RDD / DataFrame / Dataset from an existing one. They are lazy (Spark builds a logical plan / DAG but won’t execute until an action is called). Transformations are how you modify or prepare data before an action (like collect(), count(), save()).
# Narrow Transformations:
Narrow transformation is one where each output partition depends only on a single input partition. No data needs to be redistributed across the network between partitions — Spark can compute tasks using only local data. Narrow transformations do not cause a shuffle.
# Examples
* map, filter, flatMap, mapPartitions, sample, union
# Wide Transformations:
Wide transformation is one where the output partition depends on data from multiple input partitions — Spark must shuffle data across the network to reorganize it. Wide transformations create shuffle boundaries and separate stages in the DAG.
# Examples
*reduceByKey, groupByKey, groupBy, aggregateByKey,join, cogroup, distinct, repartition, sortByKey, orderBy (DataFrames), groupBy().
# Shuffling in Spark:
Shuffle is a redistributing data across the network so that records with the same key (or partitioning) end up together.
