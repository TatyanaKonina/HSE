# LAB-1
## Выполнили:
**19 ПИ - 2**
* ***Конина Татьяна*** 
* ***Ожиганова Полина***

№ 1. 
```sql
CREATE TABLE buyer (
id SERIAL PRIMARY KEY, -- индетификатор
surname text NOT NULL, -- фамилия (строка)
district text NOT NULL, -- район проживания(строка)
discount integer NOT NULL,CHECK (discount >=0) --скидка (не может быть больше 0)
);

CREATE TABLE shop (
id SERIAL PRIMARY KEY, -- индетификатор
name text NOT NULL, --
district text NOT NULL,
commission_fees integer NOT NULL, CHECK(commission_fees >= 0)
);

CREATE TABLE books (
id SERIAL PRIMARY KEY, -- индетификатор
title text NOT NULL,
price integer NOT NULL, CHECK(price >= 0),
repo text NOT NULL,
quantity integer NOT NULL,CHECK(quantity >= 0)
);

CREATE TABLE purchase (
order_number SERIAL PRIMARY KEY,
month text NOT NULL,
seller integer NOT NULL,CHECK (seller >=0),
buyer integer NOT NULL,CHECK (buyer >=0),
book integer NOT NULL,CHECK (book >= 0),
quantity integer NOT NULL,CHECK (quantity >=0),
price integer NOT NULL
);
```
<p align="left">
  <img src="https://i.imgur.com/f1XVyvj.png" width="600">
</p>
<p align="left">
  <img src="https://i.imgur.com/zHfTRPt.png" width="600">
</p>

№ 2.

```sql
INSERT INTO buyer 
(id, surname, district ,discount) 
VALUES
(001, 'Сидоров' ,'Нижегородский',10),
(002,'Потапов','Советский',20),
(003,'Попов','Ленинский',10),
(004,'Романова','Нижегородский',10),
(005,'Миронов','Автозаводский',15),
(006,'Попов','Советский',0);
```
<p align="left">
  <img src="https://i.imgur.com/PCfIioC.png" width="600">
</p>

```sql
INSERT INTO shop 
(id, name,district, commission_fees) 
VALUES 
(001,'Знание','Автозаводский',7),
(002,'Наука','Нижегородский',8),
(003,'Книжный мир','Приокский',6),
(004,'Книги','Сормовский',9),
(005,'Книги','Советский',7)
```
<p align="left">
  <img src="https://i.imgur.com/XPQH5lr.png" width="600">
</p>

```sql
INSERT INTO books 
(id, title,price,repo,quantity) VALUES
(001,'Windows для чайников',15000,'Сормовский',400),
(002,'Excel 5.0',2300,'Сормовский',360),
(003,'Работа с Visual FoxPro',32000,'Нижегородский',300),
(004,'Программирование в среде Delphi',20000,'Нижегородский',100),
(005,'SQL',47000,'Автозаводский',89),
(006,'Word 6.0 для Windows',16000,'Сормовский',200),
(007,'Твой первый выход в Internet',15000,'Советский',140)
```
<p align="left">
  <img src="https://i.imgur.com/gbCV4yF.png" width="600">
</p>

```sql
INSERT INTO purchase (order_number,month,seller,buyer,book,quantity,price)
VALUES
(10011,'Январь',001,006,003,2,64000),
(10012, 'Январь',001,006,002,2,46000),
(10013,'Январь',005,005,004,4,80000),
(10014,'Февраль',001,003,003,3,96000),
(10015,'Февраль',004,006,002,1,23000),
(10016,'Март',001,004,007,2,30000),
(10017,'Март',005,006,006,3,48000),
(10018,'Апрель',001,001,003,3,96000),
(10019,'Апрель',003,003,007,2,30000),
(10020,'Апрель',005,002,002,5,115000),
(10021,'Апрель',005,002,001,3,45000),
(10022,'Май',002,003,007,2,30000),
(10023,'Май',002,004,003,1,32000),
(10024,'Май',004,003,005,1,47000),
(10025,'Май',004,006,003,4,60000),
(10026,'Май',005,001,005,3,80000),
(10027,'Июнь',003,002,006,2,32000)
```
<p align="left">
  <img src="https://i.imgur.com/3iSEk7U.png" width="600">
</p>

№ 3.

```sql
SELECT LPAD(id::text,3,'0') as id,surname,district,discount from buyer
```
<p align="left">
  <img src="https://i.imgur.com/fwisovu.png" width="600">
</p>

```sql
SELECT LPAD(id::text,3,'0') as id, name,district, commission_fees from shop
```
<p align="left">
  <img src="https://i.imgur.com/57FsCTO.png" width="600">
</p>

```sql
SELECT LPAD(id::text,3,'0') as id, title,price,repo,quantity from books
```

<p align="left">
  <img src="https://i.imgur.com/7GvvwIv.png" width="600">
