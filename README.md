# Database star schema and ETL pipeline for Sparkify's analytics team

Esteban Zuniga <br>
August 30, 2022 <br>
Data Engineer

## Overview

Sparkify analytics team is interested in understanding what songs users are listening to on their music stream app. However, they don't
have an easy way to query their data that resides in a directory of json logs on user acitivity and metadata on the songs.

I've created a Posgres database with tables designed to optimize queries on songplay analysis. I've also built an ETL pipeline using python and SQL
that transfers data from files in two local directories into these tables.

I've defined fact(songplays) and dimension(users, songs, time, artists) tables for a star schema.


### How to run the Pyton scripts


**Steps**

1. Bring the all the files in your root directory.
2. In the command terminal move into the root directory.
3. Run create_tables.py with this command -- python create_tables.py
4. To test if tables have been created open the test.ipynb and run the cells. Be sure to close connection by restarting kernel.
5. If you have inserted any data into the table by way of the etl notebook run the create_tables.py to drop and create fresh empty tables.
6. run etl.py with this command -- python etl.py 
7. Test the tables again with the test notebook. 
8. To start over you can always run -- python create_tables.py

### Files in the repository

- sql_queries.py <br>
  This script contains all SQL queries, create and insert     statements saved in python variables.
  You will not need to run this script but it needs to be in the same directory that create_tables.py is because we will be importing modules 
  from it.

- create_tables.py <br>
    This python script has three purposes.
    1. To connect to posgres and create a database
    2. To drop any tables that were created by before
    3. To create tables that will take in our values
    
- etl.ipynb
    This notebook is for extracting data from the json files, manipulating the data then transferring it to our tables that we created previously. Use this notebook as an iterative process along with the test.ipynb and create_tables.py to develope working pipelines.

- test.ipynb 
    This is a notebook with sql magic commands to test is tables have been created, the fields are proper and quality checks on primary key fields. This notebook is your best friend for testing edge cases.
    
-  etl.py
    This is the actual etl pipeline that processes our song and log files into working pipelines that transfers data into our table for analysis.


### Star Schema Design and ETL pipeline

The schema is designed for the analytics team to get insights on what songs their users are listening to and to improve performance by reducing the number of joins.

The fact table labeled as songplays has fields that are comprised from the primary keys for the outer tables.

The outer tables have been denormalized and have user, song, artist and time information that has been duplicated.
