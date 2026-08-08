# Lesson 1: Selecting Data
## Keywords/shortcuts
- SELECT: Specifies which columns to pull
- FROM: Specifies which databse to pull from 
- *: shorthand way to refer to ALL columns for querying
- .table: to display all tables in a db
- .schema to display all information in all tables in a db

## Getting Started
- This lesson will use SQLite which which has already been installed from https://www.sqlite.org/
- It also requires this database https://swcarpentry.github.io/sql-novice-survey/files/survey.db
- I will then use sqlite via the terminal in VSCode so I can take .md notes alongside.

## Inspecting the db
- To inspect the list of tables in the db, use .tables 
- To inspect the information in the tables in the db, use .schema (which reports columnName and the dataType)
- We'll change the .mode and .header settings to make the output more readable.

## Selecting data
- We used "SELECT family, personal FROM person;" to pull the family and personal columns from the person table. 
- Note that SQL is case INsensitive, so you can write in whatever case.
- Options for common formatting include: "SELECT personal, family FROM person;" OR "select Personal, Family from PERSON;" (prefer 1st)
- Note queries MUST end with a semi-colon, if missing you will get "...>" indicating SQL is waiting for additional commands.
- Typing "; [enter]" will send the query.

## Data Storage in Databases 
- Note that columns and rows are not stored in any specific order despite always being displayed in a default order.
- You can vary how they are displayed by reordeing your query (so reversing the previous query to "personal, family" will display the data in that order).
- You can also repeat columns, so for example "SELECT id, id, id FROM Person;" will display the same column 3 times.
- A shortcut for all columns is "*", for example "SELECT * FROM Person;" will return all columns from the Person table.

## TASK
1. .schema shows that taken from Visted table is an integer.
2. SELECT name FROM site;