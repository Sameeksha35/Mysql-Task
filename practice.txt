**having and groupby queries

1.counting orders greater than 2 by customer
-> select count(orderId) ,customerId from orders group by customerId having count(orderId) > 2;

2.we want to find departments where the average salary is above $60000
-> select departmentId,Avg(salary) as avgSalary from employee groupby departmentId having avg(salary) > 60000;

3.to find departments where at least one employee earns more than $80000:
-> select departmentId,max(salary) from employee having max(salary) > 80000;

4.We want to find products where the total sales amount (quantity sold multiplied by price per unit) exceeds $500.
-> select productId ,sum(quantity * priceperunit) as totalsales from sales group by productId having sum(quantity * priceperunit) > 500;

ProductID	Quantity	PricePerUnit
1	              10	20.00
1	               5	15.00
2	               3	25.00
2	               8	10.00
3	               6	12.00

5.filtering departments with more than 10 employees
-> select departmentId, count(*) as NumOfEmployee from employee group by departmentId having count(*) > 10;

6.finding product categories with an average price greater than $50
-> select categoryId, avg(priceperunit) as avgprice from products group by categoryId having avg(priceperunit) > 50;

7.filtering products with more than 100 units in stock
-> select productId,sum(instock) as TotalStock from inventory group by productId having sum(instock) > 100;

8.finding countries with more than 5 orders
-> select country ,count(orderId) as NumOfOrders from orders group by country having count(orderId) > 5;

9.Identifying departments with an average salary greater than $70000
-> slect departmentId,avg(salary) as avgsalary from employee group by departmentId having avg(salary) > 70000;

10.filtering products with at least 3 reviews:
select productId count(reviewId) as NumOfReviews from ProductReviews group by productId having count(reviewId) >= 3;

11.finding customers who placed orders in more than 2 different months
-> select customerId,count(Distinct month(orderDate)) as NumOfDifferentMonths from orders group by customerId having count(Distinct month(orderDate)) > 2;

12.Identifying sales represtative with more than $10000 in total sales;
-> select salesRepId ,sm(TotalSales) as TotalSales from sales group by salesRepId having sum(TotalSales) > 10000;

13.filtering product categories with at least 10 different products;
->select categoryId ,count(Distinct productId) as NumOfProducts from products group by categoryId having count(Distinct productId) >= 10;






**aggregate function queries
1. counting the number of orders for each customer
-> select customerId,count(orderId) from orders group by customerId;

2.finding the minimum and maximum order amounts for each customer
-> select customerId,min(orderamount) as minorderAmount,max(orderamount) as maxorderAmount from orders group by customerId;

3.counting the number of employees in each departmentId
-> select departmentId,count(*) as NumOfEmployee from Employees group by departmentId;

4.calculating the total quantity ordered for each product category:
-> select categoryId,sum(quantity) as totalQuantityOrdered from products group by categoryId;

5.finding the average price per unit for each product
-> select productId,avg(priceperunit) as AvgPricePerUnnit from product group by productId;

6.calculating the total revenue for each year
-> select year(orderDate) as orderYear,sum(totalAmout) as totalRevenue from orders group by year(orderDate);

7.identifying the product with the highest sales amount
-> select productId, max(salesAmount) as maxsalesAmount from orders group by productId;

8.calculating the average order processing time for each shipping method
-> select shipMethod , Avg(DATEDIFF(shippedDate,OrderDate)) as AvgProcessingTime from orders group by shipMethod;




**joins queries

1.provide department name, using joins in employee and department table
-> select employee.departmentId,department.dep_id from employee join department on employee.dep_id = dep_id;

2.provide count of employee work in each department
-> select employee.count(emp_id),department.dep_id from employee join department on employee.dep_id = dep_id group by department.dep_id;

3.provide corresponding order name to the customerId
->select customer.id,orders.name from customer join orders on customer.id = orders.order.id;

4.display courseId each student from student table study
-> select student.roll_no,study.courseId from student inner join study on student.roll_no = study.roll_no;

5.display all details from both table student and study
-> select * from student full join study on student.roll_no = study.roll_no;



