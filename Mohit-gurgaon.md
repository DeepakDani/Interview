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
