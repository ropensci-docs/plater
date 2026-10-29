# Read multiple plater-formatted files and combine result into one data frame.

A wrapper around `read_plate` that handles multiple plates and combines
them all into a single data frame.

## Usage

``` r
read_plates(files, plate_names = NULL, well_ids_column = "Wells", sep = ",")
```

## Arguments

- files:

  A character vector with the paths of one or more plater-formatted .csv
  files.

- plate_names:

  A character vector the same length as `files` with the names to give
  the individual plates in the resulting data frame. Defaults to the
  file names (stripped of path and .csv).

- well_ids_column:

  The name to give the column that will contain the well identifiers.
  Default "Wells".

- sep:

  The character used to separate columns in the file (e.g. "," or ";").
  Defaults to ",".

## Value

Returns a data frame like that returned by `read_plate`, containing the
data from all of the plates. The plates will be identified with a column
called "Plate" containing the names given in `plate_names`.

## Examples

``` r
# Combine multiple files into one tidy data frame
file1 <- system.file("extdata", "example-1.csv", package = "plater")
file2 <- system.file("extdata", "more-bacteria.csv", package = "plater")

# Data are stored in plate-shaped form
data <- read_plates(
   files = c(file1, file2),
   plate_names = c("Experiment 1", "Experiment 2"),
   well_ids_column = "Wells")

# Data from both plates are tidy and in the same data frame
head(data)
#> # A tibble: 6 × 6
#>   Plate        Wells Drug  Concentration Bacteria Killing
#>   <chr>        <chr> <chr>         <dbl> <chr>      <dbl>
#> 1 Experiment 1 A01   A           100     E. coli       98
#> 2 Experiment 1 A02   A            20     E. coli       95
#> 3 Experiment 1 A03   A             4     E. coli       92
#> 4 Experiment 1 A04   A             0.8   E. coli       41
#> 5 Experiment 1 A05   A             0.16  E. coli       17
#> 6 Experiment 1 A06   A             0.032 E. coli        2
```
