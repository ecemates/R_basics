# R_basics

# loading the dslabs package and dataset
library(dslabs)
data(x) 
#you need to write name of your dataset instead of x, let's say x is data that shows us the number of covid patients acoording to countries and x has three columns -> country, numpatients, population

# determining that the x dataset is of the "data frame" class
class(x)
# finding out more about the structure of the object
str(x)
# showing the first 6 lines of the dataset
head(x)

# using the accessor operator to obtain the country column
x$country
# displaying the variable names in the murders dataset
names(x)
# determining how many entries are in a vector
pop <- x$country
length(pop)
# vectors can be of class numeric and character
class(pop)

# logical vectors are either TRUE or FALSE
z <- 3 == 2
z
class(z)

# factors are another type of class
class(x$numpatients)
# obtaining the levels of a factor
levels(x$numpatients)

#Vectors
# We may create vectors of class numeric or character with the concatenate function
codes <- c(380, 124, 818)
country <- c("italy", "canada", "egypt")

# We can also name the elements of a numeric vector
# Note that the two lines of code below have the same result
codes <- c(italy = 380, canada = 124, egypt = 818)
codes <- c("italy" = 380, "canada" = 124, "egypt" = 818)

# We can also name the elements of a numeric vector using the names() function
codes <- c(380, 124, 818)
country <- c("italy","canada","egypt")
names(codes) <- country

# Using square brackets is useful for subsetting to access specific elements of a vector
codes[2]
codes[c(1,3)]
codes[1:2]

# If the entries of a vector are named, they may be accessed by referring to their name
codes[“turkey”]
Z <- c(13, “turkey”, 56)
as.numeric(z)

# create vector and sort it
z<- c(243, 4, 3, 67, 97)
sort(z)    # puts elements in order

# index functions
index <- order(z)    # returns index that will put z in order
z[index]    # rearranging by this index puts elements in order
order(z)
z <- c(243, 4, 3, 67, 97)
rank(z)    # returns ranks (smallest to largest)

# order / abb functions
index <- order(x$country)
x$abb[index]    # order abbreviations by country

# max / min functions
max(x$numpatients)    # highest number of total covid patients
i_max <- which.max(x$numpatients)    # index with highest number of patients
x$country[i_max]    # country name with highest number of total covid patients

# to find intersection set
x <- c("a", "b", "c", "d", "e")
y <- c("a", "d", "f")
y %in% x

# adding a column with mutate
x <- mutate(x, covid_rate = numpatients / population * 100000) 

# subsetting with filter
filter(x, covid_rate <= 0.70)

# selecting columns with select
new_table <- select(x, country, numpatients, covid_rate)

# using the pipe
x %>% select(country, numpatients, covid_rate) %>% filter(covid_rate <= 0.71)

# creating a data frame with stringAsFactors = FALSE
grades <- data.frame(names = c(“student1”, “student2”, “student3”, “student4”), 
                     exam_1 = c(60, 80, 85, 70), 
                     exam_2 = c(89, 90, 85, 60),
                     stringsAsFactors = FALSE)
