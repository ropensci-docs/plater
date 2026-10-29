# Check whether a file is in plater format.

Runs the provided file through a number of diagnostics to determine
whether it is a valid plater format file and displays information about
any deficiencies found.

## Usage

``` r
check_plater_format(file, sep = ",")
```

## Arguments

- file:

  The path of the file to check.

- sep:

  The character used to separate columns in the file (e.g. "," or ";").
  Defaults to ",".

## Value

Displays a number of messages as it checks the file. Will stop with a
descriptive error message if the file is not formatted correctly.

## Examples

``` r
file_path <- system.file("extdata", "example-1.csv", package = "plater")

data <- check_plater_format(file_path)
#> * Checking file path ... 
#> good!
#> * Checking that file is not empty ... 
#> good!
#> * Checking valid column labels ... 
#> good!
#> * Checking file length and number of plate layouts ... 
#> good!
#> * Checking plate dimensions and row labels ... 
#> good!
#> Success!
```
