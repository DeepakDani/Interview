Create a directory in HDFS at given path(s).
hadoop fs -mkdir <paths>

List the contents of a directory.
hadoop fs -ls /user/saurzcode
hadoop fs -put /home/saurzcode/Samplefile.txt  /user/saurzcode/dir3/

Copies/Downloads files to the local file system
hadoop fs -get /user/saurzcode/dir3/Samplefile.txt /home/
hadoop fs -cat /user/saurzcode/dir1/abc.txt