# Read a plater-formatted file and turn it into a tidy data frame.

Converts data from `plater` format to a data frame with one well per row
identified by well name.

## Usage

``` r
read_plate(file, well_ids_column = "Wells", sep = ",")
```

## Arguments

- file:

  The path of a .csv file formatted as described below.

- well_ids_column:

  The name to give the column that will contain the well identifiers.
  Default "Wells".

- sep:

  The character used to separate columns in the file (e.g. "," or ";").
  Defaults to ",".

## Value

Returns a data frame with each well as a row. One column will be named
with `well_ids_column` and contain the well names (A01, A02..). There
will be as many additional columns as layouts in `file`. Empty wells are
omitted.

## `plater` format

The .csv file should be formatted as a microtiter plate. The top-left
most cell contains the name to use for the column representing that
plate. For example, for a 96-well plate, the subsequent wells in the top
row should be labeled 1-12. The subsequent cells in the first column
should be labeled A-H. That is:

|         |       |       |       |         |
|---------|-------|-------|-------|---------|
| ColName | **1** | **2** | **3** | **...** |
| **A**   | A01   | A02   | A03   | ...     |
| **B**   | B01   | B02   | B03   | ...     |
| **...** | ...   | ...   | ...   | ...     |

In this example, the cells within the plate contain the well IDs ("A01",
"A02"), but they may contain arbitrary characters: numbers, letters, or
punctuation. Any cell may also be blank.

Note that Microsoft Excel will sometimes include cells that appear to be
blank in the .csv files it produces, so the files may have spurious
columns or rows outside of the plate, causing errors. To solve this
problem, copy and paste just the cells within the plate to a fresh
worksheet and save it.

## Multiple columns

Multiple columns of information about a plate can be included in a
single file. After the first plate, leave one row blank, and then add
another plate formatted as described above. (The "blank" row should
appear as blank in a spreadsheet editor, but as a row of commas when
viewed as plain text.) As many plates as necessary can be included in a
single file (e.g. data measured, subject, treatment, replicate, etc.).

## Examples

``` r
file_path <- system.file("extdata", "example-1.csv", package = "plater")

# Data are stored in plate-shaped form
data <- read_plate(
   file = file_path,
   well_ids_column = "Wells")

# Now data are tidy
head(data)
#> # A tibble: 6 × 5
#>   Wells Drug  Concentration Bacteria Killing
#>   <chr> <chr>         <dbl> <chr>      <dbl>
#> 1 A01   A           100     E. coli       98
#> 2 A02   A            20     E. coli       95
#> 3 A03   A             4     E. coli       92
#> 4 A04   A             0.8   E. coli       41
#> 5 A05   A             0.16  E. coli       17
#> 6 A06   A             0.032 E. coli        2
```
