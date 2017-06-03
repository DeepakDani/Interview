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

