## Spark Log

### Files
- You can create a file in the `conf` direcotory called `log4j.properies`. 
  - The Spark developers already include a template for this file called `log4j.properties.template`
  - You can copy a new one, and named `conf/log4j.properties`
  - In this file
    - `log4j.rootCategory=INFO, console`, we can change it to `log4j.rootCategory=WARN, console` to show only the WARN messages.
  - onces you have add the log4j properties, you can use the `--files` flag of `spark-submit`
- log4j
  - spark's logging system is based on log4j, a widely used Java logging library, and uses log4j's configuration format.
  - log4j works by scanning the classpath for the first properies file it finds, and will ignore your customization if it finds properties somewhere else.

  
### YARN-Cluster
- The easitest way to collect logs is to use YARN's log collection tool
  - running `yarn logs -applicationId <app Id>` to produce a report containing logs from your application
  - But this will only work after an application has fully finished, since YARN must first aggregate these logs together.
  - For the running application, you can access the log through the resource manager.
  
