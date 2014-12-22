ProgammingAssignment3
=====================

Repository for Programming Assignment 3 for R Programming on Coursera

PART 2 FINDING THE BEST HOSPITAL IN A STATE

        best.R

1.
Naively using the template provided by the course led to that the variable storing the read-in data have the same name as the second argument, which is the very reason the test for checking arguments did not work at the first place, i.e.,

        best <- function(state, outcome) {...}
AND

          outcome <- read.csv("outcome-of-care-measures.csv", colClasses = "character")

2.
Solution for checking "if in" is retrieved from the answer by medriscoll on stackoverflow.com: http://stackoverflow.com/questions/1169248/r-function-for-testing-if-a-vector-contains-a-given-element, i.e.

        v <- c('a','b','c','e')
       'b' %in% v
        ## returns TRUE
        match('b',v)
        ## returns the first location of 'b', in this case: 2

3.
Solution for sorting the data frame is retrieved from http://www.dummies.com/how-to/content/how-to-sort-data-frames-in-r.html, i.e.

        order.outcomes <- order(outcome.data$Hospital.Name)
        outcome.data <- outcome.data[order.outcomes,]

then the data frame of "outcome.data" is sorted according to $Hospital.Name alphabet order.

4.# this part cost my whole evening!

The code got the wrong result and I did not know why. Then I manually run codes in console step by step and then I found that:
in my former solution, I acquired the indice for the wanted part data frame and then used these indice to subset a subset of the data. Of course it is wrong.
