## Spark RDD

### RDD intro
- RDD in Spark is simply an `immutable distributed collection` of objects. 
  - Each RDD is split into multiple partitions, which may be computed on different nodes of the cluster.
  - RDDs can contains any type of Python, Java or Scala objects, including user-defined classes.

### Create RDD
- Users create RDDs in two ways
  - by loading an external dataset
  - or by distributing a collection of objects (e.g., a list or set) in their driver program.
  
