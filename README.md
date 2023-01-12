# Crowdfunding-ETL

## Overview of Crowdfunding-ETL
We were tasked with helping Britta extract, transform, and load the crowdfunding data in order to get email lists for all backers and contacts with live campaigns to contact with an update on their campaigns. In order to get these email lists we will have to use python, pandas, jupyter notebook, and pgAdmin to perform the ETL Process and SQL Analysis.

## Process of Crowdfunding-ETL
**Extract Data**

Created Extract-Transform_final_code.ipynb in [Jupyter Notebook file (Extract-Transform_final_code.ipynb)](https://github.com/trevoriwen/Crowdfunding-ETL/blob/56d2d206a520f660b85603cb32c571f507d6d945/Extract-Transform_final_code.ipynb) in order to extract the information provided in backer_info.csv to a new data frame.
1. Download and import backer_info into pandas DataFrame.
2. Use regular expressions to to extract "backer_id", "cf_id", "name", and "email" into new columns into the DataFrame.
3. Create a new DataFrame with "backer_id", "cf_id", "name", and "email" columns and export to backers_data.csv for transformation.

**Transform and Clean Data**

Using the new data frame we transformed and cleaned the data using [Jupyter Notebook file (Extract-Transform_final_code.ipynb)](https://github.com/trevoriwen/Crowdfunding-ETL/blob/56d2d206a520f660b85603cb32c571f507d6d945/Extract-Transform_final_code.ipynb) and export into  [backers.csv](https://github.com/trevoriwen/Crowdfunding-ETL/blob/56d2d206a520f660b85603cb32c571f507d6d945/backers.csv).
1. Update "cf_id" data type to int. 
2. Split name column into the first_name and last_name columns and drop the name column.
3. Reorder columns to "backer_id", "cf_id", "first_name", "last_name" and "email", then export cleaned data into [backers.csv](https://github.com/trevoriwen/Crowdfunding-ETL/blob/56d2d206a520f660b85603cb32c571f507d6d945/backers.csv).

**ERD, Table Schema, and Load Data**

Created a ERD with backers table, create backers table using pgAdmin, and import data into backers table in the crowdfunding_db database.
1. Create ERD with newly added backers table using Quick DBD. Assign backer_id as primary key and cf_id as foreign key with a many to one relationship to the campaign cf_id. Image of ERD saved as [crowdfunding_db_relationships.png](https://github.com/trevoriwen/Crowdfunding-ETL/blob/56d2d206a520f660b85603cb32c571f507d6d945/Database_Setup/crowdfunding_db_relationships.PNG).
2. Schema exported from Quick DBD as [crowdfunding_db_schema.sql](https://github.com/trevoriwen/Crowdfunding-ETL/blob/56d2d206a520f660b85603cb32c571f507d6d945/Database_Setup/crowdfunding_db_schema.sql) and used to create and alter backers table in the crowdfunding_db database. Then check the table in pgAdmin.

**SQL Analysis**

Run queries to show count of backers by cf_id for live campaigns, as well as queries for the campaign contacts and campaign backers email lists. Queries saved as [crowdfunding_SQL_Analysis.sql](https://github.com/trevoriwen/Crowdfunding-ETL/blob/56d2d206a520f660b85603cb32c571f507d6d945/crowdfunding_SQL_Analysis.sql).
1. Write query to return number of backer_counts using campaigns.
2. Confirm query by writing with backers table.
3. Created email contact list with first name, last name, and email of each contact along with the remaining goal amount for live campaigns. Exported and saved as [email_contacts_remaining_goal_amount.csv](https://github.com/trevoriwen/Crowdfunding-ETL/blob/56d2d206a520f660b85603cb32c571f507d6d945/email_contacts_remaining_goal_amount.csv).
4. Created email backers list with the first name, last name and email of each backer along with the cf_id, company, description, end date, and what's remaining on the goal amount for the campaign they have already backed for live campaigns. Exported and saved as [email_backers_remaining_goal_amount.csv](https://github.com/trevoriwen/Crowdfunding-ETL/blob/56d2d206a520f660b85603cb32c571f507d6d945/email_backers_remaining_goal_amount.csv).
