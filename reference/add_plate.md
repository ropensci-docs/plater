# Read a plater-formatted file and combine it with an existing data frame.

Converts data from `plater` format to a data frame with one well per row
and merges it into an existing data frame by well name.

## Usage

``` r
add_plate(data, file, well_ids_column, sep = ",")
```

## Arguments

- data:

  The data frame to merge the file into. Must contain a column with well
  names.

- file:

  The path of a .csv file formatted as described in
  [`read_plate`](https://docs.ropensci.org/plater/reference/read_plate.md).

- well_ids_column:

  The name of the column in `data` containing the well IDs.

- sep:

  The character used to separate columns in the file (e.g. "," or ";")
  Defaults to ",".

## Value

Returns data as a tibble with as many new columns as plates in `file`.
Empty wells are indicated with NA.

## Details

If data contains more wells than in `file`, NA will be added to the
merged column(s) for those wells. If the file contains more wells than
`data`, those wells will be added to the bottom of the result with NA
for the columns in `data`.

## Examples

``` r
# Part of the data is tidy
file <- system.file("extdata", "example-2-part-A.csv", package = "plater")
data <- read.csv(file)

# Part of the data is plate-shaped
plate_shaped <- system.file("extdata", "example-2-part-B.csv", package = "plater")

# Combine the two
data <- add_plate(
   data = data, 
   file = plate_shaped,
   well_ids_column = "Wells")

# Now data are tidy
head(data)
#> # A tibble: 6 × 5
#>   Wells Killing Drug  Concentration Bacteria
#>   <chr>   <dbl> <chr>         <dbl> <chr>   
#> 1 A01        98 A           100     E. coli 
#> 2 A02        95 A            20     E. coli 
#> 3 A03        92 A             4     E. coli 
#> 4 A04        41 A             0.8   E. coli 
#> 5 A05        17 A             0.16  E. coli 
#> 6 A06         2 A             0.032 E. coli 
```
