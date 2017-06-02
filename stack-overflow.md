Sqoop error while importing to hdfs
Q1:13/12/04 02:05:39 ERROR 
security.UserGroupInformation:PriviledgedActionException  as:hadoop      
(auth:SIMPLE) 
cause:java.io.FileNotFoundException:
Ans : permissions,
-------------------------------------------------------------------------------------------------------------------------
2014-06-16 07:43:24,308 INFO  [main] manager.MySQLManager: Preparing to use a MySQL streaming resultset.
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
[root@localhost edureka]# sqoop import --connect jdbc:mysql://192.168.56.1/Edureka --table Employee --username root -P --target-dir /sqoopOut1 -m 1;

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

