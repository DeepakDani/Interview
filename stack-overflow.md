# ### ### # 1. # Sqoop error while importing to hdfs
### ### # Q1:13/12/04 02:05:39 ERROR 
### ### # security.UserGroupInformation:PriviledgedActionException  as:hadoop      
### ### # (auth:SIMPLE) 
### ### # cause:java.io.FileNotFoundException:
### ### # Ans : permissions,
-------------------------------------------------------------------------------------------------------------------------
1. 2014-06-16 07:43:24,308 INFO  [main] manager.MySQLManager: Preparing to use a MySQL streaming resultset.
2014-06-16 07:43:24,319 INFO  [main] tool.CodeGenTool: Beginning code generation
2014-06-16 07:43:25,004 INFO  [main] manager.SqlManager: Executing SQL statement: SELECT t.* FROM textlines AS t LIMIT 1
2014-06-16 07:43:25,026 INFO  [main] manager.SqlManager: Executing SQL statement: SELECT t.* FROM textlines AS t LIMIT 1
2014-06-16 07:43:25,060 INFO  [main] orm.CompilationManager: HADOOP_MAPRED_HOME is /home/socio/hadoop
Note: /tmp/sqoop-socio/compile/4d35eb51b72ffcde0e815ad25857257c/textlines.java uses or overrides a deprecated API.
Note: Recompile with -Xlint:deprecation for details.
2014-06-16 07:43:26,755 INFO  [main] orm.CompilationManager: Writing jar file: /tmp/sqoop-socio/compile/4d35eb51b72ffcde0e815ad25857257c/textlines.jar
2014-06-16 07:43:26,869 WARN  [main] manager.MySQLManager: It looks like you are importing from mysql.
2014-06-16 07:43:26,870 WARN  [main] manager.MySQLManager: This transfer can be faster! Use the --direct
2014-06-16 07:43:26,870 WARN  [main] manager.MySQLManager: option to exercise a MySQL-specific fast path.
2014-06-16 07:43:26,870 INFO  [main] manager.MySQLManager: Setting zero DATETIME behavior to convertToNull (mysql)
2014-06-16 07:43:26,877 INFO  [main] mapreduce.ImportJobBase: Beginning import of textlines
2014-06-16 07:43:26,878 INFO  [main] Configuration.deprecation: mapred.job.tracker is deprecated. Instead, use mapreduce.jobtracker.address
SLF4J: Class path contains multiple SLF4J bindings.
SLF4J: Found binding in [jar:file:/home/socio/hbase/lib/slf4j-log4j12-1.6.4.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: Found binding in [jar:file:/home/socio/hadoop/share/hadoop/common/lib/slf4j-log4j12-1.7.5.jar!/org/slf4j/impl/StaticLoggerBinder.class]
SLF4J: See http://www.slf4j.org/codes.html#multiple_bindings for an explanation.
2014-06-16 07:43:27,894 WARN  [main] util.NativeCodeLoader: Unable to load native-hadoop library for your platform... using builtin-java classes where applicable
2014-06-16 07:43:27,961 INFO  [main] Configuration.deprecation: mapred.jar is deprecated. Instead, use mapreduce.job.jar
2014-06-16 07:43:28,945 INFO  [main] Configuration.deprecation: mapred.map.tasks is deprecated. Instead, use mapreduce.job.maps
2014-06-16 07:43:29,030 INFO  [main] Configuration.deprecation: session.id is deprecated. Instead, use dfs.metrics.session-id
2014-06-16 07:43:29,031 INFO  [main] jvm.JvmMetrics: Initializing JVM Metrics with processName=JobTracker, sessionId=
2014-06-16 07:43:29,944 INFO  [main] mapreduce.JobSubmitter: Cleaning up the staging area file:/tmp/hadoop-socio/mapred/staging/socio1192068052/.staging/job_local1192068052_0001
2014-06-16 07:43:29,945 ERROR [main] security.UserGroupInformation: PriviledgedActionException as:socio (auth:SIMPLE) cause:java.io.FileNotFoundException: File does not exist: hdfs://mac:9000/home/socio/sqoop/lib/commons-io-1.4.jar
2014-06-16 07:43:29,945 ERROR [main] tool.ImportTool: Encountered IOException running import job: java.io.FileNotFoundException: File does not exist: hdfs://mac:9000/home/socio/sqoop/lib/commons-io-1.4.jar
    at org.apache.hadoop.hdfs.DistributedFileSystem$17.doCall(DistributedFileSystem.java:1110)
    at org.apache.hadoop.hdfs.DistributedFileSystem$17.doCall(DistributedFileSystem.java:1102)
    at org.apache.hadoop.fs.FileSystemLinkResolver.resolve(FileSystemLinkResolver.java:81)
    at org.apache.hadoop.hdfs.DistributedFileSystem.getFileStatus(DistributedFileSystem.java:1102)
    at org.apache.hadoop.mapreduce.filecache.ClientDistributedCacheManager.getFileStatus(ClientDistributedCacheManager.java:288)
    at org.apache.hadoop.mapreduce.filecache.ClientDistributedCacheManager.getFileStatus(ClientDistributedCacheManager.java:224)
    at org.apache.hadoop.mapreduce.filecache.ClientDistributedCacheManager.determineTimestamps(ClientDistributedCacheManager.java:93)
    at org.apache.hadoop.mapreduce.filecache.ClientDistributedCacheManager.determineTimestampsAndCacheVisibilities(ClientDistributedCacheManager.java:57)
    at org.apache.hadoop.mapreduce.JobSubmitter.copyAndConfigureFiles(JobSubmitter.java:264)
    at org.apache.hadoop.mapreduce.JobSubmitter.copyAndConfigureFiles(JobSubmitter.java:300)
    at org.apache.hadoop.mapreduce.JobSubmitter.submitJobInternal(JobSubmitter.java:387)
    at org.apache.hadoop.mapreduce.Job$10.run(Job.java:1268)
    at org.apache.hadoop.mapreduce.Job$10.run(Job.java:1265)
    at java.security.AccessController.doPrivileged(Native Method)
    at javax.security.auth.Subject.doAs(Subject.java:415)
    at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1491)
    at org.apache.hadoop.mapreduce.Job.submit(Job.java:1265)
    at org.apache.hadoop.mapreduce.Job.waitForCompletion(Job.java:1286)
    at org.apache.sqoop.mapreduce.ImportJobBase.doSubmitJob(ImportJobBase.java:186)
    at org.apache.sqoop.mapreduce.ImportJobBase.runJob(ImportJobBase.java:159)
    at org.apache.sqoop.mapreduce.ImportJobBase.runImport(ImportJobBase.java:239)
    at org.apache.sqoop.manager.SqlManager.importTable(SqlManager.java:600)
    at org.apache.sqoop.manager.MySQLManager.importTable(MySQLManager.java:118)
    at org.apache.sqoop.tool.ImportTool.importTable(ImportTool.java:413)
    at org.apache.sqoop.tool.ImportTool.run(ImportTool.java:502)
    at org.apache.sqoop.Sqoop.run(Sqoop.java:145)
    at org.apache.hadoop.util.ToolRunner.run(ToolRunner.java:70)
    at org.apache.sqoop.Sqoop.runSqoop(Sqoop.java:181)
    at org.apache.sqoop.Sqoop.runTool(Sqoop.java:220)
    at org.apache.sqoop.Sqoop.runTool(Sqoop.java:229)
