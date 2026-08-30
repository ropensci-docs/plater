# Summary

plater is an R \[@R\] package that makes it easy to work with data from
experiments performed in microtiter plates.

Many scientific instruments (such as plate readers and qPCR machines)
produce data in tabular form that mimics a microtiter plate: each cell
corresponds to a well as physically laid out on the plate. For
experiments like this, it’s often easiest to keep records of what was
what (control vs. treatment, concentration, sample type, etc.) in a
similar plate layout form.

plater defines a simple, plate-shaped file format for data storage, so
it’s easy to remember the experimental design, and provides functions to
seamlessly convert between that format and a tidy \[@tidy\] data frame
that’s optimal for analysis. When the instrument produces data that’s
already tidy, plater helps combine that data with plate-shaped
experimental metadata. Once the data is tidy, it’s sometimes useful to
look back at it in plate shape, so plater makes that easy, too.

# References
