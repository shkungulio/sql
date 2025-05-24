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

Create cars table into the car_dealer schema

``` r
cars_query <- "
  CREATE TABLE IF NOT EXISTS car_dealer.cars (
    car_id SERIAL PRIMARY KEY,
    make VARCHAR(25),
    model VARCHAR(25),
    year INTEGER,
    price NUMERIC(10, 2),
    mileage INTEGER,
    color VARCHAR(25)
  );
"
dbExecute(con, cars_query)
```

    ## NOTICE:  relation "cars" already exists, skipping

    ## [1] 0

Create customers table into the car_dealer schema

``` r
customer_query <- "
  CREATE TABLE IF NOT EXISTS car_dealer.customers (
    customer_id SERIAL PRIMARY KEY,
    first_name VARCHAR(25),
    last_name VARCHAR(25),
    email VARCHAR(50),
    phone CHAR(10),
    address VARCHAR(50),
    city VARCHAR(25),
    state CHAR(2),
    zip_code CHAR(5)
  );
"
dbExecute(con, customer_query)
```

    ## NOTICE:  relation "customers" already exists, skipping

    ## [1] 0
