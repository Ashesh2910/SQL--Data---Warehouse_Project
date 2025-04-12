# 📊 Gold Layer Data Catalog

This repository documents the **Gold Layer** of the data warehouse, optimized for **analytics and reporting**. It includes **dimension and fact tables**, sample data, a relationship diagram, and Power BI integration notes.

---

## 🔹 Table of Contents

- [1. dim_customers](#1-dim_customers)
- [2. dim_products](#2-dim_products)
- [3. fact_sales](#3-fact_sales)
- [📌 Entity Relationship Diagram](#-entity-relationship-diagram)
- [🧪 Sample Data](#-sample-data)
- [📈 Power BI Integration](#-power-bi-integration)

---

## 1. `gold.dim_customers`

**Purpose:** Stores customer details enriched with demographic and geographic data.

| Column Name       | Data Type     | Description                              |
|-------------------|---------------|------------------------------------------|
| `customer_key`    | INT           | Surrogate key for internal joins.        |
| `customer_id`     | INT           | External unique customer identifier.     |
| `customer_number` | NVARCHAR(50)  | Alphanumeric ID (e.g., `CUST-00123`).     |
| `first_name`      | NVARCHAR(50)  | First name of the customer.              |
| `last_name`       | NVARCHAR(50)  | Last name of the customer.               |
| `country`         | NVARCHAR(50)  | Country (e.g., `Australia`).             |
| `marital_status`  | NVARCHAR(50)  | `Single`, `Married`, etc.                |
| `gender`          | NVARCHAR(50)  | `Male`, `Female`, `n/a`, etc.            |
| `birthdate`       | DATE          | Format: `YYYY-MM-DD`                     |
| `create_date`     | DATE          | Record creation date.                    |

---

## 2. `gold.dim_products`

**Purpose:** Contains product master data and attributes.

| Column Name           | Data Type     | Description                              |
|-----------------------|---------------|------------------------------------------|
| `product_key`         | INT           | Surrogate key for internal joins.        |
| `product_id`          | INT           | External product identifier.             |
| `product_number`      | NVARCHAR(50)  | SKU or structured ID (e.g., `PRD-XYZ-100`).|
| `product_name`        | NVARCHAR(50)  | Full product description.                |
| `category_id`         | NVARCHAR(50)  | Maps to category hierarchy.              |
| `category`            | NVARCHAR(50)  | Top-level category (e.g., `Bikes`).      |
| `subcategory`         | NVARCHAR(50)  | Subgroup of products.                    |
| `maintenance_required`| NVARCHAR(50)  | `Yes` or `No`.                           |
| `cost`                | DECIMAL(10,2) | Base cost in currency.                   |
| `product_line`        | NVARCHAR(50)  | Line or family (e.g., `Road`).           |
| `start_date`          | DATE          | Launch date.                             |

---

## 3. `gold.fact_sales`

**Purpose:** Stores transactional sales data.

| Column Name     | Data Type     | Description                              |
|-----------------|---------------|------------------------------------------|
| `order_number`  | NVARCHAR(50)  | Sales order ID (e.g., `SO54496`).        |
| `product_key`   | INT           | FK to `dim_products`.                    |
| `customer_key`  | INT           | FK to `dim_customers`.                   |
| `order_date`    | DATE          | Order placement date.                    |
| `shipping_date` | DATE          | Date of shipment.                        |
| `due_date`      | DATE          | Payment due date.                        |
| `sales_amount`  | DECIMAL(10,2) | Total sales value.                       |
| `quantity`      | INT           | Number of units sold.                    |
| `price`         | DECIMAL(10,2) | Price per unit.                          |

---

## 📌 Entity Relationship Diagram

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

## 🧪 Sample Data

### `dim_customers`

| customer_key | customer_number | first_name | last_name | country    |
|--------------|-----------------|------------|-----------|------------|
| 101          | CUST-0001       | Sarah      | Connor    | Australia  |
| 102          | CUST-0002       | John       | Doe       | Canada     |

---

### `dim_products`

| product_key | product_number | product_name         | category   | cost    |
|-------------|----------------|----------------------|------------|---------|
| 201         | PRD-1001       | Road Bike - Blue     | Bikes      | 1200.00 |
| 202         | PRD-1002       | Helmet - Medium      | Components | 150.00  |

---

### `fact_sales`

| order_number | customer_key | product_key | order_date | sales_amount | quantity | price   |
|--------------|--------------|-------------|------------|--------------|----------|---------|
| SO1001       | 101          | 201         | 2023-01-10 | 2400.00      | 2        | 1200.00 |
| SO1002       | 102          | 202         | 2023-02-15 | 300.00       | 2        | 150.00  |
