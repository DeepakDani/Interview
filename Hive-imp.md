hive :

-d,-- Variable substitution to apply to Hive
                                  commands. e.g. -d A=B or --define A=B

 -e --SQL from command line
 -f-- SQL from files
-H--   Print help information
 -i--Initialization SQL file
 -S-Silent mode in interactive shell
 -v--Verbose mode (echo executed SQL to the
                                  console)


$HIVE_HOME/bin/hive -e 'select a.col from tab1 a'

$HIVE_HOME/bin/hive -S -e 'select a.col from tab1 a' > a.txt


$HIVE_HOME/bin/hive -i /home/my/hive-init.sql

--------------------------------------------------------
http://hadooptutorial.info/merging-small-files-into-avro-file/
http://hadooptutorial.info/merging-small-files-into-sequencefile/
https://community.hortonworks.com/questions/25190/load-multiple-json-file-to-hive-table.html


understand that the fsimage is loaded into the memory on startup and any further transactions are added to the edit log rather than to the fsimage for performance reasons.
The fsimage in memory gets refreshed when the namenode is restarted. For efficiency, secondary name node periodically does a checkpoint to update the fsimage so that the namenode recovery is faster. All these are fine