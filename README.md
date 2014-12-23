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

PART 3 RANKING HOSPITIALS BY OUTCOME IN A STATE

        rankhospital.R
        
5.
Just wrong result. So, agian, I manually run the codes and found:
When ranking data, the data must be numeric. Sometimes (e.g. before revising the code in this part), the data read in are characters, and they work well with which.max() and which.min() because of coercion, but not ranking (order(), min(), max(), etc.). Check these out:

        > d <- c("10","9","11","2","0","404","hello") # I give a example *character* vector here
        > d # yeah, they are really characters
        [1] "10"    "9"     "11"    "2"     "0"     "404"   "hello"
        > max(d)
        [1] "hello"
        > min(d)
        [1] "0"
        > order.index <- order(d) # so I order the whole vector
        > ordered.d <- d[order.index]
        > ordered.d # the order is based on ... ASCII?
        [1] "0"     "10"    "11"    "2"     "404"   "9"     "hello"
        > d[which.min(d)] # but which.max and which.min work well with characters, because of coercion
        [1] "0"
        Warning message:
        In which.min(d) : NAs introduced by coercion
        > d[which.max(d)]
        [1] "404"
        Warning message:
        In which.max(d) : NAs introduced by coercion

Hence, as for character vectors, use as.numeric() before order(). So first of all work, know the data class :3

6.
About order.
Also able to be retrieved from the link given in <3.>, we can rank the data based on two cols.

        index <- order(certain_state[[outcome_col]],certain_state$Hospital.Name) # line *
        certain_state <- certain_state[index, ]
        
<?> My current concern is, how to use with() to rewrite line *, when I only know the outcome_col and have to use [ [ ] ] for one col?
