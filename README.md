# Constraint-SQL
Constraint/SQL


-- Constraint

drop table snapdeal_orders;

create table snapdeal_orders
(
order_Id int not null, -- now we can not add null value in column order_id , not null constraint
order_date date, -- "yyyy-mm-dd" is standard format
product_name varchar(50),
total decimal(10,2),
payment_method varchar(30) check (payment_method in ('UPI','card')),-- no value is accepted other then 'UPI','card'), 
discount INT CHECK (discount <= 20)  
); 

select * from snapdeal_orders

insert into snapdeal_orders values (null,'2022-04-05 12:05:57','Froak',4000,'card'); -- now this will give error

-- in payment method i accept payment "UPI" and "Card"
insert into snapdeal_orders values (1,'2022-04-05 12:05:57','Froak',4000,'cash') -- cash can not be mention here

insert into snapdeal_orders values (1,'2022-04-05 12:05:57','Froak',4000,'card',5); -- cash can not be mention here

-- we will start from video - 2 (minute = 55)
