diffrence between fs and dfs ?

fs refers to any file system, it could be local or HDFS but dfs refers to only HDFS file system. So if you need to perform access/transfer data between different filesystem, fs is the way to go.
to check where files has stored ?
hadoop fsck / -files -blocks -locations

update query in hive :::
select e.EMPLOYEE_ID,e.FIRST_NAME,e.LAST_NAME,e.EMAIL,e.PHONE_NUMBER,e.HIRE_DATE,e.JOB_ID,e.SALARY,e.COMMISSION_PCT,e.MANAGER_ID,e.DEPARTMENT_ID from employees e left outer join employee e1 
on (e.employee_id = e1.employee_id) where e1.employee_id is  null
union
select e1.EMPLOYEE_ID,e1.FIRST_NAME,e1.LAST_NAME,e1.EMAIL,e1.PHONE_NUMBER,e1.HIRE_DATE,e1.JOB_ID,e1.SALARY,e1.COMMISSION_PCT,e1.MANAGER_ID,e1.DEPARTMENT_ID from employees e left outer join employee e1 
on (e.employee_id = e1.employee_id) where e1.employee_id is not  null;
------------------------------------------------------------------------------------------
insert and update concept in hive before 0.14 
truncate table empone;
   
 insert into empone  select e.EMPLOYEE_ID,      
                              e.FIRST_NAME ,      
                              e.LAST_NAME   ,     
                              e.EMAIL        ,    
                              e.PHONE_NUMBER  ,   
                              e.HIRE_DATE      ,  
                              e.JOB_ID          , 
                              e.SALARY           ,
                              e.COMMISSION_PCT   ,
                              e.MANAGER_ID       ,
                              e.DEPARTMENT_ID    ,
                              case when t.employee_id is null then 'I' else 'U' end from employee e left outer join emptwo t on( e.employee_id=t.employee_id);

commit;

create table upd_emp  as select e.EMPLOYEE_ID,e.FIRST_NAME,e.LAST_NAME,e.EMAIL,e.PHONE_NUMBER,e.HIRE_DATE,e.JOB_ID,e.SALARY,e.COMMISSION_PCT,e.MANAGER_ID,e.DEPARTMENT_ID,e.flag from emptwo e left outer join empone e1 on (e.employee_id = e1.employee_id) where e1.employee_id is null
 union
select e1.EMPLOYEE_ID,e1.FIRST_NAME,e1.LAST_NAME,e1.EMAIL,e1.PHONE_NUMBER,e1.HIRE_DATE,e1.JOB_ID,e1.SALARY,e1.COMMISSION_PCT,e1.MANAGER_ID,e1.DEPARTMENT_ID,e1.flag from emptwo e left outer join empone e1 on (e.employee_id = e1.employee_id) where e1.employee_id is not null;
commit;

create table ins_emp as select e.EMPLOYEE_ID,e.FIRST_NAME,e.LAST_NAME,e.EMAIL,e.PHONE_NUMBER,e.HIRE_DATE,e.JOB_ID,e.SALARY,e.COMMISSION_PCT,e.MANAGER_ID,e.DEPARTMENT_ID,e.flag from empone e left outer join emptwo e1 on( e.employee_id = e1.employee_id) where e1.employee_id is null;
commit;

truncate table emptwo;
commit;

insert into emptwo select * from ins_emp union select * from upd_emp;
commit;

drop table  upd_emp;
drop table  ins_emp;
select * from emptwo;
---------------------------------------------------------------------------------------------------------------------
Query to fetch latest record from table 

select e.employee_id,e.department_id, e.salary from employees e1  join
 (select department_id,  max(salary) sal from employees group by department_id) tm
  on (e1.department_id = tm.department_id and e1.salary = tm.sal) order by e1.department_id; 
--------------------------------------------------------------------------------------------------------------
query to delete duplicates
select distinct *  from ratnesh1_bkp;
with abc as (select rat_sk, no, name, amount ,row_number() over(partition by rat_sk, no, name, amount order by rat_sk, no, name, amount) col from ratnesh1_bkp) select no, name, amount,col from abc where col = 1; 

------------------------------------------------------------------------------------------------------------
http://www.folkstalk.com/2011/12/sql-queries-interview-questions-oracle.html
SQL Queries Interview Questions - Oracle Part 1

1. Write a SQL query to find the products which have continuous increase in sales every year?
select product_id,(quantity - name) as name1  from (select product_id, quantity, lead(quantity,1,0) over(partition by product_id order by product_id) as name from sales) where (quantity - name) >=0;

2. Write a SQL query to find the products which does not have sales at all?
select p.product_id, p.product_name from products p left outer join sales s on (p.product_id = s.product_id ) where s.product_id is null

3. Write a SQL query to find the products whose sales decreased in 2012 compared to 2011?
select p.product_id,p.product_name from products p ,(select product_id from (select product_id,quantity,lag(quantity,1,0) over(partition by product_id order by product_id) as back from sales where year in (2011, 2012)) where (quantity - back) < 0)b where p.product_id = b.product_id;