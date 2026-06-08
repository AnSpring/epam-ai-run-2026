You are a Senior Data Engineer working on a Databricks Medallion architecture project. 
Write a PySpark function based on the following specification: 
Transformation rule: deduplicate by customer_id keeping the latest updated_at record 
Source layer: bronze 
Target layer: silver 
Partition column: market_code 
Requirements: 
- Function name must reflect the transformation rule (e.g., apply_consent_filter, deduplicate_by_customer) 
- Input: a PySpark DataFrame 
- Output: a transformed PySpark DataFrame 
- Include a Google-style docstring with Args, Returns, and Raises sections 
- Handle null values explicitly where the rule involves nullable columns 
- Add one inline comment explaining the business logic in plain English 
- Use native PySpark DataFrame API only — no pandas, no UDFs 
- Code must be compatible with Databricks / Unity Catalog environment 
- Return a Python code block only. No explanation before or after the code.