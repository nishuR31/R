# R Programming Fundamentals

![R](https://img.shields.io/badge/-R-3776AB?logo=r&logoColor=white)
![Python](https://img.shields.io/badge/-Python-3776AB?logo=python&logoColor=white)

## 1. Core Language Components

### Variables & Tokens
```r
# Variable assignment
x <- 10          # Preferred assignment
y = "Hello"      # Alternative assignment
.z <<- 3.14      # Global assignment

# Valid names
my_var <- 1
Var2 <- 2
.plot_data <- 3  # Hidden variable

# Invalid names
# 2var <- 5      # Error
# .2var <- 5     # Error

# Special tokens
1:5              # Sequence operator
%in%             # Match operator
~ x + y          # Formula operator
```

### Basic Syntax Elements
| Token Type      | Examples                      |
|-----------------|-------------------------------|
| Operators       | `+`, `-`, `%%`, `==`, `!=`   |
| Brackets        | `()`, `[]`, `{}`, `[[]]`     |
| Reserved Words  | `if`, `function`, `NULL`     |
| Literals        | `3.14`, `"text"`, `TRUE`     |

## 2. Control Structures

### Conditional Logic
```r
# Basic if-else
if (x > 10) {
  print("High")
} else if (x > 5) {
  print("Medium")
} else {
  print("Low")
}

# Vectorized ifelse
result <- ifelse(x > 0, "Positive", "Non-positive")

# Switch statement
fruit <- "apple"
switch(fruit,
       "apple" = "red",
       "banana" = "yellow",
       "unknown")
```

### Loops
```r
# For loop
for (i in 1:5) {
  print(i^2)
}

# While loop
count <- 1
while (count <= 5) {
  print(paste("Count:", count))
  count <- count + 1
}

# Repeat loop
repeat {
  print("Looping")
  if (runif(1) > 0.5) break
}

# Loop control
for (i in 1:10) {
  if (i %% 2 == 0) next  # Skip even numbers
  if (i > 7) break       # Early exit
  print(i)
}
```

## 3. Error Handling
```r
# Basic error catching
try({
  result <- 10 / "a"
}, silent = TRUE)

# Structured error handling
tryCatch(
  expr = {
    sqrt("text")
  },
  error = function(e) {
    message("Error occurred: ", e$message)
    return(NA)
  },
  warning = function(w) {
    message("Warning: ", w$message)
  }
)

# Custom errors
validate_age <- function(age) {
  if (age < 0) stop("Age cannot be negative")
  if (age > 150) warning("Unusual age value")
  age
}
```

## 4. Object-Oriented Programming

### S3 System (Informal)
```r
# Create class
student <- list(name = "Alice", gpa = 3.8)
class(student) <- "Student"

# Generic method
print.Student <- function(x) {
  cat("Student:", x$name, "\nGPA:", x$gpa)
}

print(student)
```

### R6 System (Modern OOP)
```r
library(R6)

Person <- R6Class("Person",
  public = list(
    name = NULL,
    initialize = function(name) {
      self$name <- name
    },
    greet = function() {
      cat("Hello, I'm", self$name)
    }
  )
)

bob <- Person$new("Bob")
bob$greet()
```

## 5. Package Management

### Installing Modules
```r
# From CRAN
install.packages("dplyr")

# From GitHub
remotes::install_github("tidyverse/ggplot2")

# From Bioconductor
if (!require("BiocManager"))
    install.packages("BiocManager")
BiocManager::install("DESeq2")

# List installed packages
installed.packages()

# Update packages
update.packages(ask = FALSE)
```

## 6. Memory & Performance

### Object Size
```r
obj_size <- object.size(mtcars)
format(obj_size, units = "MB")
```

### Vectorization vs Loops
```r
# Loop approach
sum_loop <- function(vec) {
  total <- 0
  for (i in seq_along(vec)) {
    total <- total + vec[i]
  }
  total
}

# Vectorized approach
sum_vec <- function(vec) sum(vec)

# Benchmarking
system.time(sum_loop(1:1e6))  # ~0.05s
system.time(sum_vec(1:1e6))   # ~0.001s
```

## 7. Help & Documentation

### Accessing Help
```r
?mean                # Function documentation
help.search("linear") # Search documentation
vignette("dplyr")    # Package vignettes
example(plot)        # Run examples
```

### Code Style Guide
```r
# Good
calculate_mean <- function(x) {
  mean(x, na.rm = TRUE)
}

# Bad
CalcMean<-function(x){mean(x,na.rm=T)}
```

## 8. Data Types & Structures

### Type Checking
```r
is.numeric(5)        # TRUE
is.character("5")    # TRUE
is.logical(TRUE)     # TRUE
class(mtcars)        # "data.frame"
```

### Type Conversion
```r
as.numeric("123")    # 123
as.character(123)    # "123"
as.factor(c("a","b"))# Factor with levels
```

## 9. Functional Programming

### Map-Reduce Pattern
```r
library(purrr)

numbers <- 1:5

# Map
squared <- map(numbers, ~ .x^2)

# Reduce
total <- reduce(numbers, `+`)
```

### Memoization
```r
library(memoise)

slow_fn <- function(x) {
  Sys.sleep(1)
  x * 2
}

memo_fn <- memoise(slow_fn)
system.time(memo_fn(5))  # 1s first run, 0s subsequent
```

## 10. Debugging Tools

### Interactive Debugging
```r
debug(lm)            # Set debug flag
undebug(lm)          # Remove debug flag

# Browser mode
troublesome_fn <- function() {
  browser()  # Pauses execution here
  # ... code ...
}
```

### Profiling
```r
Rprof("profile.out")
# Code to profile
Rprof(NULL)
summaryRprof("profile.out")
```

# To install and run R codes in ide or in your local machine click -> 

[![installtion.md](https://img.shields.io/badge/Installation-Guide-fff?logo=r&logoColor=black)](installation.md)
