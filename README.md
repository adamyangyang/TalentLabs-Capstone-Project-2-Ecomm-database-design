# Ecommerce Database Design

## Overview
This project involves designing an ecommerce database for an ecommerce marketplace (ex: Shopee, WooCommerce etc).

The database consists of 12 tables, broken down by 5 dimension tables (non-red colors) and 8 fact tables (red colored).

Based on Kimball's definition of dimension and fact tables, they are defined as shown:

Dimensions - 

Facts - 

Some terminology to help understand this diagram:

|: The line '|----' indicates that there is one unique value for each data point in the table. 

Ex: Each product_id has a unique identification code for the ecommerce platform to accurately identify the product's name, price, size and etc.   

O< or >O: Many

The line 'O<---' or '--->O' indicates that each of the unique data points appear multiple times in the table.

Ex: Each product_id in the ProductRatings can appear multiple times because one single product can be rated by different users throughout different time periods.


## Database diagram
<img width="800" alt="Data Model" src="https://raw.githubusercontent.com/adamyangyang/ecomm-db-design/main/ERD-eComm-db.png">


For more clarity on the tables:

- Dimension tables in this database will always have a 'one-to-many' relationship with Fact tables 

Ex: Users (one) -> ShoppingSessions (many)

One user can browse through different product pages within a single web / mobile session.

- Dimension tables can also have a 'one-to-many' relationship with another dimension table 

Ex: ProductsCategory (one) -> Products

One product category can appear multiple times within a product table because there are many products that within a single product category (i.e. shirts, pants, caps are considered as apparel or clothing).

- Dimension tables that have a 'many-to-many' relationship is connected through a separate table. 

Ex: ShopOwners (many) -> Shops (many)

For some ecommerce platforms, an online shop owner can have multiple shops. This is connected through the table 'ShopOwnerEntity' to link the two tables together.

- Fact tables must have a 'one-to-many' relationship with another table if they are to connect with each other.

Ex: Orders (one) -> OrderDetails (many)

An easy way to understand this is to think about the receipt you get after buying a number of items from a store.

The 'Orders' table is a summary of your total price paid, when was it paid, if any discount was applied and etc.

The 'OrderDetails' table shows you what specific item you bought in each receipt, how much was bought, and each item's selling price.
 