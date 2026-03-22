## ETL Decisions

### Decision 1 – Date Format Standardization
Problem:
The dataset contains inconsistent date formats such as "29/08/2023", "12-12-2023", and "2023-02-05". This inconsistency makes it difficult to perform time based analysis and grouping.

Resolution:
All dates were converted into a standard ISO format (YYYY-MM-DD). This ensures uniformity and allows efficient querying, filtering, and aggregation by month and year in the data warehouse.

### Decision 2 – Category Normalization
Problem:
Category values are inconsistent across records, such as "electronics", "Electronics", and "Grocery" vs "Groceries". This leads to incorrect grouping and inaccurate analytical results.

Resolution:
All category values were standardized to consistent formats such as "Electronics", "Clothing", and "Groceries". This ensures correct aggregation and improves data quality in reporting.

### Decision 3 – Handling Missing and Inconsistent Values
Problem:
Raw transactional data may contain NULL values or inconsistencies in fields such as unit_price or units_sold, which can impact revenue calculations.

Resolution:
Missing numerical values were handled by either removing invalid records or replacing them with appropriate details. Additionally,
derived fields like total_amount were calculated as (units_sold × unit_price) to ensure accuracy and consistency in the fact table.
