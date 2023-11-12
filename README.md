# engdados

# AWS RDS Connection and S3 Integration

This repository contains a Jupyter Notebook script that demonstrates the integration of an AWS RDS database with an S3 bucket using the psycopg2 and boto3 libraries. The script performs the following actions:

## Setup Database
1. Connects to the AWS RDS database named 'postgres' for initial configuration.
2. Creates a new database named 'inventario.'

```python
# Connection to AWS RDS with the psycopg2 lib
# ...
con = psycopg2.connect(
    host="database-1.cbjgisljmsxh.eu-north-1.rds.amazonaws.com",
    database="postgres",
    user="postgres",
    password="12345678"
)
# ...
```

## Create Table
3. Connects to the 'inventario' database and creates a table named 'arquivos' to store file IDs and names.

```python
# Creation of the files table
# ...
con = psycopg2.connect(
    host="database-1.cbjgisljmsxh.eu-north-1.rds.amazonaws.com",
    database="inventario",
    user="postgres",
    password="12345678"
)
# ...
```

## Fetch and Save File Names
4. Utilizes boto3 to interact with the AWS S3 bucket, retrieves file names with a specific prefix, and saves them to the 'arquivos' table in the 'inventario' database.

```python
# Now we can read objects at AWS Bucket and
# Also get its names and push them to our database "inventario"
# ...
s3 = boto3.resource(
    service_name='s3',
    region_name='eu-north-1',
    aws_access_key_id='AKIA3JFRCWMSHYLK7IOH',
    aws_secret_access_key='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'
)
# ...
```

## Verify Database Entries
5. Connects to the 'inventario' database and retrieves all entries from the 'arquivos' table to verify that the file names were successfully saved.

```python
# Now we can verify if the file names were saved into our database
# ...
con = psycopg2.connect(
    host="database-1.cbjgisljmsxh.eu-north-1.rds.amazonaws.com",
    database="inventario",
    user="postgres",
    password="12345678"
)
# ...
```

Feel free to use and adapt this script to your specific AWS RDS and S3 configurations. If you have any questions or need further assistance, please don't hesitate to reach out.
