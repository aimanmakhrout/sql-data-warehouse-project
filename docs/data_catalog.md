# Data Catalog — Gold Layer

## gold.dim_customers
One row per customer, combining CRM and ERP data.

| Column | Type | Description |
|---|---|---|
| customer_key | INT | Surrogate key |
| customer_id | INT | CRM customer id |
| customer_number | NVARCHAR(50) | Business key used across systems |
| first_name | NVARCHAR(50) | First name |
| last_name | NVARCHAR(50) | Last name |
| country | NVARCHAR(50) | Country of residence (ERP) |
| marital_status | NVARCHAR(50) | `Single`, `Married`, `n/a` |
| gender | NVARCHAR(50) | `Male`, `Female`, `n/a` (CRM first, ERP fallback) |
| birthdate | DATE | Date of birth (ERP) |
| create_date | DATE | Customer creation date in CRM |

## gold.dim_products
Current products (no end date) enriched with ERP categories.

| Column | Type | Description |
|---|---|---|
| product_key | INT | Surrogate key |
| product_id | INT | CRM product id |
| product_number | NVARCHAR(50) | Business product code |
| product_name | NVARCHAR(50) | Product name |
| category_id | NVARCHAR(50) | Category id (derived from product code) |
| category | NVARCHAR(50) | e.g. Bikes, Components |
| subcategory | NVARCHAR(50) | Detailed classification |
| maintenance | NVARCHAR(50) | Maintenance required (`Yes`/`No`) |
| cost | INT | Base cost |
| product_line | NVARCHAR(50) | Mountain, Road, Touring, Other Sales |
| start_date | DATE | Date the product version became active |

## gold.fact_sales
One row per order line.

| Column | Type | Description |
|---|---|---|
| order_number | NVARCHAR(50) | Sales order id |
| product_key | INT | FK → dim_products |
| customer_key | INT | FK → dim_customers |
| order_date | DATE | Order date |
| shipping_date | DATE | Shipping date |
| due_date | DATE | Payment due date |
| sales_amount | INT | quantity × price |
| quantity | INT | Units ordered |
| price | INT | Unit price |
