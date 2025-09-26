# plsql-window-functions-Uwase-Honette
PL/SQL Window Functions for agriculture analytics: customer segmentation, sales trends, regional performance ranking. Implements RANK(), NTILE(), LAG(), SUM() OVER() with complete database solution and business insights.
Agriculture Supply Chain Analysis with PL/SQL Window Functions
Business Overview
Company: Rwandan Farming Cooperative
Industry: Agriculture & Crop Distribution
Department: Sales Analytics & Business Intelligence

Business Challenge: The cooperative struggles to analyze regional sales performance, track customer purchasing patterns, and identify growth opportunities across different crop categories. Manual reporting makes it difficult to spot trends and optimize resource allocation.

Expected Outcome: Implement data-driven insights to identify top-performing regions, segment customers by value, and optimize crop distribution strategies for increased revenue.
Database Schema
Our database models the agriculture supply chain with four core tables tracking regions, products, customers, and sales transactions.
-- Regions table: Sales territories across Rwanda

CREATE TABLE regions (
    region_id NUMBER PRIMARY KEY,
    region_name VARCHAR2(50) NOT NULL,
    country VARCHAR2(50) DEFAULT 'Rwanda'
);
!![table one](screenshots/table1.PNG)

-- Products table: Crop inventory including Coffee, Maize, Beans, Tea, Potatoes
CREATE TABLE products (
    product_id NUMBER PRIMARY KEY,
    product_name VARCHAR2(100) NOT NULL,
    category VARCHAR2(50),
    unit_price NUMBER(10,2) NOT NULL
);
!![table two](screenshots/table2.PNG)
SQL> -- 3. Create Customers Table
SQL> CREATE TABLE customers (
  2      customer_id NUMBER PRIMARY KEY,
  3      name VARCHAR2(100) NOT NULL,
  4      region_id NUMBER NOT NULL,
  5      customer_type VARCHAR2(50) CHECK (customer_type IN ('Wholesaler', 'Retailer', 'Exporter')),
  6      join_date DATE
  7  );

Table created.
![table three](screenshots/table3.PNG)

SQL> -- 4. Create Sales Transactions Table
SQL> CREATE TABLE sales_transactions (
  2      transaction_id NUMBER PRIMARY KEY,
  3      customer_id NUMBER NOT NULL,
  4      product_id NUMBER NOT NULL,
  5      region_id NUMBER NOT NULL,
  6      sale_date DATE NOT NULL,
  7      quantity NUMBER NOT NULL,
  8      total_amount NUMBER(12,2) NOT NULL
  9  );
Table created.
![table three](screenshots/table4a.PNG)

ER diagram provides the foundational database structure that enables all window function analyses by clearly defining relationships between regions, products, customers, and sales transactions.
![ER-D](screenshots/ER_diagram.PNG)


