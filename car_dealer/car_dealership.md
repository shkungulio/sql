Car Dealership Database
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

    ## [1] 0

Create employees table into the car_dealer schema

``` r
employee_query <- "
  CREATE TABLE IF NOT EXISTS car_dealer.employees (
    employee_id SERIAL PRIMARY KEY,
    first_name VARCHAR(25),
    last_name VARCHAR(25),
    role VARCHAR(25)
  );
"
dbExecute(con, employee_query)
```

    ## [1] 0

Create sales table into the car_dealer schema

``` r
sale_query <- "
  CREATE TABLE IF NOT EXISTS car_dealer.sales (
    sale_id SERIAL PRIMARY KEY,
    car_id INT, -- car id from Cars table (Foreign Key)
    customer_id INT, -- customer id from Customers table (Foreign Key)
    sale_date DATE, -- the date when the car sale was made
    sale_price DECIMAL(10, 2), -- car sale price
    FOREIGN KEY (car_id) REFERENCES car_dealer.cars(car_id),
    FOREIGN KEY (customer_id) REFERENCES car_dealer.customers(customer_id)
  );
"
dbExecute(con, sale_query)
```

    ## [1] 0