</p>

```sql
SELECT order_number,month, LPAD(seller::text,3,'0') as seller, LPAD(buyer::text,3,'0') as buyer,
LPAD (book::text,3,'0') as book, quantity,price from purchase
```

<p align="left">
  <img src="https://i.imgur.com/JwmDY2A.png" width="600">
</p>

## или

<p align="left">
  <img src="https://i.imgur.com/diraYUM.png" width="600">
</p>

<p align="left">
  <img src="https://i.imgur.com/TMRfP6k.png" width="600">
</p>

<p align="left">
  <img src="https://imgur.com/A3ZNRBD.png" width="600">
</p>

<p align="left">
  <img src="https://imgur.com/bt08gIL.png" width="600">
</p>

№ 4.
a)
```sql
SELECT title, price
FROM books;
```
<p align="left">
  <img src="https://imgur.com/datu2uW.png" width="600">
</p>

b)
```sql
SELECT district
FROM buyer; 
```
<p align="left">
  <img src="https://imgur.com/jlRQpcQ.png" width="600">
</p>

c)
```sql
SELECT month
FROM purchase; 
```
<p align="left">
  <img src="https://imgur.com/XR6njm0.png" width="600">
</p>

№ 5.
a)
```sql
SELECT surname, discount
FROM buyer
WHERE district = 'Нижегородский';
```
<p align="left">
  <img src="https://imgur.com/YzAdsIq.png" width="600">
</p>

b)
```sql
SELECT name
FROM shop
WHERE district = 'Сормовский' or district = 'Советский';
```
<p align="left">
  <img src="https://imgur.com/VEnGUzF.png" width="600">
</p>

c)
```sql
SELECT title, price
FROM books
WHERE title LIKE '%Windows%' or price > 20000
ORDER BY  price DESC 
```
<p align="left">
  <img src="https://imgur.com/9U4winu.png" width="600">
</p>

№ 6.
a) Если нужно было вывести только название книги
```sql
SELECT distinct title,surname,name from buyer,shop,purchase,books
where buyer.id=purchase.buyer and purchase.seller=shop.id and purchase.book = books.id
```
<p align="left">
  <img src="https://imgur.com/wYr5Nbe.png" width="600">
</p>

b)
```sql
SELECT title,month,surname,discount,purchase.quantity as quantity from purchase,buyer,books
where purchase.buyer=buyer.id and books.id=purchase.book
```
<p align="left">
  <img src="https://imgur.com/LbXjDrc.png" width="600">
</p>

№ 7.
a)
```sql
SELECT order_number,surname,month from purchase,buyer
where purchase.price > 60000 and buyer.id = purchase.buyer
```
<p align="left">
  <img src="https://imgur.com/OJDSeSE.png" width="600">
</p>

b)
```sql
SELECT surname,month,shop.district as district from purchase,shop,buyer where
buyer.district = shop.district and purchase.buyer = buyer.id
and purchase.seller = shop.id
and (purchase.month ='Январь'
or purchase.month = 'Февраль'
or purchase.month = 'Март')
```
<p align="left">
  <img src="https://imgur.com/dPWOE6n.png" width="600">
</p>

c)
```sql
SELECT name
FROM purchase, shop, buyer
WHERE purchase.buyer = buyer.id
and purchase.seller = shop.id
and shop.district != 'Автозаводский' 
and buyer.discount BETWEEN 10 AND 15
```
<p align="left">
  <img src="https://imgur.com/tpceD2r.png" width="600">
</p>

d)
```sql
SELECT DISTINCT books.title, books.price, books.repo, purchase.quantity 
FROM books, purchase, shop
WHERE purchase.book = books.id  -- район складирования 
and purchase.seller = shop.id  -- район складирования 
and books.quantity > 10 
ORDER BY books.price ASC
```
<p align="left">
  <img src="https://imgur.com/DoKNgm3.png" width="600">
</p>

№ 8.
```sql
update purchase set price = purchase.price * (100 - buyer.discount)/100
from buyer where purchase.buyer = buyer.id;
SELECT order_number,month, LPAD(seller::text,3,'0') as seller, LPAD(buyer::text,3,'0') as buyer,
LPAD (book::text,3,'0') as book, quantity,price from purchase
```
<p align="left">
  <img src="https://imgur.com/HoKdgD2.png" width="600">
</p>

№ 9.
```sql
ALTER TABLE purchase ADD commission_fees integer CHECK (commission_fees >= 0);
UPDATE purchase SET commission_fees = (SELECT shop.commission_fees FROM shop WHERE shop.id = purchase.seller);
	
SELECT * FROM purchase  -- проверка
```
<p align="left">
  <img src="https://imgur.com/3yfES2C.png" width="600">
</p>

## Уровень 2.

