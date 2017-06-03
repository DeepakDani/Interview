1. Write a mapreduce to find maximum dep salary Wordcount program and explanation in mapreduce .
	
1. Hadoop Developer at Infosys was asked...	8 Aug 2015
1. What is RDD (spark) What r the problem with In u place How do u use global sort in hive and partitioning logics Diff between bucketing and partitioning When will u use this.. Syntax for bucking and partitioning
1. --->1. How hadoop works?
 2. How Mapreduce works ?
 3. How file of 100MB will be stored in Hadoop 
4. How I will update data in hive files 
5. How to read csv file of 10 gb and store it in database as it is within few seconds.
1. hashset and hash map diffrence.
1. how we can remove reduce part??
1. how more than one files can be access in mapreduce ?
1. how to strt all services?
1. what is xml files?
hadoop tasktracker &

1. If you are using Hadoop 2.2.0 which has YARN framework, there is no jobtracker in it. Its functionality is split and replaced by ResourceManager and ApplicationMaster. Here is expected jps prinout while running YARN1. 

Q.
1. Why does Hadoop need classes like Text or IntWritable instead of String or Integer?
In order to handle the Objects in Hadoop way. For example, hadoop uses Text instead of java's String. The Text class in hadoop is similar to a java String, however, Text implements interfaces like Comparable, Writable and WritableComparable.

1. These interfaces are all necessary for MapReduce; the Comparable interface is used for comparing when the reducer sorts the keys, and Writable can write the result to the local disk. It does not use the java Serializable because java Serializable is too big or too heavy for hadoop, Writable can serializable the hadoop Object in a very light way.

-->For effectiveness of Hadoop, the serialization/de-serialization process should be optimized because huge number of remote calls happen between the nodes in the cluster. So the serialization format should be fast, compact, extensible and interoperable. Due to this reason, Hadoop framework has come up with one IO classes to replace java primitive data types. e.g. IntWritbale for int, LongWritable for long, Text for String etc.


1. Below parameter points to default hive table location.It can be used for dev purpose, where you just want to perform some tests on internal tables.

--warehouse-dir
1. Below parameter points to some hdfs location, where you can mount external hive tables.This is useful in production environment, where you want every data to be available to some external dir and external table.


---In my last article I have explained how we can use - -target-dir to import data in particular directory. But the limitation of target-dir is that the given directory which we will pass it to the argument must not create earlier. If this directory already created then an error will be thrown by the SQOOP Tool.

But when we pass particular directory with –warehouse-dir it will treat directory as parent directory and create sub directory inside the parent directory with the name of table name.

The SerDe interface allows you to instruct Hive as to how a record should be processed. A SerDe is a combination of a Serializer and a Deserializer (hence, Ser-De). The Deserializer interface takes a string or binary representation of a record, and translates it into a Java object that Hive can manipulate. The Serializer, however, will take a Java object that Hive has been working with, and turn it into something that Hive can write to HDFS or another supported system. Commonly, Deserializers are used at query time to execute SELECT statements, and Serializers are used when writing data, such as through an INSERT-SELECT statement.

http://www.hdfstutorial.com/blog/hadoop-scenario-based-interview-questions/
1.What are the differences between -copyFromLocal and -put command?
2.What is the default block size in Hadoop and can it be increased?
ans: The default block size in Hadoop 1 is 64 MB while in Hadoop 2, it is 128MB.
you can do it by setting fs.local.block.size in the configuration file easily. 

3.How to import RDBMS table in Hadoop using Sqoop when the table doesn’t have a primary key column?
ans: –split-by or perform a sequential import with ‘-m 1’

4.What is CBO in Hive?
ans:  CBO is cost-based optimization and applies to any database or any tool where optimization can be used.
5.Can we use LIKE operator in Hive?
WHERE table2.product LIKE concat(‘%’, table1.brand, ‘%’);
6.Can you use IN/EXIST operator in Hive?
No, Hive doesn’t support IN or EXIST operators. Instead, you can use left semi join here. Left Semi Join performs the same operation IN do in SQL.

So if you have the below query in SQL-

SELECT a.key, a.value
FROM a
WHERE a.key in
(SELECT b.key
FROM B);
7. how to open configuraration file in hive?
8.yes we can change location of internal table from  /user/hive/warehouse to some other location 
by changing location in configuration file.
9. When to use external and internal tables in Hive?

Use EXTERNAL tables when:

The data is also used outside of Hive. For example, the data files are read and processed by an existing program that doesn’t lock the files.
Data needs to remain in the underlying location even after a DROP TABLE. This can apply if you are pointing multiple schemas (tables or views) at a single data set or if you are iterating through various possible schemas.
Hive should not own data and control settings, dirs, etc., you may have another program or process that will do those things.
You are not creating a table based on existing table (AS SELECT).
Use INTERNAL tables when:

The data is temporary
You want Hive to completely manage the life cycle of the table and data
10.We have a Hive partitioned table with partition column as country. We have 10 partition and data for now is jut for one country, If we will copy the data manually for other 9 partitions, whether those will be reflected if we will run a command.
Ans: This is really a good question. As the data has been kept manually in all the other file directory and so directly it won’t be available.

11.Data will be available directly for all partition when you will put it through command and not manually.
 Where the Mapper’s Intermediate data will be stored?

Ans: The mapper output (which is intermediate data) is stored on the Local file system (not in HDFS) of each mapper nodes. This is a temporary directory location which can be setup in the configuration file by the Hadoop administrator. The intermediate data is cleaned up after the Hadoop Job completes.
------------------------------------------------------------------------------------------------------------------

can we handle xml file with mapreduce?
can u expain about couter in mapreduce?


