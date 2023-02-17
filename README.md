# HOMEWORK

```sh
+----+------+---------+-------------+--------+--------+------------+-------------+
| id | Name | borough | BuildingNum | Street | ZipCode |   Phone    | CuisineType |
+----+------+---------+-------------+--------+--------+------------+-------------+
|    |      |         |             |        |        |            |             |
|    |      |         |             |        |        |            |             |
|    |      |         |             |        |        |            |             |
|    |      |         |             |        |        |            |             |
|    |      |         |             |        |        |            |             |
+----+------+---------+-------------+--------+--------+------------+-------------+

+---------------+----------------+-----------------------+------------------------+--------------+-------+-------+
| idRestaurant  | InspectionDate | ViolationCode         | ViolationDescription   | CriticalFlag | Score | GRADE |
+---------------+----------------+-----------------------+------------------------+--------------+-------+-------+
| PK            | PK             |                       |                        |              |       |       |
| (partition    | (clustering    |                       |                        |              |       |       |
| key)          | key)           |                       |                        |              |       |       |
+---------------+----------------+-----------------------+------------------------+--------------+-------+-------+
```

## question 1: list all restaurants

SELECT \* FROM Restaurant LIMIT 100;

## question 2: list all restaurants names

SELECT Name FROM Restaurant LIMIT 100;

## question 3: Name and borough of restaurant id 41569764.

SELECT Name, borough FROM Restaurant WHERE id = 41569764;

## question 4: Dates and grades of inspections of restaurant id 41569764.

SELECT InspectionDate, GRADE FROM Inspection WHERE idRestaurant = 41569764;

## question 5: Name all restaurants located in BROOKLYN.

In Cassandra, queries that filter on non-primary key columns are not allowed by default, as they can be very slow and inefficient. However, you can add the "ALLOW FILTERING" clause to your query to force Cassandra to execute the query, even if it involves filtering on a non-primary key column. Note that this can cause performance issues, especially if the table is large.

SELECT Name FROM Restaurant WHERE borough = 'BROOKLYN' ALLOW FILTERING;

## question 6: Grades and scores for inspections on the restaurant with id 41569764 (score atleast 10)

SELECT GRADE, Score FROM Inspection WHERE idRestaurant = 41569764 AND Score >= 10 ALLOW FILTERING;
