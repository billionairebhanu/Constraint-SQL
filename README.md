# Constraint-SQL
Constraint/SQL


-- Constraint
-- null constraint -- (value could not be null)
-- unique constraint -- (value could not repeat itself)
-- check constraint -- (will not accept any random value)
-- default constraint -- (if no value given, it will take default value)
-- parimary key constraint -- (value can not be null and cannot repeat)

-- in unique constraint we can have one null value but in parimary key, we can not have any null value

drop table snapdeal_orders;

create table snapdeal_orders
(
order_Id int not null unique, -- now we can not add null value in column order_id , not null constraint & unique constraint 
order_date date, -- "yyyy-mm-dd" is standard format
product_name varchar(50),
total decimal(10,2),
payment_method varchar(30) check (payment_method in ('UPI','card')) default 'card',-- no value is accepted other then 'UPI','card'), -- check constraint
discount INT CHECK (discount <= 20),
category varchar (25) default 'Pajama'
); 

select * from snapdeal_orders

insert into snapdeal_orders values (null,'2022-04-05 12:05:57','Froak',4000,'card',20,'kurta'); -- now this will give error,because order_Id can not be null

-- in payment method i accept payment "UPI" and "Card"
insert into snapdeal_orders values (2,'2022-04-05 12:05:57','Froak',4000,'cash',3,'underwear') -- cash can not be mention here, because of check constraint

insert into snapdeal_orders values (1,'2022-04-05 12:05:57','Froak',4000,'card',5,'blazer'); -- discount value has to be <=20

insert into snapdeal_orders values (1,'2022-04-05 12:05:57','Froak',4000,'card',5,'coat'); -- unique id can not repeat itself 


insert into snapdeal_orders (order_Id,order_date,product_name,total,payment_method,discount)
values (3,'2022-04-05 12:05:57','Froak',4000,'card',5); -- Default constraint

-- we can add value in any order 
insert into snapdeal_orders (order_Id,payment_method,product_name,discount)
values (3,'card','Froak',5); --  this will take pajama by default but other values will be null.


insert into snapdeal_orders (order_Id,order_date,product_name,total,discount)
values (4,'2022-04-05 12:05:57','Froak',4000,5); -- Default constraint


