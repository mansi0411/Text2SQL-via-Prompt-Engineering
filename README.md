# Text2SQL-via-Prompt-Engineering

# Natural Language to SQL Converter

## What It Does
Converts English questions into SQL queries using Google's Gemini AI. Ask questions in plain English, get database results without writing SQL.

## Setup
```bash
pip install google-genai pandas
```

## Database Tables

**customers**: customer_id, first_name, last_name, email, phone_number, address, city, country, postal_code, membership_level

**products**: product_id, product_name, product_category, product_price, product_description, product_weight, product_color, product_brand, product_material, product_size, product_stock_quantity

**orders**: order_id, customer_id, product_id, quantity, unit_price, total_price, order_date, shipping_address, payment_method, status

## Main Functions

### `get_sql_query(genai_client, prompt, user_query)`
- Takes user question in English
- Returns JSON with SQL query or clarification needed

### `execute_query(query, db_name='ecommerce.db')`
- Runs SQL query on database
- Returns results as pandas DataFrame

### `text2sql(genai_client, prompt, user_query)`
- Combines both functions
- Translates English → SQL → Results

## Usage Examples

```python
# Orders by country
text2sql(genai_client, prompt, "Show me the order count by country")

# Orders by day
text2sql(genai_client, prompt, "Give me the order count by day of month")

# Top products
text2sql(genai_client, prompt, "What are my highest total quantity sold products")
```

## Features
- Natural language input (no SQL needed)
- Automatic table joins
- Aggregations (COUNT, SUM, GROUP BY)
- Error handling for impossible queries
- Token usage tracking

## Response Types
- `success`: SQL query generated
- `clarification_needed`: Question is ambiguous
- `error`: Request can't be done with schema
