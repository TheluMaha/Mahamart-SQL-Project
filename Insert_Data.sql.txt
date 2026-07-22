USE mahamart;
INSERT INTO Categories (Category_Name, Description) VALUES
('Electronics', 'Mobiles, Laptops and Gadgets'),
('Fashion', 'Clothing and Accessories'),
('Home & Kitchen', 'Furniture and Kitchen Items'),
('Beauty', 'Cosmetics and Personal Care'),
('Sports', 'Sports Equipment');
INSERT INTO Sellers
(Seller_Name, Business_Name, Email, Phone, City, State, GST_Number, Rating, Join_Date)
VALUES
('Amit Verma','Tech World','amit@techworld.com','9876500001','Hyderabad','Telangana','GST1001',4.8,'2025-01-10'),
('Neha Gupta','Fashion Hub','neha@fashionhub.com','9876500002','Delhi','Delhi','GST1002',4.5,'2025-02-15'),
('Rohit Kumar','Home Essentials','rohit@home.com','9876500003','Bangalore','Karnataka','GST1003',4.6,'2025-03-20'),
('Pooja Sharma','Beauty Store','pooja@beauty.com','9876500004','Mumbai','Maharashtra','GST1004',4.7,'2025-04-18'),
('Suresh Reddy','Sports Zone','suresh@sports.com','9876500005','Chennai','Tamil Nadu','GST1005',4.4,'2025-05-25');
INSERT INTO Customers
(First_Name, Last_Name, Gender, Email, Phone, City, State, Pincode, Join_Date)
VALUES
('Rahul','Sharma','Male','rahul@gmail.com','9876543210','Hyderabad','Telangana','500001','2025-01-15'),
('Priya','Reddy','Female','priya@gmail.com','9876543211','Hyderabad','Telangana','500002','2025-02-20'),
('Arjun','Kumar','Male','arjun@gmail.com','9876543212','Bangalore','Karnataka','560001','2025-03-12'),
('Sneha','Patel','Female','sneha@gmail.com','9876543213','Mumbai','Maharashtra','400001','2025-04-18'),
('Kiran','Verma','Male','kiran@gmail.com','9876543214','Chennai','Tamil Nadu','600001','2025-05-25');
INSERT INTO Products
(Product_Name, Category_ID, Seller_ID, Brand, Price, Discount, Stock, Color, Weight, Launch_Date)
VALUES
('Samsung Galaxy S25',1,1,'Samsung',75000,10,50,'Black',0.18,'2025-01-10'),
('Dell Inspiron 15',1,1,'Dell',65000,12,30,'Silver',1.80,'2025-02-15'),
('Men T-Shirt',2,2,'Levis',1200,20,100,'Blue',0.30,'2025-03-20'),
('Office Chair',3,3,'Nilkamal',5500,15,25,'Black',8.50,'2025-04-12'),
('Cricket Bat',5,5,'SG',3500,8,40,'Brown',1.20,'2025-05-18');
INSERT INTO Warehouses
(Warehouse_Name, City, State, Capacity)
VALUES
('Hyderabad Warehouse','Hyderabad','Telangana',5000),
('Bangalore Warehouse','Bangalore','Karnataka',4500),
('Mumbai Warehouse','Mumbai','Maharashtra',6000);
INSERT INTO Inventory
(Product_ID, Warehouse_ID, Stock_Quantity, Last_Updated)
VALUES
(1,1,50,'2025-06-01'),
(2,2,30,'2025-06-01'),
(3,1,100,'2025-06-01'),
(4,3,25,'2025-06-01'),
(5,2,40,'2025-06-01');
INSERT INTO Orders
(Customer_ID, Order_Date, Total_Amount, Order_Status)
VALUES
(1,'2025-06-10',75000,'Delivered'),
(2,'2025-06-12',1200,'Delivered'),
(3,'2025-06-15',65000,'Shipped'),
(4,'2025-06-18',5500,'Processing'),
(5,'2025-06-20',3500,'Delivered');
INSERT INTO Order_Items
(Order_ID, Product_ID, Quantity, Price)
VALUES
(1,1,1,75000),
(2,3,1,1200),
(3,2,1,65000),
(4,4,1,5500),
(5,5,1,3500);
INSERT INTO Payments
(Order_ID, Payment_Date, Payment_Method, Amount, Payment_Status)
VALUES
(1,'2025-06-10','UPI',75000,'Success'),
(2,'2025-06-12','Credit Card',1200,'Success'),
(3,'2025-06-15','Net Banking',65000,'Success'),
(4,'2025-06-18','Cash on Delivery',5500,'Pending'),
(5,'2025-06-20','Debit Card',3500,'Success');
INSERT INTO Shipping
(Order_ID, Shipping_Address, City, State, Pincode, Delivery_Status, Delivery_Date)
VALUES
(1,'Madhapur','Hyderabad','Telangana','500081','Delivered','2025-06-12'),
(2,'Banjara Hills','Hyderabad','Telangana','500034','Delivered','2025-06-14'),
(3,'Whitefield','Bangalore','Karnataka','560066','Shipped','2025-06-17'),
(4,'Andheri','Mumbai','Maharashtra','400053','Processing',NULL),
(5,'T Nagar','Chennai','Tamil Nadu','600017','Delivered','2025-06-22');
INSERT INTO Reviews
(Customer_ID, Product_ID, Rating, Review_Text, Review_Date)
VALUES
(1,1,5,'Excellent mobile with great performance','2025-06-13'),
(2,3,4,'Good quality T-shirt','2025-06-15'),
(3,2,5,'Laptop works very smoothly','2025-06-18'),
(4,4,4,'Comfortable office chair','2025-06-20'),
(5,5,5,'Very good cricket bat','2025-06-23');
INSERT INTO Coupons
(Coupon_Code, Discount_Percentage, Expiry_Date)
VALUES
('WELCOME10',10,'2026-12-31'),
('SAVE20',20,'2026-10-31'),
('FESTIVE15',15,'2026-11-30'),
('NEWUSER25',25,'2026-09-30'),
('SUPER30',30,'2026-08-31');
INSERT INTO Product_Log
(Product_ID, Action_Performed, Action_Date)
VALUES
(1,'Product Added',NOW()),
(2,'Product Updated',NOW()),
(3,'Stock Updated',NOW()),
(4,'Price Updated',NOW()),
(5,'Product Added',NOW());