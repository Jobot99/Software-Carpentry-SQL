# Lesson 2: Sorting and Removing Duplicates
## Keywords/shortcuts
- DISTINCT: Will identify all unique values in a column
- ORDER BY: Will order the output based on the column specified. By default in ascending order, use DESC modifier to order descending.

## Sorting and Removing Duplicates
- To return all the unique values in a column, use distinct, for example "SELECT DISTINCT taken, quant FROM Survey;" will return all unique values in the quant column of the Survey table
- Use "SELECT * FROM person ORDER BY id DESC;" to return everything from the Person table, ordered descending by the id column.
- Note that you can specify ascending using ASC.
- You can sort on several columns at once with the order of the sort commands deciding priority. For example, this command will sort by "taken" first, then by "person" for rows with the same "taken" value: "SELECT taken, person, quant FROM Survey ORDER BY taken ASC, person DESC;"
- Let's use these query commands to investigate which scientists specialised in certain measurements. This will take only rows with unique values in both quant and person columns and order by quant to show who did what: "SELECT DISTINCT quant, person FROM Survey ORDER BY quant ASC;"


## TASK

- This query will select distinct dates from the Visited table:
"SELECT DISTINCT dated FROM visited;"
- This query will display the full names of scientists in the Person table, ordered by family name:
"SELECT DISTINCT personal, family FROM Person ORDER BY family;"