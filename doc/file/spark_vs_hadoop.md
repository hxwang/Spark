## Spark v.s. Hadoop

### Why spark is so fast
- It can run as a standalone or on top of Hadoop YARN, where it can read data directly from HDFS. 


### Spark v.s. Different
- Memory
  - Spark processes data in-memory
    - Spark needs a lot of memory. Much like standard DBs, it loads a process into memory and keeps it there until further notice.
  - Hadoop MapReduce persists back to the disk after a map or reduce action
    - MapReduce, however, kills its processes as soon as a job is done, so it can easily run alongside other services with minor performance differences.
  - Comments
    - thus Spark could be faster than Hadoop
    - Spark is better at iterative computations that need to pass over the same data many times. 
    - But when it comes to one-pass ETL-like job, for example, data transformation or data integration, then MapReduce is the deal
- Ease of use
  - Spark has comfortable APIs for Java, Scala and Python
  - Hadoop MapReduce is written in Java and is infamous for being very difficult to program. MapReduce doesn't have an interative mode.
- Cost
  - Spark requires a lot of memory to achieve optimal performance.
- Compatibility
  - Spark can run as stonealone or on top of Hadoop YARN or on the cloud.
  - It supports data sources that it implement Hadoop InputFormat, so it can integrate with all the data sources and file formats that are supported by Hadoop.
- Data Processing
  - Spark can do more than plain data processing, it can process graphs and use the existing machine-learning libraries. Spark can do real-time processing as well as batch processing.
  - Hadoop is great for batch processing. But Hadoop will need to use different platforms for different types of data processing. For example, use Impala for real-time, use Giraph for graph processing.
- Failure Tolerance
  - MapReduce relies on hard drives, if a process crashes in the middle of execution, it could continue where it left off, where Spark will have to start from the beginning.

- Security
  - Spark is a little bare.
    - Authentication is supported via a shared secret, the Web UI can be secured via javax servlet filters, and event logging is included.
    - Spark can run on YARN and use HDFS, which means that it can enjoy Kerberos authentication, HDFS file permissions and encryption between nodes.
  - Hadoop MapReduce can enjoy all the Hadoop security benefits and integrate with Hadoop security projects. 
  
- Summary
  - For Spark, you still need HDFS to store the data and you may want to use HBasem Hive, Pig, Impala or other Hadoop projects. This means you'll still need to run Hadoop and MapReduce alongside Spark for a full Big Data package.
