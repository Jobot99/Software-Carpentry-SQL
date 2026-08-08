# Lesson 4: Calculating New Values
## Keywords/shortcuts 
- ROUND(SUM,N): Will round the result of the SUM to N decimal places.
- AS: Will name the column that the result of the query sum will create (rather than just naming it the sum as default)
- ||: Concatenation operator, will combine the values of two columns.
- UNION: Will combine the results of two complete, seperate queries and return unique values.
- UNION ALL: Is the same as the "UNION" operator except it does NOT eliminate duplicate rows.
- INSTR(X, Y): Will tell you at what location (as a number counting from the first character as 1) string Y is within string X.
- SUBSTR(X, I, L): Will return the actual value from string X, starting at position I, of length L.

## Calculation Within Queries
- You can apply calculations on the fly in the query, for example this query will multiply all results in the reading column by 1.05:
SELECT 1.05 * reading FROM Survey WHERE quant = 'rad';
- You can use all arithmetic operators and common functions on any field, for example, this query will convert from Fahrenheit to Celsius and round to two decimal places:
SELECT taken, round(5 * (reading - 32) / 9, 2) FROM Survey WHERE quant = 'temp';
- Note that the output will name the column as the equation used to generate those values. This is messy, so to name the new column somehting custom, us "as" operator. This query will save the new column as "Celsius":
SELECT taken, round(5 * (reading - 32) / 9, 2) as Celsius FROM Survey WHERE quant = 'temp';

## Concatenation operator
- You can combine values from different columns using the concatenation operator "||", the value in the '' between the concatenation symbols is the deliminator (so just a space here), this query will attach the family name with the personal name in the personal column:
"SELECT personal || ' ' || family FROM Person;
- Note that this will return the concatentaion in a column with the first columns name. To give a new name (such as Full_Name in this case) use the as operator, for example:
SELECT personal || ' ' || family as Full_Name FROM Person;

## TASK
- This query will return all of Valentina Roerich salinity measurements with the values divided by 100:
SELECT taken, round(reading/100, 2) FROM Survey WHERE person = 'roe' AND quant = 'sal';

## Union operators
- The "UNION" operator will combine the results of two complete, seperate queries and return unique values, for example,
SELECT * FROM Person WHERE id = 'dyer' UNION SELECT * FROM Person WHERE id = 'roe'; 
would return the same as:
SELECT * FROM Person WHERE id = 'dyer' OR id = 'roe';
- The "UNION ALL" operator is the same as the "UNION" operator except it does NOT eliminate duplicate rows.

## TASK
- This query will return a consolidated list of salinity measurements in ascending order in which ONLY roe's measurements are corrected as before:
SELECT taken, reading FROM Survey WHERE person != 'roe' AND quant = 'sal' UNION SELECT taken, round(reading / 100, 2) FROM Survey WHERE person = 'roe' AND quant = 'sal' ORDER BY taken ASC;

## Locator functions
- SQlite has functions designed to help locate specific characters or strings within fields.
- The INSTR(X, Y) function will tell you at what location (as a number counting from the first character as 1) string Y is within string X. So for example if you had a column called "Greetings" full of values "Hello" in a table called "Salutations", the query below would return 2:
SELECT INSTR(Greetings, 'e') FROM Salutations;
- The SUBSTR(X, I, L) function will return the actual value from string X, starting at position I, of length L. So below will return "Hell":
SELECT SUBSTR(Greetings, 1, 4) FROM Salutations;

## TASK
- The query below will pull only the MajorSites (dropping the numbering) by creating a substring of the site column which only fills with the characters up to the one before the "-".
SELECT DISTINCT substr(site, 1, instr(site, '-') - 1) AS MajorSite FROM Visited;