Ans : This issue is related to inappropriate hadoop configuration. In my case the mapred.site.xml for hadoop was missing from ../etc/hadoop directory.
------------------------------------------------------------------------------------------------------------
1. [root@localhost edureka]# sqoop import --connect jdbc:mysql://192.168.56.1/Edureka --table Employee --username root -P --target-dir /sqoopOut1 -m 1;

Warning: /usr/lib/hcatalog does not exist! HCatalog jobs will fail.
Please set $HCAT_HOME to the root of your HCatalog installation.
Enter password: 
16/08/06 23:34:48 INFO manager.MySQLManager: Preparing to use a MySQL streaming resultset.
16/08/06 23:34:48 INFO tool.CodeGenTool: Beginning code generation
16/08/06 23:34:48 ERROR manager.SqlManager: Error executing statement: com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure
The last packet sent successfully to the server was 0 milliseconds ago. The driver has not received any packets from the server.
com.mysql.jdbc.exceptions.jdbc4.CommunicationsException: Communications link failure

Ans:
you should use port number in JDBC connection string:
further more, you also should use hostname instead for IP.
so if output of command hostname -f is computer.name use this in JDBC connection string:
-------------------------------------------------------------------------------------------------------
1.I have this code in which i have set one mapper and one reducer. want to include one more mapper and a reducer for doing further jobs. The problem is that i have to take the output file of the first map reduce job as the input to the next map reduce job.Is it possible to do that?if yes then how can i do it?
ANS:
yes its possible to do that. you can check the following tutorial to see how chaining occurs. http://gandhigeet.blogspot.com/2012/12/as-discussed-in-previous-post-hadoop.html

