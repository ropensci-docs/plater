# Displays the data in the form of a microtiter plate.

Displays the data in the form of a microtiter plate.

## Usage

``` r
view_plate(data, well_ids_column, columns_to_display, plate_size = 96)
```

## Arguments

- data:

  A data frame containing the data

- well_ids_column:

  The name of the column in `data` containing the well IDs.

- columns_to_display:

  A vector of the names of one or more columns you'd like to display.

- plate_size:

  The number of wells in the plate. Must be 6, 12, 24, 48, 96 384,
  or 1536. Default 96.

## Value

A depiction of the data in `columns_to_display` as though laid out on a
microtiter plate with `plate_size` wells.

## Examples

``` r
# Generate some tidy data
data <- data.frame(Wells = paste0(LETTERS[1:3], 0, rep(1:4, each = 3)), 
Species = rep(c("Alien", "Human", "Cat"), 4), 
OxygenProduction = round(rnorm(12), 3))
head(data)
#>   Wells Species OxygenProduction
#> 1   A01   Alien           -1.400
#> 2   B01   Human            0.255
#> 3   C01     Cat           -2.437
#> 4   A02   Alien           -0.006
#> 5   B02   Human            0.622
#> 6   C02     Cat            1.148

# See which wells had cells from which species and the amount of oxygen 
# produced for each well
view_plate(data, "Wells", c("Species", "OxygenProduction"), 12)
#> $Species
#>       1     2     3     4
#> A Alien Alien Alien Alien
#> B Human Human Human Human
#> C   Cat   Cat   Cat   Cat
#> 
#> $OxygenProduction
#>        1      2      3      4
#> A   -1.4 -0.006 -1.822 -0.283
#> B  0.255  0.622 -0.247 -0.554
#> C -2.437  1.148 -0.244  0.629
#> 
```
