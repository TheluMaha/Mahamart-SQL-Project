USE mahamart;

CREATE TABLE Categories (
    Category_ID INT PRIMARY KEY AUTO_INCREMENT,
    Category_Name VARCHAR(100) NOT NULL,
    Description VARCHAR(255)
);

CREATE TABLE Sellers (
    Seller_ID INT PRIMARY KEY AUTO_INCREMENT,
    Seller_Name VARCHAR(100) NOT NULL,
    Business_Name VARCHAR(100),
    Email VARCHAR(100),
    Phone VARCHAR(15),
    City VARCHAR(50),
    State VARCHAR(50),
    GST_Number VARCHAR(30),
    Rating DECIMAL(2,1),
    Join_Date DATE
);

CREATE TABLE Customers (
    Customer_ID INT PRIMARY KEY AUTO_INCREMENT,
    First_Name VARCHAR(50),
    Last_Name VARCHAR(50),
    Gender VARCHAR(10),
    Email VARCHAR(100),
    Phone VARCHAR(15),
    City VARCHAR(50),
    State VARCHAR(50),
    Pincode VARCHAR(10),
    Join_Date DATE
);
CREATE TABLE Products (
    Product_ID INT PRIMARY KEY AUTO_INCREMENT,
    Product_Name VARCHAR(100) NOT NULL,
    Category_ID INT,
    Seller_ID INT,
    Brand VARCHAR(100),
    Price DECIMAL(10,2),
    Discount DECIMAL(5,2),
    Stock INT,
    Color VARCHAR(50),
    Weight DECIMAL(10,2),
    Launch_Date DATE,
    FOREIGN KEY (Category_ID) REFERENCES Categories(Category_ID),
    FOREIGN KEY (Seller_ID) REFERENCES Sellers(Seller_ID)
);

CREATE TABLE Warehouses (
    Warehouse_ID INT PRIMARY KEY AUTO_INCREMENT,
    Warehouse_Name VARCHAR(100),
    City VARCHAR(50),
    State VARCHAR(50),
    Capacity INT
);

CREATE TABLE Inventory (
    Inventory_ID INT PRIMARY KEY AUTO_INCREMENT,
    Product_ID INT,
    Warehouse_ID INT,
    Stock_Quantity INT,
    Last_Updated DATE,
    FOREIGN KEY (Product_ID) REFERENCES Products(Product_ID),
    FOREIGN KEY (Warehouse_ID) REFERENCES Warehouses(Warehouse_ID)
);

CREATE TABLE Orders (
    Order_ID INT PRIMARY KEY AUTO_INCREMENT,
    Customer_ID INT,
    Order_Date DATE,
    Total_Amount DECIMAL(10,2),
    Order_Status VARCHAR(30),
    FOREIGN KEY (Customer_ID) REFERENCES Customers(Customer_ID)
);
CREATE TABLE Order_Items (
    Order_Item_ID INT PRIMARY KEY AUTO_INCREMENT,
    Order_ID INT,
    Product_ID INT,
    Quantity INT,
    Price DECIMAL(10,2),
    FOREIGN KEY (Order_ID) REFERENCES Orders(Order_ID),
    FOREIGN KEY (Product_ID) REFERENCES Products(Product_ID)
);

CREATE TABLE Payments (
    Payment_ID INT PRIMARY KEY AUTO_INCREMENT,
    Order_ID INT,
    Payment_Date DATE,
    Payment_Method VARCHAR(50),
    Amount DECIMAL(10,2),
    Payment_Status VARCHAR(30),
    FOREIGN KEY (Order_ID) REFERENCES Orders(Order_ID)
);

CREATE TABLE Shipping (
    Shipping_ID INT PRIMARY KEY AUTO_INCREMENT,
    Order_ID INT,
    Shipping_Address VARCHAR(255),
    City VARCHAR(50),
    State VARCHAR(50),
    Pincode VARCHAR(10),
    Delivery_Status VARCHAR(30),
    Delivery_Date DATE,
    FOREIGN KEY (Order_ID) REFERENCES Orders(Order_ID)
);

CREATE TABLE Reviews (
    Review_ID INT PRIMARY KEY AUTO_INCREMENT,
    Customer_ID INT,
    Product_ID INT,
    Rating INT,
    Review_Text VARCHAR(255),
    Review_Date DATE,
    FOREIGN KEY (Customer_ID) REFERENCES Customers(Customer_ID),
    FOREIGN KEY (Product_ID) REFERENCES Products(Product_ID)
);

CREATE TABLE Coupons (
    Coupon_ID INT PRIMARY KEY AUTO_INCREMENT,
    Coupon_Code VARCHAR(20),
    Discount_Percentage DECIMAL(5,2),
    Expiry_Date DATE
);

CREATE TABLE Product_Log (
    Log_ID INT PRIMARY KEY AUTO_INCREMENT,
    Product_ID INT,
    Action_Performed VARCHAR(100),
    Action_Date DATETIME,
    FOREIGN KEY (Product_ID) REFERENCES Products(Product_ID)
);