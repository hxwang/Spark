## Spark Components

### Driver
- Every Spark application consists of a `driver` program that launches various parallel operations on a cluster. The driver program
  - contains your application's main function and 
  - defines distributioned datasets on the cluster.
  - then apply operations to them
- Driver programs access Spark through a `SparkContext` object, which represents a connection to a computing cluster.

<img src="./figs/components-dist.PNG" width="600" />


