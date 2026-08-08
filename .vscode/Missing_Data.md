# Lesson 5: Missing Data
## Keywords/shortcuts


## Null Values
- By default SQLite does not disiplay null values in output, we'll use .nullvalue to assign a visible null value.
- By running SELECT * FROM Visited; we can see a null value for dated with id 752. 
- You will notice that if you try to search based on the dated column, that row will never appear, as a null value cannot be determined to be higher than, lower than or equal to anything else.
- You can use the special test function "IS NULL" to pull just null results, for example: "SELECT * FROM Visited WHERE dated IS NULL;"
- Or the inverse "IS NOT NULL":  "SELECT * FROM Visited WHERE dated IS NOT NULL;"
- Note that this can omit whole rows where just the value in the column you are filtering on contains a null. You need to explicitly include IS NULL to avoid this, for example:
"SELECT * FROM Survey WHERE quant = 'sal' AND (person != 'lake' OR person IS NULL);" will include every row from every record that doesn't have lake as the person, INCLUDING where the person is null.

## TASK
- The query below will sort the records in Visited by date in ascending order, omitting null dates:
SELECT * FROM Visited WHERE dated IS NOT NULL ORDER BY dated ASC;