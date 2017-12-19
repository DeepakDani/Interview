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
