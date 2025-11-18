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

