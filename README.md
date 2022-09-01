# Database Star Schema and ETL Pipeline for Sparkify's Analytics Team

Esteban Zuniga <br>
August 30, 2022 <br>
Data Engineer

## Overview

Sparkify analytics team is interested in understanding what songs users are listening to on their music stream app. However, they don't
have an easy way to query their data that resides in a directory of json logs on user acitivity and metadata on the songs.

I've created a Posgres database with tables designed to optimize queries on songplay analysis. I've also built an ETL pipeline using python and SQL
that transfers data from files in two local directories into these tables.

I've defined fact(songplays) and dimension(users, songs, time, artistis) tables for a star schema.


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
  This script contains all SQL queries, create and insert statements saved in python variables.
  You will not need to run this script but it needs to be in the same directory that create_tables.py is because we will be importing modules 
  from it.
