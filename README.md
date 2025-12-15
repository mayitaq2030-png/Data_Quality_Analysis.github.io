# Data Quality Analysis Global Logistics Company

### Executive Summary:

<p align ="justify"> A global logistics company was facing inefficiencies in order delivery due to poor data quality. Incomplete records and duplicate entries caused delays and costly operational errors. After analyzing the shipping dataset, several data-cleaning and standardization techniques were applied. The project included the development of a Power BI dashboard featuring an Order Completion chart highlighting the percentage of orders delivered correctly versus those affected by data errors. Once the data was corrected, the rate of fully completed deliveries increased and customer support workload decreased. Overall, validation processes were optimized and business rules were established, resulting in more reliable logistics data and improved operational efficiency. </p>

### Business Problem:

In logistics, data accuracy is mission-critical: even the best operations cannot deliver an order if the address is wrong. Several issues were identified across the company:

- Incomplete or poorly formatted addresses: missing street names, invalid postal codes, inconsistent formats.

- Duplicate records: identical orders entered multiple times, creating inventory confusion and duplicated shipments. Duplicates also distorted reports and produced a poor customer experience (such as multiple confirmation emails).

- Date/time inconsistencies: mismatched formats across systems (YYYY-MM-DD vs DD/MM/YYYY), affecting delivery prioritization.

- These issues translated into returns, delays, and additional costs. In summary, the lack of data integrity and accuracy disrupted the efficiency of the supply chain.

### Order Completion Chart

<p align ="justify"> To illustrate the impact of data quality, an Order Completion chart was designed. The dashboard allows filtering by delivery route, carrier, or date range, helping quickly identify the most common error categories. The visualization shows that 85% of orders are delivered without issues, while 15% experience problems attributable to data quality. These metrics reinforce the need for data cleansing and help monitor improvements over time. </p>

<img width="600" height="425" alt="ChatGPT Image 15 dic 2025, 01_16_16 p m" src="https://github.com/user-attachments/assets/90d81573-40da-4925-9369-c151a20d1b7c" />

### Methodology

The problem was addressed through a multi-stage data analysis and data-cleaning process:

#### 1. Initial Profiling

Using SQL and Python, the order database (from a PostgreSQL warehouse) was loaded to calculate data-quality metrics: percentage of null fields, duplicates, and value-range validations. Critical fields with missing data (such as postal codes) and duplicate order entries were identified.

#### 2. Cleaning Strategy

Address validation and cleaning: a geocoding API (Google Maps API) was used to correct and standardize addresses. Each order was validated to ensure it contained a complete and correct address before being processed.

Duplicate removal: deduplication rules were applied using combinations of key fields (customer ID, date, SKU) through Python (pandas) and SQL.

Format standardization: date formats were normalized to ISO; units were standardized (e.g., “kg” vs. “KILOGRAMOS”).

Cross-validations: referential integrity checks were performed across tables (e.g., each shipment must reference an existing order). Orphan orders were flagged for manual correction, preventing shipments to non-existent customers.

#### 3. Visualization

Cleaned data was connected to Power BI. A dashboard was created featuring key metrics (completed orders, delivery times, error causes) and the Order Completion chart. This allowed operations teams to monitor supply chain performance in real time.

In summary, the approach combined data-engineering techniques (Python/SQL) with data-governance strategies (validation rules and shared standards) to ensure accuracy, integrity, and consistency across logistics records.

### Skills

Python: Pandas, NumPy, regex for cleaning, API consumption (address geocoding).

SQL: PostgreSQL for profiling queries (COUNT, JOIN, GROUP BY) and cleaning scripts (conditional UPDATE and DELETE).

Power BI: dashboard creation, visual storytelling, and KPI design (Order Completion chart, metric tables).

Other: Excel for spot checks, ETL tools, and industry-standard data-quality practices (field validation, business rules, profiling).

#### Results & Recommendations


<img width="600" height="425" alt="ChatGPT Image 15 dic 2025, 01_33_24 p m" src="https://github.com/user-attachments/assets/155354dc-82b3-4098-8c5e-40fc22dedada" />


#### Results

Clean Data: 12% of records with incomplete addresses were corrected, and duplicate entries causing order duplication were removed. This increased the rate of successful deliveries and reduced operational errors.

Improved KPIs: higher accuracy in delivery-time calculations and reduced reshipment costs. Pending-order reports became reliable for inventory decision-making.

#### Recommendations

Automate validations: embed validation rules into data-loading processes (mandatory fields, address-format checks).

Data governance policies: create a logistics data catalog and clear ownership roles. Implement periodic quality checks (profiling) to detect issues early.

System integration: standardize formats across ERP and TMS systems to prevent duplicates caused by schema mismatches.

In essence, improved data quality strengthened the logistics operation. Clean data enables better decision-making, operational efficiency, cost reduction, and higher customer satisfaction.

### Next Steps

- Continuous monitoring: develop automated data-quality pipelines with alerts for new missing values or duplicates.

- Advanced analytics: apply machine learning to predict delays or delivery incidents using the cleaned historical dataset.

- Project expansion: incorporate post-delivery analytics (customer feedback, service quality) to close the improvement loop.

- Documentation and training: create internal guides on logistics data management and train staff on best practices (data entry, standard templates).
