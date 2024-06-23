# R

### Notes
- Use . for naming or Camel Case (ex. numberOfMiles) for variable names. Snake Case (ex. number_of_miles) is considered bad style
- R rewrites objects without asking for permission or issuing a warning if you redefine it
- R is case sensitive

***Literal Values*** by appending <code>L</code> to a number, we're instructing R to treat that number as an Integer and not merely a Numeric

- Exponentiation (<code>^</code>): This operator raises a number to a specified power. In mathematical terms, x ^ n means multiplying the number x by itself n times. For instance, 2 ^ 3 translates to 2 * 2 * 2.

- Integer Division (<code>%/%</code>): The operation x %/% n determines how many times the number n can be found within x without exceeding it. For example, 17L %/% 5L results in 3, indicating that 5 can be found three times in 17 without surpassing it.

- Modulo (<code>%%</code>): This operator returns the remainder after an integer division. Continuing the above example, the remainder when 17 is divided by 5 is 2. Hence, 17 %% 5 produces 2.

### Logical Operators
- Logical NOT (<code>!</code>)
- Logical AND (<code>&&</code>)
- Logical OR (<code>||</code>)

# Packages

- to install a package, use <code>install.packages("PACKAGENAME")</code>
- after you install it, you need to open or "load" the package to use it. this is done with the <code>library(PACKAGENAME)</code> function
- if you don't know what you need, go to the ***cran.r-project.org*** website > packages BUT a better approach is to go to the ***CRAN Task Views*** instead bc it lets you browse packages by subject area. can also go to ***r-bloggers.com*** to find out the cool shit about what is fashionable now and in previous years

## tidyverse
install.packages("readr")
- ***Number of Rows***: Use the <code>nrow()</code> function which returns an integer number.
- ***Number of Columns***: Use the <code>ncol()</code> function which returns an integer number.
- ***Column Names***: Use the <code>colnames()</code> function which returns the names of the columns.

## Package: ggplot2
This function receives the following parameters:
- The dataset itself: (optionally, we can specify this parameter with <code>data = name_of_dataset</code> or just the name of the dataset directly)
- What each ***dot*** represents on the horizontal (x) axis (parameter <code>x = column_x_on_the_dataset</code>), and on the vertical (y) axis (parameter <code>y = column_y_on_the_dataset</code>). We call this the "aesthetic mappings", and we use <code>aes()</code> to accommodate the x and y parameters. Think of it like telling R that the data in your <code>x_values</code> column in the dataset should go on the x-axis, and the data in your <code>y_values</code> column in the dataset should go on the y-axis.
- We also need to specify the type of plot we want to build (here we use <code>geom_point()</code> for scatter plot

Example if we wanted to show the minimum salary (salary_min) of different job posts:
```
ggplot(data = monster_jobs_clean, 
       aes(x = job_id, y = salary_min)) +
  geom_point()
```
***YOU DO NOT NEED TO PUT 'data ='***

Example where4 you use color for the job_type
```
ggplot(monster_jobs_clean,
       aes(x = job_id, y = salary_min,
      color = job_type)) + 
  geom_point()
```

# RStudio
***Keyboard Shortcuts for RStudio*** 
- <code>TAB</code> will give you code completion
- <code>CTRL</code> + <code>L</code> will clear the console
- <code>Alt</code> + <code>-</code> for typing the assignment operator <code><-</code>
- help("whatever_you_need_help_with") Ex. help(is.complex)
    - can also use ?is.helpThing() Ex. ?is.complex()
- <code>ls()</code> lists all the visible objects in your environment

- If we want to remove selected objects from the workspace (in the environment tab), select the grid view from the dropdown menu
- if you want to change the appearance go to Tools> Global options > appearance
### Most common packages
Tidyverse is a collection of packages needed for data analysis.

These are the most common packages:
- <code>reader</code>, for data import.
- <code>ggplot2</code>, for data visualization.
- <code>dplyr</code>, for data manipulation.
- <code>tidyr</code>, for data cleaning.
- <code>purrr</code>, for functional programming.
- <code>tibble</code>, for tibbles, a modern re-imagining of dataframes.
- <code>string</code>, for strings.

There are a few ways to set the working directory in RStudio.
- Use the <code>setwd()</code> function. We can use this function to set our working directory to the Desktop folder by typing: <code>setwd("~/Desktop")</code> in the Console.
- Navigate to and choose the working directory from the Session menu.

To print our working directory in the Console, type <code>getwd()</code>

# Building Blocks of R

### Data Types in R (integers and doubles)
- 6 types of vectors:
  1. integer - must use L bc R is heavily used for data analysis and statistical manipulation which don't really use integers all that often
  2. double - can store any number (large, small, positive, negative, with digits after the decimal, or without)
  3. character
  4. logical - store Boolean data T & F are shorthand and you can use that or TRUE & FALSE
  5. complex (not widely applicable)
  6. raw (not widely applicable)
- can create a vector using c(...)
    - ex. a <- c(1, 2, 3, 4, ..., 10)
    - the c stands for concatenate
- ***typeof(variable.name)*** - returns the basic type of an object

### Coercion rules in R
- All vector elements must be of the same type
- If a vectors has only logical and numeric elements, all logicals will be converted to numbers
- if vector has a mix of characters, logical, and numbers => everything is converted to characters

### Functions in R
- <code>function.name(x)</code> - runs the function called function.name on the data x
- generally like to save the results to our function into a new variable
- <code>args(round)</code> will tell you what arguments the function takes
