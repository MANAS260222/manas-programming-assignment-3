# manas-programming-assignment-3

## A pair of functions that cache the inverse of a matrix


## Creates a special matrix object that can cache its inverse
makeCacheMatrix <- function( M = matrix() ) {
  
  ## ASSIGN A VALUE TO THE INVERSE property
  i <- NULL
  
  ## Set the matrix
  set <- function( matrix ) {
    M <<- matrix
    i <<- NULL
  }
  
  ##  function to get the matrix
  get <- function() {
    ## Return the matrix
    M
  }
  
  ## FunctioN to set the inverse of the matrix
  setInverse <- function(inverse) {
    i <<- inverse
  }
  
  ## Method to get the inverse of the matrix
  getInverse <- function() {
    ## Return the inverse property
    i
  }
  
  ## Return a list of the methods
  list(set = set, get = get,
       setInverse = setInverse,
       getInverse = getInverse)
}

cacheSolve <- function(x, ...) {
  
  ## Return a matrix that is the inverse of 'x'
  M <- x$getInverse()
  
  ## Just return the inverse if its already set
  if( !is.null(M) ) {
    message("getting cached data")
    return(M)
  }
  
  ## Get the matrix from our object
  data <- x$get()
  
  ## Calculate the inverse using matrix multiplication
  M <- solve(data) %*% data
  
  ## Set the inverse to the object
  x$setInverse(M)
  
  ## Return the matrix
  M
}

