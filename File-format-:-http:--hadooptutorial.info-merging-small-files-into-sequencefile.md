http://hadooptutorial.info/merging-small-files-into-sequencefile/

File format :

Text File
Sequence file
RCFile
ORCFILE
avro file	



SEQUENCEFILE
We know that Hadoop’s performance is drawn out when we work with a small number of files with big size rather than a large number of files with small size. If the size of a file is smaller than the typical block size in Hadoop, we consider it as a small file. Due to this, a number of metadata increases which will become an overhead to the NameNode. To solve this problem sequence files are introduced in Hadoop. Sequence files act as a container to store the small files.
Sequence files are in the binary format which are able to split and the main use of these files is to club two or more smaller files and make them as a one sequence file.

There are three types of sequence files:
• Uncompressed key/value records.
• Record compressed key/value records – only ‘values’ are compressed here
• Block compressed key/value records – both keys and values are collected in ‘blocks’ separately and compressed. The size of the ‘block’ is configurable.
• sequence file store data in binary format.
•set hive.exec.compress.output = true;
•set mapred.output.compression = true;
set mapred.output.compression.codec= org.apache.hadoop.compress.snappyCodec ;
Due to complexity of reading sequence files, they are often only used for "in flight" data such as imtermediate storage used with a sequence of mapreduce jobs. 




RCFILE
RCFILE stands of Record Columnar File which is another type of binary file format which offers high compression rate on the top of the rows.
RCFILE is used when we want to perform operations on multiple rows at a time.
RCFILEs are flat files consisting of binary key/value pairs, which shares much similarity with SEQUENCEFILE. RCFILE stores columns of a table in form of record in a columnar manner. It first partitions rows horizontally into row splits and then it vertically partitions each row split in a columnar way. RCFILE first stores the metadata of a row split, as the key part of a record, and all the data of a row split as the value part. This means that RCFILE encourages column oriented storage rather than row oriented storage.
This column oriented storage is very useful while performing analytics. It is easy to perform analytics when we “hive’ a column oriented storage type.
Facebook uses RCFILE as its default file format for storing of data in their data warehouse as they perform different types of analytics using Hive.

Creating RCFILE

1
create table olympic_rcfile(athelete STRING,age INT,country STRING,year STRING,closing STRING,sport STRING,gold INT,silver INT,bronze INT,total INT) row format delimited fields terminated by '\t' stored as rcfile

We cannot load data into RCFILE directly. First we need to load data into another table and then we need to overwrite it into our newly created RCFILE as shown below:

ORCFILE

ORC stands for Optimized Row Columnar which means it can store data in an optimized way than the other file formats. ORC reduces the size of the original data up to 75%. As a result the speed of data processing also increases. ORC shows better performance than Text, Sequence and RC file formats.
An ORC file contains rows data in groups called as Stripes along with a file footer. ORC format improves the performance when Hive is processing the data.

13. What is Partition and Combiner in MapReduce?

Partition and combiner are the two phase of a MapReduce operation those are executed before the reduce phase and after the map phase. Here are the details of partition and combiner in MapReduce.

Combiner: Combiner works like a mini reducer in Map phase which takes the input from map phase. It performs local reduce function on mapper result before they are distributed further. Once combiner functionality is executed (if required) then the output is passed to the reducer phase.

Partition: Partition comes into picture when you are using more than one reducer. Partition decides which reducer is responsible for a particular key.

It takes the input from mapper phase or Combiner phase (if used) and then sends it across the responsible reducer based on the key. The number of partitions is equal to the number of reducers.

So in partition and combiner, combiner comes first and then partition. The below image from Yahoo depicts the operation beautifully.

there r three types of xml file available :
mapred-site.xml
core-site.xml
hdfs-site.xml
---------------------------------------------------------------------------------------------------
orc file format :: optimized row column format 
diffenect formats for different columns according to the requirement
------------------------------------------------------------------------------------------------
summit :: avro, orc, sequence, textfile

parquet : 
Schema integrated with footer
column major format with strips
All the data pushed to leave of the tree
integrated compression and indexes
