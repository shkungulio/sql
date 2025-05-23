Car Dealer Database
================
2025-05-23

Create database schema **car_dealer**

``` r
tryCatch({
  # write operation
  schema_query <- "CREATE SCHEMA IF NOT EXISTS car_dealer;"
  dbExecute(con, schema_query)
}, error = function(e) {
  message("Error: ", e$message)
})
```

    ## NOTICE:  schema "car_dealer" already exists, skipping

    ## [1] 0

Create tables into the car_dealer schema

``` r
cars_table_query <- "
  CREATE TABLE IF NOT EXISTS car_dealer.cars (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(50),
    hire_date DATE,
    salary NUMERIC(10, 2)
);
"
dbExecute(con, cars_table_query)
```

    ## NOTICE:  relation "cars" already exists, skipping

    ## [1] 0

``` r
#dbWriteTable(con, cars_table_query)
```
