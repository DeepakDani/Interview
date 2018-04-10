How will you go about identifying duplicate records in a table?/SQL query to delete duplicate rows

Method 1)
with table1 as(select no,name, amount, row_number() over(partition by no,name,amount order by no,name,amount)  git from RATNESH1) select no,name,amount from table1 where git >1;

Method 2)
       select distinct * into #tmp From EmpDup
       delete from EmpDup
       insert into EmpDup                
       select * from #tmp drop table #tmp
	
       select * from EmpDup
    

Oracle 2 folktalk


---2)  Write a query to compare the products sales of "IPhone" and "Samsung" in each year?
 
select b.product_name,a.product_name,a.year, a.quant_iphone,b.quant_samsung, a.iphone_price,b.samsung_price from 
(select p.product_name,s.year,s.quantity as quant_iphone,s.price as  iphone_price from sales s,products p where p.product_name in ('IPhone')  and s.product_id = p.product_id) a,
(select p.product_name,s.year,s.quantity as quant_samsung,s.price as samsung_price from sales s,products p where p.product_name in ('Samsung')  and s.product_id = p.product_id) b 
where a.year = b.year;

3) --In the SALES table quantity of each product is stored in rows for every year. Now write a query to transpose the quantity for each product and display it in columns? The output should look like as 

select * from PRODUCTS;
select * from  SALES;
method 1)

 select product_name, Quan_2010, Quan_2011, Quan_2012 from
 (select s2010.product_id,s2010.quantity as Quan_2010, s2011.quantity as Quan_2011,s2012.quantity as Quan_2012 from sales s2010,sales s2011, sales s2012
 where s2010.product_id = s2011.product_id and s2011.product_id = s2012.product_id and s2010.year = 2010 and s2011.year = 2011 and s2012.year = 2012) a,products p where a.product_id = p.product_id order by p.product_name ;

method 2)
 
 select p.product_name,max(decode(s.year,2010,s.Quantity,0)) as q1,
 max(decode(s.year,2011,s.Quantity,0)) as q2,
 max(decode(s.year,2012,s.Quantity,0)) as q3
 from sales s,products p where s.product_id = p.product_id group by p.product_name;
 
---4) Write a query to find the number of products sold in each year?

select year,count(1) num_products from sales group by year;

--------------------------------------------------------------------------------------------------------------------------
SQL Query Interview Questions - Part 5
1. Load the below products table into the target table.

The requirements for loading the target table are:
Select only 2 products randomly.
Do not select the products which are already loaded in the target table with in the last 30 days.
Target table should always contain the products loaded in 30 days. It should not contain the products which are loaded prior to 30 days.

ANS :+1: 

INSERT INTO tgt_products select a.product_id,a.product_name,TO_DATE(sysdate, 'YYYY-MON-DD') from (select * from (select * from products order by dbms_random.value ) where rownum <=2)a 
 left outer join tgt_products t 
 on (a.product_id = t.product_id)
 where t.product_id is null or (to_date(sysdate, 'YYYY-MON-DD') - TO_DATE(t.insert_date, 'DD-MON-YY')) > 30;