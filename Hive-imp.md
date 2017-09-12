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
----------------------------------------------------------------
select e.empno, e.ename, e.deptno ,d.dname,d.location from emp e,dept d where e.deptno = d.deptno order by e.deptno;
select empno,deptno,sal, FIRST_VALUE(sal IGNORE NULLS)over(partition by deptno)ratnesh from emp;

7782	10	2450	2450
7934	10	1300	2450
7839	10	5000	2450
7566	20	2975	2975
7369	20	800	2975
7788	20	3000	2975
7876	20	1100	2975
7902	20	3000	2975
7844	30	1500	1500
7654	30	1250	1500
7521	30	1250	1500
-----------------------------------------------------------------------------------------------
select deptno, sal, avg(sal) over(PARTITION BY deptno order by sal) as name from emp;

10	1300	1300
10	2450	1875
10	5000	2916.666666666666666666666666666666666667
20	800	800
20	1100	950
20	2975	1625
20	3000	2175
20	3000	2175
30	950	950
30	1250	1150
30	1250	1150
30	1500	1237.5
30	2850	1560
-------------------------------------------------------------------------------------------------
select empno, deptno, sal ,lag(sal,2,0) over(order by sal) sal_prev from emp; 

7369	20	800	0
7900	30	950	0
7876	20	1100	800
7654	30	1250	950
7521	30	1250	1100
7934	10	1300	1250
7844	30	1500	1250
7782	10	2450	1300
-------------------------------------------------------------------------------------------------
select empno, deptno, sal ,lag(sal,1,0) over(order by sal) sal_prev, sal -lag(sal,1,0)over(order by sal) diff from emp; 

7369	20	800	0	800
7900	30	950	800	150
7876	20	1100	950	150
7654	30	1250	1100	150
7521	30	1250	1250	0
7934	10	1300	1250	50
7844	30	1500	1300	200
7782	10	2450	1500	950
--------------------------------------------------------------------------------------------------
select empno, deptno, sal ,lead(sal,2,12) over(order by sal) sal_prev from emp; 

7782	10	2450	2975
7698	30	2850	3000
7566	20	2975	3000
7902	20	3000	5000
7788	20	3000	12
7839	10	5000	12
-----------------------------------------------------------------------
select empno , deptno, sal , rank() over( partition by deptno  order by sal) rank from emp;
7934	10	1300	1
7782	10	2450	2
7839	10	5000	3
7369	20	800	1
7876	20	1100	2
7566	20	2975	3
7902	20	3000	4
7788	20	3000	4
7900	30	950	1
7521	30	1250	2
----------------------------------------------------------------------------------------
select empno , deptno, sal , dense_rank() over( partition by deptno  order by sal) rank from emp;

7369	20	800	1
7876	20	1100	2
7566	20	2975	3
7902	20	3000	4
7788	20	3000	4
7900	30	950	1
7521	30	1250	2
7654	30	1250	2
7844	30	1500	3
7698	30	2850	4
-------------------------------------------------------------------------
with ordered_query as (select empno,deptno,ename,sal,mgr,hiredate from emp) select empno from ordered_query;
-----------------------------------------------------------------------------------------------