Make sure you delete the intermediate output data in HDFS which will be created by each MR phase by using fs.delete(intermediateoutputPath);
public class ChainJobs extends Configured implements Tool {

 private static final String OUTPUT_PATH = "intermediate_output";

 @Override
 public int run(String[] args) throws Exception {
  /*
   * Job 1
   */
  Configuration conf = getConf();
  FileSystem fs = FileSystem.get(conf);
  Job job = new Job(conf, "Job1");
  job.setJarByClass(ChainJobs.class);

  job.setMapperClass(MyMapper1.class);
  job.setReducerClass(MyReducer1.class);

  job.setOutputKeyClass(Text.class);
  job.setOutputValueClass(IntWritable.class);

  job.setInputFormatClass(TextInputFormat.class);
  job.setOutputFormatClass(TextOutputFormat.class);

  TextInputFormat.addInputPath(job, new Path(args[0]));
  TextOutputFormat.setOutputPath(job, new Path(OUTPUT_PATH));

  job.waitForCompletion(true); /*this goes to next command after this job is completed. your second job is dependent on your first job.*/
--------------------------------------------------------------------------------------------------------------------------
Create then build, show formatted (with column names), and drop index:
CREATE INDEX table02_index ON TABLE table02 (column3) AS 'COMPACT' WITH DEFERRED REBUILD;
ALTER INDEX table02_index ON table2 REBUILD;
----------------------------------------------------------------------------------------------------------------
Create bitmap index, build, show, and drop:
CREATE INDEX table03_index ON TABLE table03 (column4) AS 'BITMAP' WITH DEFERRED REBUILD;
ALTER INDEX table03_index ON table03 REBUILD;
----------------------------------------------------------------------------------------------------------------
You can optimize Hive queries in at least five ways: First, with a little research, you can often speed your joins by leveraging certain optimization techniques, as described on the Hive wiki. Second, column-oriented storage options can be quite helpful. Remember that the ORC file format is new as of Hive 0.11.

Third, you can partition tables. Fourth, the Hive community has provided indexing. Finally, don’t forget the hive.exec.mode.local.auto configuration variable.
-------------------------------------------------
The Difference Between ROW_NUMBER(), RANK(), and DENSE_RANK()-- these r called window function
row Number:--
SELECT v, ROW_NUMBER() OVER(ORDER BY v)
FROM t
The above query returns:

| V | ROW_NUMBER |
|---|------------|
| a |          1 |
| a |          2 |
| a |          3 |
| b |          4 |
| c |          5 |
| c |          6 |
| d |          7 |

Row()--
SELECT v, RANK() OVER(ORDER BY v)
FROM t
… then the result we’re getting is this:

| V | RANK |
|---|------|
| a |    1 |
| a |    1 |
| a |    1 |
| b |    4 |
| c |    5 |
| c |    5 |
| d |    7 |
-----------------------------------------------------------------------------------------

DENSE_RANK()----
SELECT v, DENSE_RANK() OVER(ORDER BY v)
FROM t
… to obtain

| V | DENSE_RANK |
|---|------------|
| a |          1 |
| a |          1 |
| a |          1 |
| b |          2 |
| c |          3 |
| c |          3 |
| d |          4 |
| e |          5 |

One interesting aspect of DENSE_RANK() is the fact that it “behaves like” ROW_NUMBER() when we add the DISTINCT keyword.

1
2
SELECT DISTINCT v, DENSE_RANK() OVER(ORDER BY v)
FROM t
… to obtain

| V | DENSE_RANK |
|---|------------|
| a |          1 |
| b |          2 |
| e |          5 |
| d |          4 |
| c |          3 |
 ------------------------------------------------------------------------
coalesce: 

PRIMARY_KEY	DATEFIELD1	DATEFIELD2	DATEFIELD3
1	NULL	NULL	1993-06-04
The code:


SELECT COALESCE(datefield1, datefield2, datefield3) as first_date_found
FROM
tblDates
WHERE
primary_key = 1

will return ‘1993-06-04’ 
------------------------------------------------------------------------------------------------------------------
SQL is a powerful declarative language. Like other declarative languages, there is more than one way to write a SQL statement. Although each statement’s functionality is the same, it may have strikingly different performance characteristics.

Let’s look at an example. Consider a click-stream event table:

CREATE TABLE clicks ( timestamp date, sessionID string, url string, source_ip string)

STORED as ORC tblproperties (“orc.compress” = “SNAPPY”);

Each record represents a click event, and we would like to find the latest URL for each sessionID.

One might consider the following approach:

SELECT clicks.* FROM clicks inner join (select sessionID, max(timestamp) as max_ts from clicks

group by sessionID) latest ON clicks.sessionID = latest.sessionID

and clicks.timestamp = latest.max_ts;

In the above query, we build a sub-query to collect the timestamp of the latest event in each session, and then use an inner join to filter out the rest.

While the query is a reasonable solution—from a functional point of view—it turns out there’s a better way to re-write this query as follows:

SELECT * FROM (SELECT *, RANK() over (partition by sessionID,order by timestamp desc) as rank FROM clicks) ranked_clicks WHERE ranked_clicks.rank=1;

Here we use Hive’s OLAP functionality (OVER and RANK) to achieve the same thing, but without a Join. Clearly, removing an unnecessary join will almost always result in better performance, and when using big data this is more important than ever. You may find many cases where queries are not optimal — so look carefully at every query and consider if a rewrite can make it better and faster.

De-normalizing data:

Normalization is a standard process used to model your data tables with certain rules to deal with redundancy of data and anomalies. In simpler words, if you normalize your data sets, you end up creating multiple relational tables which can be joined at the run time to produce the results. Joins are expensive and difficult operations to perform and are one of the common reasons for performance issues . Because of that, it’s a good idea to avoid highly normalized table structures because they require join queries to derive the desired metrics.

Use Vectorization:

Vectorized query execution improves performance of operations like scans, aggregations, filters and joins, by performing them in batches of 1024 rows at once instead of single row each time.

Introduced in Hive 0.13, this feature significantly improves query execution time, and is easily enabled with two parameters settings:

set hive.vectorized.execution.enabled = true;

set hive.vectorized.execution.reduce.enabled = true;

Use ORC File:

Hive supports ORCfile, a new table storage format that sports fantastic speed improvements through techniques like predicate push-down, compression and more.

Using ORCFile for every HIVE table is extremely beneficial to get fast response times for your HIVE queries.

As an example, consider two large tables A and B (stored as text files, with some columns not all specified here), and a simple query like:

SELECT A.customerID, http://A.name, A.age, A.address join B.role, B.department, B.salary

ON A.customerID=B.customerID;

This query may take a long time to execute since tables A and B are both stored as TEXT. Converting these tables to ORCFile format will usually reduce query time significantly:

CREATE TABLE A_ORC (customerID int, name string, age int, address string)

STORED AS ORC tblproperties (“orc.compress" = “SNAPPY”);

INSERT INTO TABLE A_ORC SELECT * FROM A;

CREATE TABLE B_ORC (customerID int, role string, salary float, department string)

STORED AS ORC tblproperties (“orc.compress" = “SNAPPY”);

INSERT INTO TABLE B_ORC SELECT * FROM B;

SELECT A_ORC.customerID, A_ORC.name, A_ORC.age, A_ORC.address join B_ORC.role, B_ORC.department, B_ORC.salary ON A_ORC.customerID=B_ORC.customerID;

ORC supports compressed storage (with ZLIB or as shown above with SNAPPY) but also uncompressed storage.

Converting base tables to ORC is often the responsibility of your ingest team, and it may take them some time to change the complete ingestion process due to other priorities. The benefits of ORCFile are so tangible that I often recommend a do-it-yourself approach as demonstrated above – convert A into A_ORC and B into B_ORC and do the join that way, so that you benefit from faster queries immediately, with no dependencies on other teams.

Cost Based Query Optimization:

Hive optimizes each query’s logical and physical execution plan before submitting for final execution. These optimizations are not based on the cost of the query – that is, until now.

A recent addition to Hive, CBO, performs further optimizations based on query cost, resulting in potentially different decisions: how to order joins, which type of join to perform, degree of parallelism and others.

To use CBO, set the following parameters at the beginning of your query:

set hive.cbo.enable=true;

set hive.compute.query.using.stats=true;

set hive.stats.fetch.column.stats=true;

set hive.stats.fetch.partition.stats=true;

Then, prepare the data for CBO by running Hive’s “analyze” command to collect various statistics on the tables for which we want to use CBO.

For example, in a table tweets we want to collect statistics about the table and about 2 columns: “sender” and “topic”:

analyze table tweets compute statistics;

analyze table tweets compute statistics for columns sender, topic;

With HIVE 0.14 (on HDP 2.2) the analyze command works much faster, and you don’t need to specify each column, so you can just issue:

analyze table tweets compute statistics for columns;

That’s it. Now executing a query using this table should result in a different execution plan that is faster because of the cost calculation and different execution plan created by Hive.

Parallel execution:

Hadoop can execute MapReduce jobs in parallel, and several queries executed on Hive automatically use this parallelism. However, single, complex Hive queries commonly are translated to a number of MapReduce jobs that are executed by default sequencing. Often though, some of a query’s MapReduce stages are not interdependent and could be executed in parallel. They then can take advantage of spare capacity on a cluster and improve cluster utilization while at the same time reducing the overall query executions time. The configuration in Hive to change this behavior is merely switching a single flag

SET hive.exec.parallel=true.

Input Format Selection:

Input formats play a critical role in Hive performance. For example JSON, the text type of input formats, is not a good choice for a large production system where data volume is really high. These type of readable formats actually take a lot of space and have some overhead of parsing ( e.g JSON parsing ). To address these problems, Hive comes with columnar input formats like RCFile, ORC etc. Columnar formats allow you to reduce the read operations in analytics queries by allowing each column to be accessed individually. There are some other binary formats like Avro sequence files, Thrift and ProtoBuf, which can be helpful in various use cases too.

Partitioning Tables:

Hive partitioning is an effective method to improve the query performance on larger tables . Partitioning allows you to store data in separate sub-directories under table location. It greatly helps the queries which are queried upon the partition key(s). Although the selection of partition key is always a sensitive decision, it should always be a low cardinal attribute, e.g. if your data is associated with time dimension, then date could be a good partition key. Similarly, if data has association with location, like a country or state, then it’s a good idea to have hierarchical partitions like country/state.

Bucketing:

Bucketing improves the join performance if the bucket key and join keys are common. Bucketing in Hive distributes the data in different buckets based on the hash results on the bucket key. It also reduces the I/O scans during the join process if the process is happening on the same keys (columns).

Additionally it’s important to ensure the bucketing flag is set (SET hive.enforce.bucketing=tr

ue;) every time before writing data to the bucketed table. To leverage the bucketing in the join operation we should SET hive.optimize.bucketmapjo

in=true. This setting hints to Hive to do bucket level join during the map stage join. It also reduces the scan cycles to find a particular key because bucketing ensures that the key is present in a certain bucket.

Sampling:

Sampling allows users to take a subset of dataset and analyze it, without having to analyze the entire data set. If a representative sample is used, then a query can return meaningful results as well as finish quicker and consume fewer compute resources.

Hive offers a built-in TABLESAMPLE clause that allows you to sample your tables. TABLESAMPLE can sample at various granularity levels – it can return only subsets of buckets (bucket sampling), or HDFS blocks (block sampling), or only first N records from each input split. Alternatively, you can implement your own UDF that filters out records according to your sampling algorithm.

Map join:

Map joins are really efficient if a table on the other side of a join is small enough to fit in the memory . Hive supports a parameter, hive.auto.convert.join, which when it’s set to “true” suggests that Hive try to map join automatically.

Optimize join performance:

The next example extends the above discussion of using clustered fields (bucketed fields) to improve join performance. The optimization is turned off by default for many versions of Hive. Enable the optimization with the following settings.

set 	hive.optimize.bucketmapjoin=true;
set 	hive.optimize.bucketmapjoin.sortedmerge=true;
Note: The second setting takes advantage of clustered fields which are also sorted.

Compress map/reduce output:

Compression techniques significantly reduce the intermediate data volume, which internally reduces the amount of data transfers between mappers and reducers. All this generally occurs over the network. Compression can be applied on the mapper and reducer output individually. Keep in mind that gzip compressed files are not splittable. That means this should be applied with caution. A compressed file size should not be larger than a few hundred megabytes . Otherwise it can potentially lead to an imbalanced job. Other options of compression codec could be snappy, lzo, bzip, etc.

For map output compression set mapred.compress.map.output to true
For job output compression set mapred.output.compress to true
Avoid Global sorting:

Global sorting in Hive can be achieved with ORDER BY but this comes with a drawback as ORDER BY produces the result by setting the number of reducers to 1, making it very inefficient for large datasets.

In Hive, ORDER BY is not a very fast operation because it forces all the data to go into the same reducer node. By doing this, Hive ensures that the entire dataset is totally ordered.

Considering the Cardinality within GROUP BY:

There’s a probability where GROUP BY becomes a little bit faster, by carefully ordering a list of fields within GROUP BY in an order of high cardinality.

Write select uid, gender group by uid.gender rather than writing select uid, gender group by gender, uid.

-->SNAPPY for time based performance, ZLIB for resource performance(Drive Space)(But zlib is better than snaapy).
create table mytest (
...
)
STORED AS ORC
tblproperties("orc.stripe.size"=67108864); -- 64MB Stripes
tblproperties("orc.row.index.stride"=50000); -- 50K index strid
----------------------------------------------------------------------------------------
difference bw hiveql,impalaql, and sparksql
for  connecting to the cluster -- set -o vi
                                   ssh <cluster name >
-- Hive works on the top of MR and Yarn.
-- for changeing setting from MR to Tez in Hive .
set hive.execution.engine;
o/p hive.execution.engine=mr
set hive.execution.engine=tez;
--------------------------------------------------------------------------------------------------------
http://www.evoketechnologies.com/blog/hadoop-counters-mapreduce-api-example/
----------------------------------------------------------------------------------------------
How do I read Snappy compressed files on HDFS without using Hadoop?
ans:hadoop fs -text filename
------------------------------------------------------------------------------------------------------
qoop Import - Query must contain '$CONDITIONS' in where clause

error :Query [select * from reason where id>20] must contain '$CONDITIONS' in WHERE clause.
Sqoop requires to access metadata of table for example column type information. Placeholder $CONDITIONS is by default set to '1 = 0' to ensure that sqoop receives only type information. So, after executing sqoop command you will see first query that gets fired is with default $CONDITIONS. Later on, it is substituted by different values defining different ranges based on number of mappers (-m) or --split-by column or --boundary-query so that entire data set can be divided into different data slices or chunks and chunks can be imported in parallel with as much as concurrency available. Sqoop will automatically substitute this placeholder with the generated conditions specifying which slice of data should be transferred by each individual task.
For example, consider sample_data table with columns name, id and salary. You want to fetch records with salary > 1k.

 sqoop import \ 
    --connect "jdbc:mysql://quickstart.cloudera:3306/retail_db" \
    --username retail_dba --password cloudera \
    --query 'select * from sample_data where $CONDITIONS AND salary > 1000' \
    --split-by salary \
    --target-dir hdfs://quickstart.cloudera/user/cloudera/sqoop_new

Following is first query which returns empty set.

_SqlManager: Executing SQL statement: select * from sample_data where  (1 = 0)  AND salary > 1000_
_Then next query is to get min and max of range._
_INFO db.DataDrivenDBInputFormat: BoundingValsQuery: SELECT MIN(salary), MAX(salary) FROM (select * from sample_data where  (1 = 1)  AND salary > 1000) AS t1;
-------------------------------------------------------------------------------------------------------
https://community.cloudera.com/t5/Data-Ingestion-Integration/Sqoop-import-exception-java-lang-NoClassDefFoundError-org-json/td-p/50758
--------------------------------------------------------------------------------------------------------
When using --incremental lastmodified option in sqoop command line "the second job will take both the old and new data and will merge them together into the final output, preserving only the last updated value for each row."
However, when I try to run incremental lastmodified twice, the second time I get "FileAlreadyExistsException: Output directory already exists".
The incremental lastmodified should read from this directory to get the data from the last run and should not throw an exception.
still open
--------------------------------------------------------------------------------

Hi,
I have this very weird issue, using sqoop to pulling data from oracle to hdfs/hive, i have three jobs running, total records is 312,163,901, but it stops at 312,160,000, the jobs show as running, but it hangs and nohting in the log and no update.
A different table works fine.
To me somehow the last 3901 got stuck, can someone help or give some hints?
ans : 

This is due to java heap space issue. 
 
Pls try the below steps
1. Check the current mapreduce.map.memory.mb and mapreduce.reduce.memory.mb (there are different ways to check - you can use either Cloudera manager -> Yarn -> configuration (or) from hive/beeline CLI (or) mapred-site.xml or yarn-site.xml )
2. Increase (1 or 2 GB) java heap space temporarly,  i've already shared the details in the below link.
3. Try the sqoop now, if the issue fixed then work with your admin and increase it permanently 
 
----------------------------------------------------------------------------------------------
impala can not properly handle .csv format. We have to use hive instead of 
--------------------------------------------------------------------------------------------------
I have a .txt file which is zipped in .gz format.
I want to load the data from .txt file to hive table.
 
The .txt file is around 432Gb, which i cant upload.
But after zip it is now 26Gb, I can upload to hue.
-----------------------------------------------------------------------------
When i was trying to see the data under my table, it is throwing Analysis exception.I tried changing the ip address with  hostname as suggetsed but it did not work. 
When i tried to open the tables and see the data in metastor manager in that also it is shwing error.
ans : its resolved using hostname in the query. 
------------------------------------------------------------------------------
All,
Working on importing data from DB2 using sqoop import, it worked fine for the most part except one table, which seemed to have some special characters ( control-M = ^M ) in contents, hence while sqooping, these characters are treated as newline and hence everything after it will be on the next line in the imported files, which will affect all the records after one bad record.
I am unable to guess how to fix the imports? is there any easy way?
ans :
If your business allows to replace Ctrl+M with something else then I would suggest two steps
 
1. Understand the regexp_replace function
ex: regexp_replace(col2,  '<the char that you want to replce>', '')
 
2. Use --query option instead of --table option in sqoop
 
So you have to use the following method to replace Ctrl+M with something else in your sqoop script
--query "select col1, regexp_replace(col2,  '<the char that you want to replce>', '') from db.table"
----------------------------------------------------------------------------------
 
How many number of MAPPER and Reducer will run when when select count(*) from table ??

Number of Mappers depends on the number of input splits calculated by the job client.
If you write a simple query like select Count(*) from company only one Map reduce Program will be executed.
So, in short mappers are decided by HDFS and reducers can be customized.
---------------------------------------------------------------------------------------
STACK OVERFLOW
I am migrating from Impala to SparkSQL, using the following code to read a table:

my_data = sqlContext.read.parquet('hdfs://my_hdfs_path/my_db.db/my_table')
How do I invoke SparkSQL above, so it can return something like:

'select col_A, col_B from my_table'

aNS::Pyspark.sql import SQLContext
Df = sqlContext.read.parquet(:””)
Df.select(“id”,”name”).show()
SqlContext.registerDataFrameAsTable(df,”table1”)
sqlContext.sql(“select * from table1”).show()
--------------------------------------------------------------------------------------------
Hive : Optimize a long running Query
ans ::

A simple Hive SQL query run on a 50GB size employee log table is running for hours.

select dept,count(distinct emp_id) from emp_log group by dept;    
There are just 4-5 departments and a huge number of employees per department.

It was run with Hive 0.14 + Tez on 1TB memory. Is there any way to optimize this code block for better performance?
ans:::

You should try that to avoid count(distinct foo) :

SELECT dept, size(collect_list(emp_id)) nb_emps
FROM emp_log 
GROUP BY dept
count(distinct x) is ineffective in HIVE 0.14.

Also you should activate statistics for these columns:

ANALYZE TABLE emp_log COMPUTE STATISTICS;
ANALYZE TABLE emp_log COMPUTE STATISTICS FOR COLUMNS dept, emp_id;
---------------------------------------------------------------------------------------------
How to save DataFrame directly to Hive?
Ans:: 
df.select(df.col("col1"),df.col("col2"), df.col("col3")) .write().mode("overwrite").saveAsTable("schemaName.tableName");
or
df.write().mode(SaveMode.Overwrite).saveAsTable("dbName.tableName");
---------------------------------------------------------------------------------------
Save Spark dataframe as dynamic partitioned table in Hive

I have a sample application working to read from csv files into a dataframe. The dataframe can be stored to a Hive table in parquet format using the method  df.saveAsTable(tablename,mode).
The above code works fine, but I have so much data for each day that i want to dynamic partition the hive table based on the creationdate(column in the table).

is there any way to dynamic partition the dataframe and store it to hive warehouse. Want to refrain from Hard-coding the insert statement using hivesqlcontext.sql(insert into table partittioin by(date)....).

Question can be considered as an extension to :How to save DataFrame directly to Hive?

ans :::df is a dataframe with year, month and other columns

df.write.partitionBy('year', 'month').saveAsTable(...)
or

df.write.partitionBy('year', 'month').insertInto(...)

--------------------------------------------------------------------------------------------------------------------------
Find maximum element in an RDD in Pyspark by using map/filter

a = sc.parallelize((1,9,3,10))
I want to find the maximum element in a without using any max function.

I tried a.filter( lambda x,y: x if x>y else y)

I am not able to compare elements in the RDD. How do I use for loop or if else condition properly in the map/filter function. Is it possible?

Thank you.

I was trying to post a different question. But not able to.

a = sc.parallelize((11,7,20,10,1,7))
I want to sort the elements in increasing order without using sort() function.

I tried:

def srt(a,b):
if a>b:
    i=a
    a=b
    b=i   

final=a.map(lambda x,y: srt(x,y))
I am not getting the required result.

I want to get

  (1,7,7,10,11,20)
thank you.

ANSWER 👍 

1
down vote
accepted
You cannot find the max/min using filters. You may achieve that using comparison in a reduce operation:

a = sc.parallelize([1,9,3,10])
max_val = a.reduce(lambda a, b: a if a > b else b)
The lambda just compares and returns the bigger of 2 values.
------------------------------------------------------------------------------------
how to increase java heap size in Hadoop


3
down vote
accepted
For that you may execute the following before executing hadoop command:

export HADOOP_HEAPSIZE=4096
Alternatively, you can achieve the same thing by adding the following permanent setting in your mapred-site.xml file, this file lies in HADOOP_HOME/conf/ :

<property>
    <name>mapred.child.java.opts</name>
    <value>-Xmx4096m</value>
</property>