# 📊 Data Catalog – Gold Layer

> The Gold Layer represents the **business-level** view of the data, optimized for **reporting and analysis**. It includes well-defined **dimension tables** and **fact tables** representing key business metrics and relationships.

---

## 🔹 Table of Contents
- [1. dim_customers](#1-dim_customers)
- [2. dim_products](#2-dim_products)
- [3. fact_sales](#3-fact_sales)
- [📌 Entity Relationship Diagram](#-entity-relationship-diagram)

---

## 1. `gold.dim_customers`
**Purpose:** Stores customer details enriched with demographic and geographic data.

| Column Name     | Data Type     | Description                                                                 |
|-----------------|---------------|-----------------------------------------------------------------------------|
| `customer_key`  | INT           | Surrogate key uniquely identifying each customer record.                    |
| `customer_id`   | INT           | Unique numerical identifier assigned to each customer.                      |
| `customer_number` | NVARCHAR(50) | Alphanumeric ID (e.g., `CUST-00123`).                                       |
| `first_name`    | NVARCHAR(50)  | Customer's first name.                                                      |
| `last_name`     | NVARCHAR(50)  | Customer's last name.                                                       |
| `country`       | NVARCHAR(50)  | Country of residence (e.g., `Australia`).                                   |
| `marital_status`| NVARCHAR(50)  | Marital status (e.g., `Married`, `Single`).                                 |
| `gender`        | NVARCHAR(50)  | Gender (`Male`, `Female`, `n/a`).                                           |
| `birthdate`     | DATE          | Date of birth (e.g., `1971-10-06`).                                         |
| `create_date`   | DATE          | Record creation date (e.g., `2022-01-01`).                                  |

---

## 2. `gold.dim_products`
**Purpose:** Provides information about products and their business attributes.

| Column Name         | Data Type     | Description                                                                 |
|---------------------|---------------|-----------------------------------------------------------------------------|
| `product_key`       | INT           | Surrogate key for each product.                                             |
| `product_id`        | INT           | Unique product identifier.                                                  |
| `product_number`    | NVARCHAR(50)  | Code (e.g., `PRD-XYZ-100`).                                                 |
| `product_name`      | NVARCHAR(50)  | Product name (e.g., `Mountain Bike - Red`).                                 |
| `category_id`       | NVARCHAR(50)  | ID linking to category (e.g., `CAT001`).                                    |
| `category`          | NVARCHAR(50)  | Product category (`Bikes`, `Components`).                                   |
| `subcategory`       | NVARCHAR(50)  | Subcategory (`Helmets`, `Frames`).                                          |
| `maintenance_required` | NVARCHAR(50) | Indicates if maintenance is needed (`Yes`, `No`).                         |
| `cost`              | DECIMAL(10,2) | Base cost of the product (e.g., `1500.00`).                                 |
| `product_line`      | NVARCHAR(50)  | Line of the product (`Road`, `Mountain`).                                   |
| `start_date`        | DATE          | Launch date (e.g., `2021-03-15`).                                           |

---

## 3. `gold.fact_sales`
**Purpose:** Contains transactional sales records for reporting and analytics.

| Column Name     | Data Type     | Description                                                                 |
|-----------------|---------------|-----------------------------------------------------------------------------|
| `order_number`  | NVARCHAR(50)  | Sales order ID (e.g., `SO54496`).                                           |
| `product_key`   | INT           | Foreign key to `dim_products`.                                              |
| `customer_key`  | INT           | Foreign key to `dim_customers`.                                             |
| `order_date`    | DATE          | Date the order was placed.                                                 |
| `shipping_date` | DATE          | Date the order was shipped.                                                |
| `due_date`      | DATE          | Due date for the payment.                                                  |
| `sales_amount`  | DECIMAL(10,2) | Total sales amount (e.g., `499.99`).                                       |
| `quantity`      | INT           | Quantity sold.                                                              |
| `price`         | DECIMAL(10,2) | Unit price (e.g., `249.99`).                                               |

---

## 📌 Entity Relationship Diagram

> This ERD illustrates the relationship between the dimension and fact tables.

```mermaid
erDiagram
    gold_dim_customers {
        INT customer_key PK
        INT customer_id
        NVARCHAR customer_number
        NVARCHAR first_name
        NVARCHAR last_name
        NVARCHAR country
        NVARCHAR marital_status
        NVARCHAR gender
        DATE birthdate
        DATE create_date
    }

    gold_dim_products {
        INT product_key PK
        INT product_id
        NVARCHAR product_number
        NVARCHAR product_name
        NVARCHAR category_id
        NVARCHAR category
        NVARCHAR subcategory
        NVARCHAR maintenance_required
        DECIMAL cost
        NVARCHAR product_line
        DATE start_date
    }

    gold_fact_sales {
        NVARCHAR order_number PK
        INT product_key FK
        INT customer_key FK
        DATE order_date
        DATE shipping_date
        DATE due_date
        DECIMAL sales_amount
        INT quantity
        DECIMAL price
    }

    gold_fact_sales ||--o{ gold_dim_customers : "customer_key"
    gold_fact_sales ||--o{ gold_dim_products : "product_key"
