# R / RStudio Quick Cheat Sheet# R / RStudio Quickselected objects only
dont_rm_ls <- c("obj1", "obj2", "obj3")
rm(list = setdiff(ls(), dont_rm_ls))
```

---

## RStudio

```r
# Clear console
cat("\014")
```

Shortcuts:

- Run line: `Ctrl + Enter`
- Comment/uncomment: `Ctrl + Shift + C`
- Clear console: `Ctrl + L`
- Assign operator: `Alt + -`

---

## Variables

```r
x <- 10
y <- 20

z <- x + y
```

Check type:

```r
class(x)
typeof(x)
str(x)
```

---

## Vectors

```r
x <- c(1, 2, 3, 4, 5)
```

Common functions:

```r
length(x)
sum(x)
mean(x)
min(x)
max(x)
sort(x)
```

Indexing:

```r
x[1]
x[2]
x[length(x)]
```

Filtering:

```r
x[x > 3]
```

---

## Data Frames

```r
df <- data.frame(
  name = c("John", "Mary"),
  age = c(25, 30)
)
```

View data:

```r
head(df)
tail(df)
str(df)
summary(df)
View(df)
```

Select columns:

```r
df$name
df[, "name"]
df[, c("name", "age")]
```

Filter rows:

```r
df[df$age > 25, ]
```

Create column:

```r
df$age_plus_10 <- df$age + 10
```

---

## Import / Export

CSV:

```r
df <- read.csv("file.csv")

write.csv(df, "output.csv", row.names = FALSE)
```

Excel:

```r
library(readxl)

df <- read_excel("file.xlsx")
```

---

## Missing Values

```r
is.na(x)

sum(is.na(x))

na.omit(df)
```

Replace NA:

```r
df[is.na(df)] <- 0
```

---

## Strings

```r
x <- "hello world"
```

Common functions:

```r
toupper(x)
tolower(x)

nchar(x)

paste("Hello", "World")
paste0("Hello", "World")

substr(x, 1, 5)
```

---

## Factors

```r
x <- factor(c("A", "B", "A"))

levels(x)
```

---

## Dates

```r
today <- Sys.Date()

today

as.Date("2025-01-01")
```

---

## Loops

For loop:

```r
for(i in 1:5){
  print(i)
}
```

While loop:

```r
i <- 1

while(i <= 5){
  print(i)
  i <- i + 1
}
```

---

## Conditions

```r
if(x > 0){
  print("Positive")
} else {
  print("Negative")
}
```

Vectorized:

```r
ifelse(x > 0, "Positive", "Negative")
```

---

## Functions

```r
add_numbers <- function(a, b){
  return(a + b)
}

add_numbers(2, 3)
```

---

## Apply Family

```r
lapply(my_list, mean)

sapply(my_list, mean)

apply(my_matrix, 2, mean)
```

Margin:

- 1 = rows
- 2 = columns

---

## Useful Packages

```r
library(dplyr)
library(tidyr)
library(readr)
library(readxl)
library(ggplot2)
```

Install:

```r
install.packages("dplyr")
```

---

## dplyr

```r
library(dplyr)
```

Select columns:

```r
df %>% select(name, age)
```

Filter rows:

```r
df %>% filter(age > 25)
```

Create column:

```r
df %>% mutate(age2 = age + 10)
```

Sort:

```r
df %>% arrange(age)

df %>% arrange(desc(age))
```

Group:

```r
df %>%
  group_by(group) %>%
  summarise(avg_age = mean(age))
```

---

## Pipes

```r
df %>%
  filter(age > 25) %>%
  arrange(age)
```

Read as:

"Take df, then filter, then arrange."

---

## ggplot2

```r
library(ggplot2)
```

Scatter:

```r
ggplot(df, aes(x = age, y = salary)) +
  geom_point()
```

Line:

```r
ggplot(df, aes(x = date, y = sales)) +
  geom_line()
```

Histogram:

```r
ggplot(df, aes(x = age)) +
  geom_histogram()
```

Boxplot:

```r
ggplot(df, aes(x = group, y = value)) +
  geom_boxplot()
```

---

## Useful Functions

```r
head()
tail()

dim()
nrow()
ncol()

names()

unique()

table()

which()

match()

subset()
```

---

## Debugging

```r
print(x)

str(df)

summary(df)
```

Check object type:

```r
class(x)

typeof(x)
```

---

## Session Info

```r
sessionInfo()
```

---

## Fresh Start

```r
# Remove all objects
rm(list = ls())

# Clear console
cat("\014")
```

## Workspace

```r
# List objects
ls()

# Remove all objects
rm(list = ls())

