# R Basics

This course includes 4 sections: 

- Section 1: R Basics
- Section 2: Data Wrangling
- Section 3: Programming Basics
- Section 4: Importing Data

These four sections correspond to the first chapter of the [first book](https://rafalab.dfci.harvard.edu/dsbook-part-1/).

I will take notes in the order of the book rather than the order of the video.

## 1. Getting Started

As an undergraduate student taking notes from the online book "Introduction to Data Science - Getting Started with R," here are the key points to consider:

### Why R?

- **Origin**: Developed by statisticians for interactive data analysis, not for general software development like C or Java.
- **Interactivity**: Essential for quick data exploration in data science.
- **Scripting**: Ability to save work as scripts for record-keeping and reproducibility.
- **Differences**: Not conventional like other programming languages; offers unique power in data analysis and visualization.
- **Other** Attractive Features of R
    1. **Free and Open Source**: Accessible to all users.
    2. **Cross-Platform**: Runs on Windows, macOS, UNIX/Linux.
    3. **Seamless Sharing**: Scripts and data objects can be shared across different platforms.
    4. **Active Community**: Large, growing, and supportive with numerous learning resources.
    5. **Extensibility**: Easy to contribute and share new data science methodologies across various disciplines.

### The R Console

- **Function**: Used for interactive data analysis, executing commands as typed.
- **Access**: Can be accessed by starting R on a computer.

### RStudio

- **Role**: Serves as a launching pad for data science projects with an editor, console, and other tools.
- **Panes**: Four main panes for different functionalities (code editor, console, environment/history/connections/tutorial, files/plots/packages/help/viewer/presentation).
- **Key Bindings**: Keyboard shortcuts for efficient task performance, recommended to memorize for common operations.

### Installing R Packages

- **Base R**: Limited functionality; extended by add-ons from developers.
- **CRAN and GitHub**: Sources for packages, with hundreds available.
- **Installation**: Easy installation from within R or RStudio. `install.packages()`
- **Loading Packages**: Use `library()` to load installed packages into R sessions.
- **Dependencies**: Some packages install additional required packages automatically.

## 2. R basic

Motivating Example: **US Gun Murders**
you can load the data through `data(murders)`.

### The Very Basics of R

- **Objects**: Storing values for later use with `<-` for assignment
    - Example: Solving quadratic equations using variables
- **Workspace**: The environment where objects are stored and can be accessed
    - Viewing workspace variables in RStudio's Environment tab
    - Methods to save and load workspaces using `save`, `save.image`, and `load`
- **Prebuilt Functions and Objects**
    - **Prebuilt Functions**
        - Using predefined functions like `sqrt`, `log` for calculations
        - You can get help by using the `help` function like this: `help("log")` or `?log`
    - **Prebuilt Objects**
        - You can see all available prebuilt datasets using `data()`
        - mathematical quantities like `pi` and `Inf`
- **Variable Names** in R:  start with a letter, can’t contain spaces, and avoid conflicts with existing functions or reserved words in the language
- **Comment**: comments start with the symbol `#`

### Data Types in R

Using `class()` to identify the type of an object; The function `str` is useful for finding out more about the structure of an object.

- **Data Frames**
    - Storing datasets in data frames as tables with observations and variables
    - Accessing data frames and their structure using `str()` and `head()`
    - Using `$` to access variables within a data frame
    - Naming and accessing vector entries
- **Vectors**
    - Creating and manipulating vectors with `c()` and accessing elements
    - types: "numeric", "character", "logical", "factor", "integer"
    - Numbers default to the numeric class, even if they are whole numbers. To convert to integers, use `as.integer()` or suffix with `L` (e.g., `1L`).
- **Factor**: Storing categorical data and ordering levels with `factor` and `reorder` (different from character)
- **Lists**
    - Data frames are a special case of _lists_. Lists are useful because you can store any combination of different types. You can create a list using the `list` function like this:

    ```R
    record <- list(name = "John Doe",
                  student_id = 1234,
                  grades = c(95, 82, 91, 97, 93),
                  final_grade = "A")

    record$student_id
    #> [1] 1234
    record[["student_id"]]
    #> [1] 1234
    ```

    - you can extract the components of a list with the accessor `$` or double square brackets (`[[`)
- **Matrices**
    - Defining matrices for matrix algebra operations and converting to data frames
    - entries in matrices have to be all the same type
    - We can define a matrix using the `matrix` function like:

    ```R
    mat <- matrix(1:12, 4, 3)
    mat
    #>      [,1] [,2] [,3]
    #> [1,]    1    5    9
    #> [2,]    2    6   10
    #> [3,]    3    7   11
    #> [4,]    4    8   12
    ```

    - We can access elements in the matrix in a similar manner to numpy
    - We can convert matrices into data frames using the function `as.data.frame`

### More of Vectors

- **names**:

```R
codes <- c(italy = 380, canada = 124, egypt = 818)
codes 
#> italy canada egypt 
#> 380 124 818
names(codes)
#> [1] "italy"  "canada" "egypt"
#another way to assign name
codes <- c(380, 124, 818)
country <- c("italy","canada","egypt")
names(codes) <- country
codes
#>  italy canada  egypt 
#>    380    124    818
```

- Use `seq` for creating vectors generates sequance
- **Subsetting**: We use square brackets to access specific elements of a vector.
- **Coercion**: When an entry does not match the expected, some of the prebuilt R functions try to guess what was meant before throwing an error. `as.numeric`, `as.character`; a special value called an `NA` for “not available”

```R
x <- c(1, "canada", 3)
x
#> [1] "1"      "canada" "3"
class(x)
#> [1] "character"
```

- **Sorting and Ordering**
    - `sort` return the sorted vector in increasing order.
    - `order`  takes a vector as input and returns the vector of indexes that sorts the input vector
    - `rank` For any given vector it returns a vector with the rank of the first entry, second entry, etc., of the input vector.
    - `max` and `min` return the value.
    - `which.max` and `which.min` return the index.
- **Vector arithmetics**:
    - arithmetic operations on vectors occur _element-wise_
    - If we have two vectors of the same length, and we sum them in R, they will be added entry by entry as follows:

$$
\begin{pmatrix}a \\b \\c \\d\end{pmatrix}+\begin{pmatrix}e \\f \\g \\h\end{pmatrix}=\begin{pmatrix}a+e \\b+f \\c+g \\d+h\end{pmatrix}
$$

- if the vectors don’t match in length,  R has recycled the numbers in the short vector
- **Indexing**:
    - we can use logicals to index vectors
        - logical operator: `==`, `!=`, `<>`, `>`, `>=`, `<`, `<=`, `&`, `|`, `!`, `&&`, `||`
        - `&`and `|` are Element-wise Logical operator
        - `&&` and `||` are Vectorized Logical operator
    -  The function `which` tells us which entries of a logical vector are TRUE
    - The function `match` tells us which indexes of a second vector match each of the entries of a first vector
    - If rather than an index we want a logical that tells us whether or not each element of a first vector is in a second, we can use the function `%in%`

### Basic Plots

- Creating scatterplots with `plot`, histograms with `hist`, boxplots with `boxplot`, and image with `image`
- The function `with` Evaluate an **R** expression in an environment constructed from data, possibly modifying (a copy of) the original data.

## 3. Programming Basic

- **Conditional expressions**
    - R use if-else statement (like C language) for flow control
    - `ifelse`  takes three arguments: a logical and two possible answers. If the logical is `TRUE`, the value in the second argument is returned and if `FALSE`, the value in the third argument is returned
- **Defining functions**
    - In general, functions are objects, so we assign them to variable names with `<-`. The function `function` tells R you are about to define a function. The general form of a function definition looks like this:

```R
my_function <- function(VARIABLE_NAME){
    perform operations on VARIABLE_NAME and calculate VALUE
    VALUE
}
```

- **namespace**: it is likely that two packages use the same name for two different functions
    - R will follow a certain order when searching for a function in these _namespaces_. You can see the order by typing `search`
    - You can force the use of a specific namespace by using double colons (`::`) like: `dplyr::filter`, `stats::filter`
    - if we want to use a function in a package without loading the entire package, we can use the double colon as well
    - If you want to see all the packages that have function called, for example `filter`, you can use double questions marks: `??filter`
- **For-loops**: the grammar is also like C language.
- **Vectorization and functionals**: _vectorization_ is preferred over for-loops
    - _Functionals_ are functions that help us apply the same function to each entry in a vector, matrix, data frame, or list. Here we cover the functional that operates on numeric, logical, and character vectors: `sapply`.

## 4. The tidyverse

- **Tidy format** permits the data analyst to focus on more important aspects of the analysis rather than the format of the data
- Refining data frame:
    - `mutate`: **adding columns**;  it takes the data frame as a first argument and the name and values of the variable as a second argument using the convention; **transform variables**, apply the same transformation to several variables by `across`
    - `filter`: row-wise subsetting; it takes the data frame as the first argument and then a conditional statement as the second
    - `select`: column-wise subsetting;  it takes the data frame as a first argument and the column name as the next arguments (or `starts_with`, `where`, `ends_with`, `contains`, `matches`, `num_range`)
- **Pipe**: perform a series of operations by `%>%` or `|>`; the pipe sends the result of the left side of the pipe to be the first argument of the function on the right side of the pipe
- The `summarize` function in **dplyr** provides a way to compute summary statistics
- A common operation in data exploration is to first split data into groups and then compute summaries for each group `group_by`
- We can extract varialbes with `pull`
- With `arrange` we get to decide which column to sort by (also for nested sorting)
-  The function `top_n` takes a data frame as it’s first argument, the number of rows to show in the second, and the variable to filter by in the third. if the third argument is left blank, `top_n` filters by the last column.
- **“tibble”**, is a special kind of data frame, we can transform a data frame into a tibble by `as_tibble`
    - Tibbles display better than data frame
    - Tibbles can have complex entries (even functions)
    - Tibbles can be grouped
    - creating tibble;

```R
grades_t <- tibble(names = c("John", "Juan", "Jean", "Yao"), 
                     exam_1 = c(95, 80, 90, 85), 
                     exam_2 = c(90, 85, 85, 90))
grades_d <- data.frame(names = c("John", "Juan", "Jean", "Yao"), 
                     exam_1 = c(95, 80, 90, 85), 
                     exam_2 = c(90, 85, 85, 90))
as_tibble(grades_d) |> class()
#> [1] "tbl_df"     "tbl"        "data.frame"
```

- **Placeholder**: if we want to pass it as argument to the right-hand side function that is not the first, we should use placeholder.
    - For `|>` pipe the placeholder operator is `_`
    - for the `%>%` pipe the placeholder is `.`
- **purrr** package:  includes functions similar to `sapply` but that better interact with other tidyverse functions
    -  `map` works very similar to `sapply` but always, without exception, returns a list
    - `map_dbl` always returns a vector of numeric values
    - `map_df`, always returns a tibble data frame
- **Tidyverse conditionals**:
    - The `case_when` function is useful for vectorizing conditional statements. It is similar to `ifelse` but can output any number of values

    ```R
    x <- c(-2, -1, 0, 1, 2)
    case_when(x < 0 ~ "Negative", 
              x > 0 ~ "Positive", 
              TRUE  ~ "Zero")
    #> [1] "Negative" "Negative" "Zero"     "Positive" "Positive"
    ```

    - `between` function determines if a value falls inside an interval.

## 5. data.table

- **data.table** is more efficient and can handle larger datasets more effectively.
- **data.table** is a separate package that needs to be installed: `library(data.frame)`
- **Refining data tables**:
    - `as.data.table` can convert the data frame into a data.table
    - **Column-wise subsetting**:

    ```R
    murders_dt[, c("state", "region")] 
    murders_dt[, .(state, region)] 
    ```

  - **Adding or transformin variables**: The **data.table** `:=` function permits us update the variable by reference

  ```R
  murders_dt[, rate := total / population * 100000]
  murders_dt[, ":="(rate = total / population * 100000, rank = rank(population))]
  ```

    - **Reference versus copy**
        - The **data.table** package is designed to avoid wasting memory: In `y <- x` , `y` is referencing `x`; In `y <- copy(x)`, `y` is the actual copy of `x`
        - the function `as.data.table` creates a copy of the data frame being converted. However, if working with a large data frames it is helpful to avoid this by using `setDT`:
    - **Row-wise subsetting**: `murders_dt[rate <= 0.7, .(state, rate)]` has the same function as `murders |> filter(rate <= 0.7) |> select(state, rate)`
- **Summarizing data**: `s <- heights |> summarize(avg = mean(height), sd = sd(height))` has the same function as `s <- heights_dt[, .(avg = mean(height), sd = sd(height))]`
    - We simply add the `by` argument to split the data into groups based on the values in categorical variable `heights_dt[, .(avg = mean(height), sd = sd(height)), by = sex]`
- **Sorting**: `murders_dt[order(population)]`

## 6. Importing data

- highly recommend only using _relative paths_ in your code
- `getwd` get the full path of your working directory; `setwd` change your working directory; `file.path` function combines characters to form a complete path; `file.copy` copy the file with full path;
- **File types**: text files and binary files
    - The most common delimiters are comma (`,`), semicolon (`;`), space (` `), and tab (a preset number of spaces or `\t`);
    - You can look at any number of lines from within R using the `readLines` function which can reveal what the file's delimited is.
    - R’s `readBin` function can process any binary file
    - **Encoding**: ASCII, UTF-8, UTF-16, and UTF-32; RStudio typically uses **UTF-8** as its default
- **Parsers**: importing functions are most in **readr**, **readxl** and **data.table** packages.
    - **Basic R**: `read.csv`, `read.table` and `read.delim`; `scan` is another flexible function
    - **readr**: it is part of the **tidyverse**; Its parsers permit us to specify an encoding. It also includes a function `guess_encoding` that tries to guess the encoding;  we can specify it through the `locale` argument
    - **readxl**: provides functions to read-in Microsoft Excel formats; These functions read the first sheet by default; The `excel_sheets` function gives us the names of all the sheets in an Excel file. These names can then be passed to the `sheet` argument in these functions.
    - **data.table**: provides the `fread` function for large datasets which automatically detects the format of the input (even gzip and zip)

| Function     | Format                                          | Typical suffix |
| ------------ | ----------------------------------------------- | -------------- |
| `read_table` | white space separated values                    | txt            |
| `read_csv`   | comma separated values                          | csv            |
| `read_csv2`  | semicolon separated values                      | csv            |
| `read_tsv`   | tab delimited separated values                  | tsv            |
| `read_delim` | general text file format, must define delimiter | txt            |

| Function   | Format                 | Typical suffix |
| ---------- | ---------------------- | -------------- |
| read_excel | auto detect the format | xls, xlsx      |
| read_xls   | original format        | xls            |
| read_xlsx  | new format             | xlsx           |

- **Downloading files**: Most parsers can read these files on the internet through url directly;
    - you can use the `download.file` function to have a local copy of the file;
    - `tempdir` creates a directory with a random name that is very likely to be unique;
    -  `tempfile` creates a character string, not a file, that is likely to be a unique filename
- **Organizing data with spreadsheets**:
    - avoid Microsoft Excel format
    - **Be Consistent**
    - **Choose Good Names for Things**: don't use space and symbols; stick to letters and numbers
    - **Write Dates as YYYY-MM-DD**
    - **No Empty Cells**
    - **Put Just One Thing in a Cell**
    - **Make It a Rectangle**
    - **Create a Data Dictionary**
    - **No Calculations in the Raw Data Files**
    - **Do Not Use Font Color or Highlighting as Data**
    - **Make Backups**
    - **Use Data Validation to Avoid Errors**
    - **Save the Data as Text Files**