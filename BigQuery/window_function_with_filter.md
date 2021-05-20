# Window function with a filter

normally, if you want to get a max value for every row, you can do:

```sql
SELECT 
    MAX(some_value) OVER (partition by id, column_2) AS column_new
FROM 
    (SELECT 
        id,
        column_2,
        column_3,
        some_value
    FROM TableX
)
```

However, if you want do a filter on the MAX... value (E.g. filter for `column_3` not null in the above), you'll need 
something along the lines of:

```sql
SELECT 
    MAX(IF(column_3 IS NOT NULL, some_value, NULL)) OVER (partition by id, column_2) AS column_new
FROM 
    (SELECT 
        id,
        column_2,
        column_3,
        some_value
    FROM TableX
)
```

courtesy of https://stackoverflow.com/questions/47514566/filter-partitions-in-window-computing-event-recency-in-bigquery