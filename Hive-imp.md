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