№ 10.
a)
```sql
select * from buyer
where id not in (select buyer from purchase where month in ('Июнь'))
```
<p align="left">
  <img src="https://imgur.com/ebZsQlk.png" width="600">
</p>

b)
```sql

```

c) внимание!! тут результат отличается от 7а, так как мы в 8 поменяли последнюю колонку!!!!
```sql
SELECT distinct order_number, surname , month from purchase,buyer
where purchase.price > 60000 and surname in (select surname from buyer where buyer.id = purchase.buyer);
```
<p align="left">
  <img src="https://imgur.com/dASlhJ7.png" width="600">
</p>

№ 11.
a)
```sql
SELECT *
FROM buyer
WHERE discount = ALL (SELECT MIN(discount)
					  FROM buyer)
					  AND id IN (SELECT purchase.buyer
						   FROM purchase
					 	   WHERE purchase.buyer = buyer.id
						   AND purchase.price >= 50000)
```
<p align="left">
  <img src="https://imgur.com/YcguBvN.png" width="600">
</p>

b)
```sql
SELECT t.surname, max(t.amount) as Highest
   FROM (
    SELECT surname, SUM(quantity) amount
    from purchase, buyer	
	where purchase.buyer = ALL(select purchase.buyer
							   from purchase 
							   where purchase.buyer = buyer.id)
	group by surname, buyer.id
  )t
  group by t.surname
 order by Highest desc
 limit 1
```
<p align="left">
  <img src="https://imgur.com/wKBxNO2.png" width="600">
</p>

c)
```sql
SELECT surname, month, shop.district AS district 
FROM purchase,shop,buyer
WHERE buyer.district = ANY(SELECT district
			   FROM buyer
			   WHERE buyer.district = shop.district) 
AND purchase.buyer = buyer.id
AND purchase.seller = shop.id
AND purchase.month = ANY(SELECT month
			 FROM purchase
			 WHERE purchase.month ='Январь'
			 OR purchase.month = 'Февраль'
			 OR purchase.month = 'Март')
```
<p align="left">
  <img src="https://imgur.com/DNRQG2F.png" width="600">
</p>

d)
```sql
SELECT t.surname, MIN(t.sum1) AS Lowest
FROM
(SELECT surname, SUM(price * quantity) sum1
FROM  purchase, buyer, shop
WHERE purchase.buyer = ALL(SELECT purchase.buyer
			   FROM purchase 
			   WHERE purchase.buyer = buyer.id)
AND purchase.seller=shop.id
AND buyer.district != shop.district
GROUP BY surname, buyer.id )t, purchase, buyer
GROUP BY t.surname
ORDER BY Lowest ASC
LIMIT 1
```
<p align="left">
  <img src="https://imgur.com/bdAGXdO.png" width="600">
</p>

№ 12.
```sql
select district from buyer
union
select repo from books
```
<p align="left">
  <img src="https://imgur.com/gYh7qxg.png" width="600">
</p>

№ 13.
```sql

```

№ 14.
a)
```sql
select avg(price) from purchase;
```
<p align="left">
  <img src="https://imgur.com/4ivmm3X.png" width="600">
</p>

b)
```sql
select count(buyer) from purchase,shop
where purchase.seller=shop.id and shop.name='Наука'
```
<p align="left">
  <img src="https://imgur.com/ngAmHsZ.png" width="600">
</p>

c)
```sql
select avg(discount) from buyer;
select * from buyer where discount > (select avg(discount) from buyer)
```
<p align="left">
  <img src="https://imgur.com/c5MoEcM.png" width="600">
</p>

d)
```sql
select * from shop where id in (
SELECT seller from purchase
group by (seller) having count(*) > (select count(buyer) from purchase,shop
where purchase.seller=shop.id and shop.name='Наука'))
```
<p align="left">
  <img src="https://imgur.com/F289MiM.png" width="600">
</p>

№ 15.
a)
```sql
select name, SUM(price * quantity)
from shop,purchase,buyer
where purchase.seller=shop.id and purchase.buyer=buyer.id
group by name
```
<p align="left">
  <img src="https://imgur.com/gP5YLdW.png" width="600">
</p>

b)
```sql
select shop.district, name, SUM(price * quantity) as district
from shop,purchase,buyer
where purchase.seller=shop.id and purchase.buyer=buyer.id
group by shop.district,name
```
<p align="left">
  <img src="https://imgur.com/5hCL2Oj.png" width="600">
</p>

c)
```sql
select surname, SUM(price * quantity)
from purchase, buyer
where purchase.buyer=buyer.id
group by surname, buyer.id
```
<p align="left">
  <img src="https://imgur.com/Jlf0AT0.png" width="600">
</p>

d)
```sql
select month, SUM(quantity) as amount
from purchase, shop
where purchase.seller = shop.id AND shop.district != 'Советский' 
group by month
```
<p align="left">
  <img src="https://imgur.com/4V3GoUm.png" width="600">
</p>
