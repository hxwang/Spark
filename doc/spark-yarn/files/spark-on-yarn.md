## Spark on Yarn
- [ref](http://badrit.com/blog/2015/2/29/running-spark-on-yarn#.VbJ46bNVhBc)

### YARN-Client Mode
- In yarn-client mode, the driver runs in the client process, and the application master is only used for requesting resources from YARN.
- Yarn-client mode makes sense for interative and debugging uses where you want to see your application's output immediately (on the client process side).


### YARN-Cluster Mode
- In yarn-cluster mode, the Spark driver runs inside an application master process which is managed by Yarn on the cluster, and the client can go away after initating the application.
- Yarn-cluster mode makes sense for production jobs.

### Why Run on Yarn
- Running Spark on YARN has some benefits
  - YARN allows to dynamically share the cluster resources between different frameworks that run on YARN. For example, you can run a mapreduce job after that you can run a Spark job without any changes in YARN configurations. (??? what does it mean)
  - You can use YARN scheduler for categorizing, isolating, and prioritizing workloades.
  - YARN is the only cluster manager for Spark that supports security. With YARN, Spark can use secure authentication between its process.
