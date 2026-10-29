# Changelog

## plater 1.0.5

CRAN release: 2024-10-25

- Add package to plater.R per CRAN request. Thanks to Maëlle Salmon
  [@maelle](https://github.com/maelle)

## plater 1.0.4

CRAN release: 2022-02-11

- Add an option to allow non-comma delimiters
  ([\#27](https://github.com/ropensci/plater/issues/27)). Thanks to
  Yorgos Bos [@superpuffin](https://github.com/superpuffin)

## plater 1.0.3

CRAN release: 2021-01-06

- Change
  [`add_plate()`](https://docs.ropensci.org/plater/reference/add_plate.md)
  to return a tibble rather than trying to preserve initial class
- Remove use of deprecated `select_` function

## plater 1.0.2

CRAN release: 2020-03-24

- Changes to tests to comply with new CRAN policy on
  `data.frame(..., stringsAsFactors = FALSE)`
- Add support for 6- and 1536-well plates
- Change behavior of add_plate so that when the plate layout contains
  more wells than the input data frame, those wells are appended to the
  end of the data frame instead of erroring.

## plater 1.0.1

CRAN release: 2017-06-26

- Eliminate warnings from readLines on files without EOF (Mac issue)
- Fix issue with numeric formatting in mixed numeric/character layouts
- Fix issue with grouped tibbles and view_plate

## plater 1.0.0 (5 Oct 2016)

CRAN release: 2016-10-06

- Changes in response to rOpenSci reviewers
- Reorder arguments of
  [`add_plate()`](https://docs.ropensci.org/plater/reference/add_plate.md)
  for better pipelining
- add
  [`check_plater_format()`](https://docs.ropensci.org/plater/reference/check_plater_format.md)
  to help with preparing files
- rename all lowercase

## plateR 0.2.1

- Reorganize parameters for consistency
- Add defaults for parameters
- Add
  [`read_plates()`](https://docs.ropensci.org/plater/reference/read_plates.md)

## plateR 0.2

- Introduce new data format with multiple plate layouts per .csv file
  (replacing multiple files at once)

## plateR 0.1

- Add support for reading multiple files at once
