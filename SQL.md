How will you go about identifying duplicate records in a table?/SQL query to delete duplicate rows

Method 1)
with table1 as(select no,name, amount, row_number() over(partition by no,name,amount order by no,name,amount)  git from RATNESH1) select no,name,amount from table1 where git >1;

Method 2)
       select distinct * into #tmp From EmpDup
       delete from EmpDup
       insert into EmpDup                
       select * from #tmp drop table #tmp
	
       select * from EmpDup
    
