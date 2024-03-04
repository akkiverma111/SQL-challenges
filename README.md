# SQL-challenges

Write an SQL query 𝐭𝐨 𝐝𝐢𝐬𝐩𝐥𝐚𝐲 𝐭𝐡𝐞 𝐝𝐞𝐩𝐭 𝐰𝐡𝐢𝐜𝐡 𝐡𝐚𝐬 𝐭𝐡𝐞 𝐨𝐯𝐞𝐫𝐚𝐥𝐥 𝐦𝐢𝐧𝐢𝐦𝐮𝐦 𝐭𝐱𝐧𝐚𝐦𝐨𝐮𝐧𝐭 𝐚𝐧𝐝 𝐭𝐡𝐞 𝐝𝐞𝐩𝐭 𝐰𝐡𝐢𝐜𝐡 𝐡𝐚𝐬 𝐭𝐡𝐞 𝐨𝐯𝐞𝐫𝐚𝐥𝐥 𝐦𝐚𝐱𝐢𝐦𝐮𝐦 𝐭𝐫𝐚𝐧𝐬𝐚𝐜𝐭𝐢𝐨𝐧 𝐚𝐦𝐨𝐮𝐧𝐭.

𝐓𝐚𝐛𝐥𝐞 𝐒𝐜𝐫𝐢𝐩𝐭:
create table ecommerce(dept varchar(50),txnmonth varchar(50),txnamount int);
insert into ecommerce values('Electronics','Jan',1000);
insert into ecommerce values('Electronics','Feb',2000);
insert into ecommerce values('Electronics','Mar',2500);
insert into ecommerce values('Textile','Jan',1000);
insert into ecommerce values('Textile','Feb',2000);
insert into ecommerce values('Textile','Mar',1500);
insert into ecommerce values('Sports','Jan',600);
insert into ecommerce values('Sports','Feb',200);
insert into ecommerce values('Sports','Mar',500);

Solution -1 
select * from ecommerce ;
select  
(select dept from ecommerce where txnamount = (select min(txnamount) from ecommerce)) as a
,
(select dept from ecommerce where txnamount = (select max(txnamount) from ecommerce)) as b;

 Solution -2 
SELECT
  (SELECT dept FROM ecommerce WHERE txnamount = (SELECT MIN(txnamount) FROM ecommerce)) AS min_txnamt_dept,
  (SELECT dept FROM ecommerce WHERE txnamount = (SELECT MAX(txnamount) FROM ecommerce)) AS max_txnamt_dept;

