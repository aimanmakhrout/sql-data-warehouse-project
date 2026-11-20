# Datasets

Place the source CSV files here:

```
datasets/
├── source_crm/  cust_info.csv · prd_info.csv · sales_details.csv
└── source_erp/  CUST_AZ12.csv · LOC_A101.csv · PX_CAT_G1V2.csv
```

Then update the `BULK INSERT` paths in `scripts/bronze/proc_load_bronze.sql`.
