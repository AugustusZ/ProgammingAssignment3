ProgammingAssignment3
=====================

Repository for Programming Assignment 3 for R Programming on Coursera

1.
Naively using the template provided by the course led to that the variable storing the read-in data have the same name as the second argument, which is the very reason the test for checking arguments did not work at the first place, i.e.,
        best <- function(state, outcome) {
AND
          outcome <- read.csv("outcome-of-care-measures.csv", colClasses = "character")

2.
Solusion for checking "if in" is retrieved from the answer by medriscoll on stackoverflow.com: http://stackoverflow.com/questions/1169248/r-function-for-testing-if-a-vector-contains-a-given-element, i.e.
        v <- c('a','b','c','e')

        'b' %in% v
        ## returns TRUE

        match('b',v)
        ## returns the first location of 'b', in this case: 2

3.
