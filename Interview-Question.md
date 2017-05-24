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


