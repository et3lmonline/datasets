# Datasets

- [Contoso Dataset](https://www.microsoft.com/en-us/download/details.aspx?id=18279): A fictitious retail demo dataset used for presenting Microsoft Business Intelligence products.
  - OLTP Version 1: Restructured from the [original Contoso Data Warehouse (DWH)](contoso_oltp_v1/original_structure.md) tables:
    - Tables were renamed
    - Primary keys renamed (e.g., `DimProducts.product_key` to `products.id`).
    - Foreign keys renamed (e.g., `FactSales.StoreKey` to `sales_line_items.store_id`).
    - Data covers the period from 2007 - 2009
