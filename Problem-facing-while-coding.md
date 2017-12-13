Map reduce program: --
1.it is map and reduce in small letter.
2.hasnext will be with values. 
3,tool & Toolrunner are throwing warning 'The type Tool is deprecated'(Solution: add in code @SuppressWarnings("deprecation")
)
4.java.lang.UnsupportedClassVersionError: MapReduce/DriverCode : Unsupported major.minor version 52.0(solution :This is because of a higher JDK during compile time and lower JDK during runtime. So you just need to update your JDK version, possible to JDK 7)


1. This command is used to change the replication factor of a file to a specific instead of the default of replication factor for the remaining in HDFS.

If <path> is a directory then the command recursively changes the replication factor of all files under the directory tree rooted at <path>.

1.The type Joinmap.Table1 must implement the inherited abstract method Mapper<LongWritable,Text,IntWritable,Text>.map(LongWritable, 
 Text, OutputCollector<IntWritable,Text>, Reporter)

Caused by: java.lang.ClassCastException: cannot assign instance of scala.collection.immutable.List$SerializationProxy to field org.apache.spark.rdd.RDD.org$apache$spark$rdd$RDD$$dependencies_ of type scala.collection.Seq in instance of org.apache.spark.rdd.MapPartitionsRDD
I get the error above when I use dataset.map(). Why?
Ans  ::no
Can I run this somehow: combPrdGrp3.repartition(10).saveAsTextFile("Combined") and save it as gzip files?
ans ::
combPrdGrp3.repartition(10).saveAsTextFile("Combined", classOf[GzipCodec])
 hive -------------------------------------------
https://www.cloudera.com/documentation/cdh/5-0-x/CDH5-Release-Notes/cdh5rn_hive_ki.html
1.invalidate metadata 
2.compute stats
3. you can nt load directly csv file to parquet/orc/rc format.
4. https://github.com/prestodb/presto/issues/1848  /// skip.header.line.count is an issue.
5. implement timestamp support in Parquet SerDe. // https://issues.apache.org/jira/browse/HIVE-6394 -- use unix_timestamp
6. Hive creates an invalid table if you specify more than one partition with alter table.https://www.cloudera.com/documentation/cdh/5-0-x/CDH5-Release-Notes/cdh5rn_hive_ki.html
ex.
ALTER TABLE page_view ADD PARTITION (dt='2008-08-08', country='us') location '/path/to/us/part080808' PARTITION
(dt='2008-08-09', country='us') location '/path/to/us/part080809';
should be replaced with:
ALTER TABLE page_view ADD PARTITION (dt='2008-08-08', country='us') location '/path/to/us/part080808';
ALTER TABLE page_view ADD PARTITION (dt='2008-08-09', country='us') location '/path/to/us/part080809';





