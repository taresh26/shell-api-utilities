# Dummy Data Generator for PostgreSQL

This utility generates dummy unique data for testing purposes in a PostgreSQL database. It is designed to help you create millions of records dynamically.

## Prerequisites

- Python 3.x
- PostgreSQL server
- `Faker` library
- `psycopg2` library

You can install the required libraries using pip:

```bash
pip install faker psycopg2


Database Parameters: Update the following variables in generate_dummy_data.py:

DB_HOST = 'localhost'
DB_NAME = 'your_database_name'
DB_USER = 'your_username'
DB_PASS = 'your_password'
TABLE_NAME = 'your_table_name'  # Replace with your target table name
Table Structure: Ensure the target table has the following columns (adjust as necessary):


CREATE TABLE your_table_name (
    id UUID PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    address TEXT,
    dob DATE,
    age INTEGER
);
Usage
Run the script:


python generate_dummy_data.py
When prompted, enter the number of records you want to generate.

The script will connect to your PostgreSQL database and insert the generated data.

Notes
The generated data is unique due to the use of fake.unique.
Adjust the fields in the generate_dummy_data function to match your requirements.
Make sure to handle any database constraints or requirements specific to your schema.