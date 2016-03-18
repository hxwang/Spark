## Spark Functions

### Element-wise transformation
- `map()`
  - transform each element to a new value
- `filter()`
  - takes in a function and returns an RDD that only has elements that pass the `filter()` function
- `flatmap()`
  - we use it when we want to produce multiple output elements for each input element.
  ```java
  JavaRDD<String> lines = sc.parallelize(Arrays.asList("hello world", "hi"));
  JavaRDD<String> words = lines.flatMap(new FlatMapFunction<String, String>(){
    public Iterable<String> call(String line){
      return Arrays.asList(line.split(" "));
    }
  });
  words.first
  ```
- `distinct()`
  - remove duplicates
- `foreach(func)`
  - apply the provided function to  each element of the RDD
  - return nothing
