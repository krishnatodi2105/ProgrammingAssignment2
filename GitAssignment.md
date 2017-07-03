# Week-3-Assignment
Peer Graded Assignment

Below is a function that stores a matrix and caches its inverse.
This function creates a special "matrix" object that can cache its inverse.

makeCacheMatrix <- function(x=matrix()){

#Creating the matrix by initializing object x.

inv <- NULL

set <- function(y){

x <<- y

inv <<- NULL

}

#Defining x outside of get() and retrieving from parent environment

get <- function()x

#Defining setting and getting the inverse functions

setInverse <- function(inverse) inv <<- inverse

getInverse <- function() inv

#Naming each element in order ot allow the use of "$" operator

list(set=set,
get=get,
setInverse=setInverse,
getInverse=getInverse)

}

This function computes the inverse of the special "matrix" returned by makeCacheMatrix above. 
If the inverse has already been calculated (and the matrix has not changed), then it should retrieve the inverse from the cache.

cacheSolve <- function(x,...){

Return a matrix that is the inverse of x.

#Retrieving an inverse by calling getinverse() function on the input

inv <- x$getInverse()

#Check to see whether the result is NULL. If there isn't a NULL value, a valis caches inverse exists.

if(!is.null(inv)){

message("getting cached data")

#Returning inverse matrix to the parent environment

return(inv)

}

#If !is.null(inv) is FALSE, then this function gets the matrix and calculates the inverse using solve()

mat <-x$get()

inv <- solve(mat,...)

#Inputting the matrix to set the inverse in the input object

x$setInverse(inv)

#Printing the inverse matrix to the parent environment

inv

}
