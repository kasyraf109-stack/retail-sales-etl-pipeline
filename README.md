# Retail Sales ETL Pipeline

## Project Overview

This project demonstrates a basic **Extract, Transform, Load (ETL)** workflow using a retail sales dataset.

The objective is to transform one large transactional sales table into a cleaner **star schema** structure that is easier to analyze, validate, and reuse for reporting or dashboard development.

The notebook covers the full ETL process, including data extraction, data cleaning, feature creation, dimension table creation, fact table creation, validation, and CSV export.

---

## Project Objectives

The main goals of this project are to:

- Load and inspect the raw retail sales dataset
- Clean and standardize the dataset
- Handle missing values and duplicate records
- Convert date columns into proper datetime format
- Create useful date-related features
- Split the original dataset into multiple dimension tables
- Build a central fact table for sales transactions
- Validate row counts, primary keys, and sales totals
- Export the final transformed tables as CSV files

---

## Dataset

The project uses a Superstore-style retail sales dataset containing order, customer, product, location, shipping, and sales information.

Key fields include:

- Order ID
- Order Date
- Ship Date
- Ship Mode
- Customer ID
- Customer Name
- Segment
- Country
- City
- State
- Postal Code
- Region
- Product ID
- Category
- Sub-Category
- Product Name
- Sales

---

## ETL Workflow

### 1. Extract

The raw dataset is loaded into a Pandas DataFrame for inspection and processing.

### 2. Transform

The transformation process includes:

- Standardizing column names into lowercase snake_case format
- Rounding sales values to 2 decimal places
- Converting `order_date` and `ship_date` into datetime format
- Removing rows with missing postal codes
- Checking for duplicate rows
- Creating date features such as year, month, and year-month
- Formatting postal codes
- Calculating shipping duration
- Creating dimension tables
- Creating a central fact table
- Adding surrogate keys where needed

### 3. Load

The final transformed tables are exported as CSV files:

- `dim_customer.csv`
- `dim_product.csv`
- `dim_location.csv`
- `dim_date.csv`
- `dim_shipping.csv`
- `fact_sales.csv`

---

## Data Model

The final output follows a simple star schema design.

### Dimension Tables

| Table | Description |
|---|---|
| `dim_customer` | Stores customer details such as customer ID, customer name, and segment |
| `dim_product` | Stores product details such as product key, product ID, product name, category, and sub-category |
| `dim_location` | Stores location details such as country, city, state, region, and postal code |
| `dim_date` | Stores date-related fields such as order date, year, month, and year-month |
| `dim_shipping` | Stores shipping method information |

### Fact Table

| Table | Description |
|---|---|
| `fact_sales` | Stores sales transaction records and foreign keys linking to the dimension tables |

---

## Validation Checks

Several validation checks were performed to confirm that the transformed data is reliable.

| Check | Result |
|---|---|
| Original cleaned dataframe rows | 9,789 |
| Final fact table rows | 9,789 |
| Missing customer keys | 0 |
| Missing product keys | 0 |
| Missing location keys | 0 |
| Missing shipping keys | 0 |
| Original sales total | 2,252,607.18 |
| Fact table sales total | 2,252,607.18 |
| Sales total difference | 0.00 |

The validation confirms that the fact table preserves the row count and total sales value from the cleaned dataset.

---

## Tools Used

- Python
- Pandas
- Google Colab
- Jupyter Notebook
- GitHub

---

## Repository Structure

```text
retail-sales-etl-pipeline/
│
├── README.md
├── retail_sales_etl_pipeline.ipynb
├── .gitignore
│
├── output/
│   ├── dim_customer.csv
│   ├── dim_product.csv
│   ├── dim_location.csv
│   ├── dim_date.csv
│   ├── dim_shipping.csv
│   └── fact_sales.csv
│
└── data/
    └── superstore_dataset.csv

```
---

## How to Run This Project

1. Open the notebook in Google Colab or Jupyter Notebook.
2. Upload the dataset or update the file path in the notebook.
3. Run each notebook cell from top to bottom.
4. Review the generated dimension and fact tables.
5. Export the final tables as CSV files.

---

## Example Analysis

After building the star schema, the final tables can be used to answer questions such as:

- What is the monthly sales trend?
- Which product categories generate the highest sales?
- Which customer segments contribute the most revenue?
- Which regions have the strongest sales performance?
- What is the average shipping duration by shipping mode?

---

## Key Learning Outcomes

This project helped demonstrate important data engineering concepts, including:

- ETL pipeline development
- Data cleaning and standardization
- Dimensional modeling
- Star schema design
- Surrogate key creation
- Fact and dimension table validation
- Exporting transformed datasets for analysis

---

## Future Improvements

Possible future improvements include:

- Loading the final tables into a SQL database
- Creating SQL queries for analysis
- Building a Power BI or Tableau dashboard
- Automating the ETL workflow
- Adding data quality checks using a validation framework
- Creating an ERD diagram for the star schema
