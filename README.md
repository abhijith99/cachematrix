# cachematrix
assignment week 3
## Put comments here that give an overall description of what your
## functions do

## Write a short comment describing this function

makeCacheMatrix <- function(x = matrix()) {
> makeCacheMatrix <- function(x = matrix()) {
+         ## @x: a square invertible matrix
+         ## return: a list containing functions to
+         ##              1. set the matrix
+         ##              2. get the matrix
+         ##              3. set the inverse
+         ##              4. get the inverse
+         ##         this list is used as the input to cacheSolve()
+         
+         inv = NULL
+         set = function(y) {
+                 # use `<<-` to assign a value to an object in an environment 
+                 # different from the current environment. 
+                 x <<- y
+                 inv <<- NULL
+         }
+         get = function() x
+         setinv = function(inverse) inv <<- inverse 
+         getinv = function() inv
+         list(set=set, get=get, setinv=setinv, getinv=getinv)
+ }
> 
> cacheSolve <- function(x, ...) {
+         ## @x: output of makeCacheMatrix()
+         ## return: inverse of the original matrix input to makeCacheMatrix()
+         
+         inv = x$getinv()
+         
+         # if the inverse has already been calculated
+         if (!is.null(inv)){
+                 # get it from the cache and skips the computation. 
+                 message("getting cached data")
+                 return(inv)
+         }
+         
+         # otherwise, calculates the inverse 
+         mat.data = x$get()
+         inv = solve(mat.data, ...)
+         
+         # sets the value of the inverse in the cache via the setinv function.
+         x$setinv(inv)
+         
+         return(inv)
+ }
> test = function(mat){
+         ## @mat: an invertible matrix
+         
+         temp = makeCacheMatrix(mat)
+         
+         start.time = Sys.time()
+         cacheSolve(temp)
+         dur = Sys.time() - start.time
+         print(dur)
+         
+         start.time = Sys.time()
+         cacheSolve(temp)
+         dur = Sys.time() - start.time
+         print(dur)
+ }
> set.seed(1110201)
> r = rnorm(1000000)
> mat1 = matrix(r, nrow=1000, ncol=1000)
> test(mat1)
Time difference of 1.572631 secs
getting cached data
Time difference of 0.02501702 secs
> 

}


## Write a short comment describing this function

cacheSolve <- function(x, ...) {
        ## Return a matrix that is the inverse of 'x'
}
