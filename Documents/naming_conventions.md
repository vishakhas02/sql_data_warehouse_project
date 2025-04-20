Naming Conventions -
This document outlines the naming conventions used for schemas, tables, views, columns, and other objects in the data warehouse.
----------------------------------------------------------------------------------------------------------------------------------
Table of Contents
1. General Principles
2. Table naming conventions
   > Bronze rules
   > Silver rules
   > Gold rules
3. Column naming conventions
   > Surrogate keys
   > Technical columns
4. Stored Procedures
-------------------------------------------------------------------------------------------------------------------------------------
General Principles
Naming Conventions: Use snake_case, with lowercase letters and underscores (_) to separate words.
Language: Use English for all names.
Avoid Reserved Words: Do not use SQL reserved words as object names.
--------------------------------------------------------------------------------------------------------------------------------------
Table Naming Conventions :
1. Bronze Rules
   > All names must start with the source system name, and table names must match their original names without renaming.
   > <sourcesystem>_<entity>
    <sourcesystem>: Name of the source system (e.g., crm, erp).
    <entity>: Exact table name from the source system.
    Example: crm_customer_info → Customer information from the CRM system.
2. Silver Rules
   > All names must start with the source system name, and table names must match their original names without renaming.
   > <sourcesystem>_<entity>
     <sourcesystem>: Name of the source system (e.g., crm, erp).
     <entity>: Exact table name from the source system.
     Example: crm_customer_info → Customer information from the CRM system.
3. Gold Rules
   > All names must use meaningful, business-aligned names for tables, starting with the category prefix.
   > <category>_<entity>
     <category>: Describes the role of the table, such as dim (dimension) or fact (fact table).
     <entity>: Descriptive name of the table, aligned with the business domain (e.g., customers, products, sales).
     Examples:
     dim_customers → Dimension table for customer data.
     fact_sales → Fact table containing sales transactions.
---------------------------------------------------------------------------------------------------------------------------
Column Naming Conventions
1. Surrogate Keys -
  > All primary keys in dimension tables must use the suffix _key.
  > <table_name>_key
    <table_name>: Refers to the name of the table or entity the key belongs to.
    _key: A suffix indicating that this column is a surrogate key.
    Example: customer_key → Surrogate key in the dim_customers table.

Technical Columns -
 > All technical columns must start with the prefix dwh_, followed by a descriptive name indicating the column's purpose.
 > dwh_<column_name>
   dwh: Prefix exclusively for system-generated metadata.
   <column_name>: Descriptive name indicating the column's purpose.
   Example: dwh_load_date → System-generated column used to store the date when the record was loaded.
---------------------------------------------------------------------------------------------------------------------------
Stored Procedure
> All stored procedures used for loading data must follow the naming pattern:
> load_<layer>.
  - <layer>: Represents the layer being loaded, such as bronze, silver, or gold.
  - Example :
    load_bronze → Stored procedure for loading data into the Bronze layer.
    load_silver → Stored procedure for loading data into the Silver layer.
