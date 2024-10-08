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


## 2. Joining tables

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


## 3. Parsing dates and times

### lubridate

extract values: `year`, `month` and `day`

convert strings into dates: `ymd`,`ydm`, `mdy`, `myd`, `dmy`, `dym`, `yq`, `ym`, `my`

get the current time: `now`

create a date object: `make_date`

 _round_ dates to nearest year, quarter, month, week, day, hour, minutes, or seconds: `round_date`

### data.table

`second`, `minute`, `hour`, `yday`, `wday`, `week`, `isoweek` and `quarter`

`IDate` and `ITime`

## 4. Locales

access or change the current locale settings: `Sys.getlocale` and `Sys.setlocale`

- `LC_ALL`:  all locale categories
- `LC_COLLATE`: for string collation
- `LC_TIME`: date and time formatting
- `LC_MONETARY`: currency formatting.
- `LC_MESSAGES`: system message translations.
- `LC_NUMERIC`: number formatting.

`locale()` in **readr**  can change the current locale from within R

## 5. Extracting data from the web

### Scraping HTML

**rvest** package: import the webpage into R. `read_html`, `html_text`, `html_nodes`, `html_table`

### JSON

**jsonlite** package: `fromJSON` read JSON file also you can choose **rjson**

### Data APIs

**httr2** package: `request`, `req_perform`, `resp_body_string`, `read_csv`

## 6.  String processing

| stringr           | Task       | Description                                                                                      | Base R                         |
| ----------------- | ---------- | ------------------------------------------------------------------------------------------------ | ------------------------------ |
| `str_detect`      | Detect     | Is the pattern in the string?                                                                    | `grepl`                        |
| `str_which`       | Detect     | Returns the index of entries that contain the pattern.                                           | `grep`                         |
| `str_subset`      | Detect     | Returns the subset of strings that contain the pattern.                                          | `grep` with `value = TRUE`     |
| `str_locate`      | Locate     | Returns positions of first occurrence of the pattern in a string.                                | `regexpr`                      |
| `str_locate_all`  | Locate     | Returns position of all occurrences of the pattern in a string.                                  | `gregexpr`                     |
| `str_view`        | Locate     | Show the first part of the string that matches the pattern.                                      |                                |
| `str_view_all`    | Locate     | Show all the parts of the string that match the pattern.                                         |                                |
| `str_extract`     | Extract    | Extract the first part of the string that matches the pattern.                                   |                                |
| `str_extract_all` | Extract    | Extract all parts of the string that match the pattern.                                          |                                |
| `str_match`       | Extract    | Extract first part of the string that matches the pattern and the groups defined by the pattern. |                                |
| `str_match_all`   | Extract    | Extract all parts of the string that match the pattern and the groups defined by the pattern.    |                                |
| `str_sub`         | Extract    | Extract a substring.                                                                             | `substring`                    |
| `str_split`       | Extract    | Split a string into a list with parts separated by a pattern.                                    | `strsplit`                     |
| `str_split_fixed` | Extract    | Split a string into a matrix with a fixed number of parts separated by a pattern.                | `strsplit` with `fixed = TRUE` |
| `str_count`       | Describe   | Count number of times a pattern appears in a string.                                             |                                |
| `str_length`      | Describe   | Number of character in string.                                                                   | `nchar`                        |
| `str_replace`     | Replace    | Replace first part of a string matching a pattern with another.                                  |                                |
| `str_replace_all` | Replace    | Replace all parts of a string matching a pattern with another.                                   | `gsub`                         |
| `str_to_upper`    | Replace    | Change all characters to upper case.                                                             | `toupper`                      |
| `str_to_lower`    | Replace    | Change all characters to lower case.                                                             | `tolower`                      |
| `str_to_title`    | Replace    | Change first character of each word to upper and rest to lower case.                             |                                |
| `str_replace_na`  | Replace    | Replace all `NA`s with a new value.                                                              |                                |
| `str_trim`        | Replace    | Remove white space from start and end of string.                                                 |                                |
| `str_c`           | Manipulate | Join multiple strings.                                                                           | `paste0`                       |
| `str_conv`        | Manipulate | Change the encoding of the string.                                                               |                                |
| `str_sort`        | Manipulate | Sort the vector in alphabetical order.                                                           | `sort`                         |
| `str_order`       | Manipulate | Provide index needed to order the vector in alphabetical order.                                  | `order`                        |
| `str_trunc`       | Manipulate | Truncate a string to a fixed size.                                                               |                                |
| `str_pad`         | Manipulate | Add white space to string to make it a fixed size.                                               |                                |
| `str_dup`         | Manipulate | Repeat a string.                                                                                 | `rep` then `paste`             |
| `str_wrap`        | Manipulate | Wrap things into formatted paragraphs.                                                           |                                |
| `str_interp`      | Manipulate | String interpolation.                                                                            | `sprintf`                      |

`suppressWarnings`: avoid the warning message

`cat` lets us see what the string actually looks like

### Escaping characters

Characters are typically escaped by placing a backslash `\` before them.

### Regular expressions

A regular expression (regex) is a way to describe specific patterns of characters of text. They can be used to determine if a given string matches the pattern. [Tutorial](https://rstudio.github.io/cheatsheets/strings.pdf)

**Strings are a regex**

**Special characters**

- `\d` means any digit: 0, 1, 2, 3, 4, 5, 6, 7, 8, 9.
- `|` means _or_ in a pattern
- `\w` which stands for _word character_ and it matches any letter, number, or underscore.

**Character classes**

- Character classes are used to define a series of characters that can be matched. We define character classes with square brackets `[]`
- we can define lower case letters as `[a-z]`, upper case letters as `[A-Z]`, and `[a-zA-Z]` as both.
- `\w` is equivalent to `[a-zA-Z0-9_]`.

**Anchors**:  let us define patterns that must start or end at a specific place

- The two most common anchors are `^` and `$` which represent the beginning and end of a string

**Bounded quantifiers**: following the pattern with curly brackets containing the number of times the previous entry can be repeated

**White space**: `\s` represents white space

**Unbounded quantifiers**: `*`, `?`, `+` 

| Usage        | Unbounded quantifiers |
| ------------ | :-------------------: |
| none or once |          `?`          |
| once or more |          `+`          |
| none or more |          `*`          |

**Not**: 

- we can use the `^` symbol but only **inside** square brackets. Remember that outside the square bracket `^` means the start of the string.
- `\D` means anything other than a digit
- `\S` means anything except a space

**Groups**: _Groups_ are a powerful aspect of regex that permits the extraction of values. Groups are defined using parentheses. They don’t affect the pattern matching per se. Instead, it permits tools to identify specific parts of the pattern so we can extract them.

**Search and replace using groups**: The regex special character for the `i`-th group is `\\i`

**Lookarounds**: Lookarounds provide a way to ask for one or more conditions to be satisfied _without moving the search forward_ or matching it.

 - lookahead `(?=pattern)`
 - lookbehind `(?<=pattern)`
 - negative lookahead `(?!pattern)`
 -  negative lookbehind `(?<!pattern)`

### Trimming

`str_trim`: remove the space at the start or end of the string

### Case conversion

- `str_to_upper()` converts to upper case.
- `str_to_lower()` converts to lower case.
- `str_to_title()` converts to title case, where only the first letter of each word is capitalized.
- `str_to_sentence()` convert to sentence case, where only the first letter of sentence is capitalized.

