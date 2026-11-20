# Naming Conventions

| Object | Rule | Example |
|---|---|---|
| Schemas | layer name | `bronze`, `silver`, `gold` |
| Bronze / Silver tables | `<source_system>_<entity>` (source names kept) | `crm_cust_info`, `erp_loc_a101` |
| Gold views | `dim_<entity>` / `fact_<entity>` | `dim_customers`, `fact_sales` |
| Surrogate keys | `<entity>_key` | `customer_key` |
| Technical columns | `dwh_` prefix | `dwh_create_date` |
| Load procedures | `<layer>.load_<layer>` | `silver.load_silver` |
| Style | `snake_case`, English, no SQL reserved words | |
