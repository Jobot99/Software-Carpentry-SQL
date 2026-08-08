# Lesson 3: Filtering
## Keywords/shortcuts
- WHERE: Applies a filter to query using boolean operators such as =, <, > etc.
- AND: Can be used to apply multiple filters sequentially
- OR: Can be used to apply multiple filters in parallel

## WHERE command
- Filtering is one of the most powerful uses of SQL and can be done using the "WHERE" command, for example:
"SELECT * FROM Visited WHERE site = 'DR-1';" will pull everything from the Visited table where the value in the site column is DR-1.
- You can use many boolean operators to filter data with AND. For example, this query will pull everything from the Visited table where site = DR-1 AND dated is before (lower than) 1930-01-01: "SELECT * FROM Visited WHERE site = 'DR-1' AND dated < '1930-01-01';"
- You can also combine using OR. For example, this query will pull all columns from the Survey table where person = lake OR roe: "SELECT * FROM Survey WHERE person = 'lake' OR person = 'roe';"
- Note, you must order the AND/OR commands carefully as this will impact the pulled data. Use parentheses to group together commands, for example: "SELECT * FROM Survey WHERE quant = 'sal' AND (person = 'lake' OR person = 'roe');"
- You can combine all of these with the DISTINCT command. For example, this query will return distinct person and quant values from the Survey table where person = lake or roe (so in other words, will show you each unique quant value for lake and roe)

## IN command
- You can use the IN command to determine whether a value is in a specific set. For example, this query will select all columns from Survey where lake or roe exist in the person column: 
"SELECT * FROM Survey WHERE person IN ('lake', 'roe');"
- 

## LIKE command
- The LIKE command allows you to search for partial matches and you can use "%" as a wildcard where the desired values may vary. For example "SELECT * FROM Visited WHERE site LIKE 'DR%';" will return everything from the Visted table where values in site begin with "DR". 
- Note, the wildcard can go anywhere, so "%DR" woul return values ENDING in DR and "D%R" would return values starting with D and ending with R. Wildcards can be as long as needed, for example 'alpha' LIKE 'a%p%' is TRUE because the first wildcar covers the "l" and the second covers "ha"

## TASK
- The following query is wrong because the AND command is needed rather than the OR command.
SELECT * FROM Site WHERE (lat > -48) OR (lat < 48);
- The following query will select all records from Survey with salinity values outside the range 0.0-1.0:
SELECT * FROM Survey WHERE quant = 'sal' AND (reading < 0.0 OR reading > 1.0);