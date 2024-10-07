# Wrangling

## 0. Importing data

See in [R basics](01-R_Basics)

## 1. Reshaping data

### tidyverse

`pivot_longer`:  convert wide data into long (tidy) data

`pivot_wider`:  convert long (tidy) data into wide data

`separate_wider_delim`, `separate_wider_position`, `separate_wider_regex`, `separate`: separate these columns into two or more

`unite`: paste together multiple columns into one

`clean_names`: Resulting names are unique and consist only of the _ character, numbers, and letters.

`column_to_rownames`: convert an explicit column to row name.

`row_to_names`: Elevate a row to be the column names of a data.frame.

`get_dupes`: For hunting duplicate records during data cleaning. Specify the data.frame and the variable combination to search for duplicates and get back the duplicated rows.

### data.table

`melt`: convert wide data into long data.

`dcast`: convert long data into wide data.

`tstrsplit`: This is a convenient wrapper function to split a column using `strsplit` and assign the transposed result to individual columns.


## 3. Joining tables

### Joins

`left_join`, `right_join`, `inner_join`, `full_join`, `semi_join`, `anti_join`

### Binding

**Binding columns**: `bind_cols`, `cbind` (`cbind` can create different types of objects, while `bind_cols` always produces a data frame.)

**Binding by rows**: `bind_rows`

### Set operators

`intersect`, `union`, `setdiff`, `setequal`

`dplyr::intersect`, `dplyr::union`, `dplyr::setdiff`, `dplyr::setequal`

### Joining with data.table

`merge` uses the the logical arguments `all` (full join), `all.x` (left join), and `all.y` (right join).