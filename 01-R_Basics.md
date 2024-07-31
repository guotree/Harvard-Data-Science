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
	-   If you want to see all the packages that have function called, for example `filter`, you can use double questions marks: `??filter`
- **For-loops**: the grammar is also like C language.
- **Vectorization and functionals**: _vectorization_ is preferred over for-loops
	- _Functionals_ are functions that help us apply the same function to each entry in a vector, matrix, data frame, or list. Here we cover the functional that operates on numeric, logical, and character vectors: `sapply`.