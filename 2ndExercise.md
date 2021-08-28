
/* joins: select all the computers from the products table:
using the products table and the categories table, return the product name and the category name */

SELECT P.Name AS ProductName, C.Name AS CategoryName
FROM Products AS P
INNER JOIN Categories AS C
ON P.CategoryID = C.CategoryID
WHERE C.Name = 'Computers';
 
/* joins: find all product names, product prices, and products ratings that have a rating of 5 */

SELECT P.Name, P.Price, R.Rating 
FROM Products AS P
LEFT JOIN Reviews AS R
ON P.ProductID = R.ProductID
WHERE R.RATING = 5;
 
/* joins: find the employee with the most total quantity sold.  use the sum() function and group by */

SELECT E.FirstName, E.LastName, SUM(S.Quantity) AS Total
FROM sales AS S
INNER JOIN Employees AS E
ON E.EmployeeID = S.EmployeeID
GROUP BY E.EmployeeID
ORDER BY Total DESC;


/* joins: find the name of the department, and the name of the category for Appliances and Games */

SELECT d.Name as 'Department Name', c.Name as 'Category Name'
FROM departments AS d
INNER JOIN categories AS c
ON c.DepartmentID = d.DepartmentID
where c.Name = 'Games' or c.name = 'Appliances';

/* joins: find the product name, total # sold, and total price sold,
 for Eagles: Hotel California --You may need to use SUM() */
 
 select p.name, sum(s.quantity) as "Amount Sold", sum(s.PricePerUnit * s.quantity) as "Price Sold"
 from products as p
 inner join sales as s
 on s.productid = p.ProductID
 where p.productid = 97;

/* joins: find Product name, reviewer name, rating, and comment on the Visio TV. (only return for the lowest rating!) */

select p.Name, r.Reviewer,r.Rating, r.Comment
from products as p
inner join reviews as r
on r.productid = p.productid
where p.productid =857 and r.Rating = 1;
