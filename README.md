# Ecommerce Database Design

## Overview
This project involves designing an ecommerce database for an ecommerce marketplace (ex: Shopee, WooCommerce etc).

The database consists of **12 tables**, broken down by **5 dimension tables (non-red colors)** and **8 fact tables (red colored)**.

Based on [Kimball's definition](https://www.kimballgroup.com/2003/01/fact-tables-and-dimension-tables/) of dimension and fact tables, they are defined as shown:

### Dimension Tables
They provide context such as "who, what, where, when, why and how" to an event or business process.

*Ex: What products have the highest sales?*

### Fact Tables
They measure the result from an event or business process we want to track. They are also always numeric.

*Ex: How much revenue do we have.*


When combined together, **dimension tables provide context to the fact tables** to help us better understand the business metrics we're measuring.

*Ex: What products brought in the highest revenue for Q1 this year?*

_________________________________________________________________________________________________________________

### Some terminology to help understand this diagram

**The line '|----'** 

This indicates that there is **one unique value** for each data point in the table. 

*Ex: Each product_id has a unique identification code for the ecommerce platform to accurately identify the product's name, price, size and etc.*

**The line 'O<---'** or **'--->O'** 

This indicates that **each of the unique data points appear multiple times** in the table.

*Ex: Each product_id in the ProductRatings can appear multiple times because one single product can be rated by different users throughout different time periods.*


## Database diagram
<img width="800" alt="Data Model" src="https://raw.githubusercontent.com/adamyangyang/ecomm-db-design/main/ERD-eComm-db.png">


### For more clarity on the tables:

#### 1) Dimension tables in this database will always have a 'one-to-many' relationship with Fact tables
<img width="150" alt="Users and Shopping Sessions" src="https://raw.githubusercontent.com/adamyangyang/ecomm-db-design/main/images/user-shopping-sessions.PNG">

*Ex: Users (one) -> ShoppingSessions (many)*

One user can browse through different product pages within a single web / mobile session.



#### 2) Dimension tables can also have a 'one-to-many' relationship with another Dimension table. 
<img width="300" alt="Product and Product Categories" src="https://raw.githubusercontent.com/adamyangyang/ecomm-db-design/main/images/products-category.PNG">

*Ex: ProductsCategory (one) -> Products*

One product category can appear multiple times within a product table because there are many products that within a single product category (i.e. shirts, pants, caps are considered as apparel or clothing).



#### 3) Dimension tables that have a **'many-to-many' relationship** is connected through a separate table. 
<img width="300" alt="Multiple Shop Owners" src="https://raw.githubusercontent.com/adamyangyang/ecomm-db-design/main/images/multiple-shop-owners.PNG">

*Ex: ShopOwners (many) -> Shops (many)*

For some ecommerce platforms, an online shop owner can have multiple shops. This is connected through the table 'ShopOwnerEntity' to link the two tables together.



#### 4) Fact tables must have a **'one-to-many' relationship** with another table if they are to connect with each other.
<img width="300" alt="Orders and OrderDetails" src="https://raw.githubusercontent.com/adamyangyang/ecomm-db-design/main/images/order-details.PNG">

*Ex: Orders (one) -> OrderDetails (many)*

An easy way to understand this is to think about the receipt you get after buying a number of items from a store.

The 'Orders' table is a summary of your total price paid, when was it paid, if any discount was applied and etc.

The 'OrderDetails' table shows you what specific item you bought in each receipt, how much was bought, and each item's selling price.
 
