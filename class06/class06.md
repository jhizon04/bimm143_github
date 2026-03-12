# Class 6: R functions
Jacob Hizon PID: A17776679

- [Background](#background)
- [Our first function](#our-first-function)
- [A second function](#a-second-function)
- [A Protein generating function](#a-protein-generating-function)

## Background

All functions in R have at least 3 things:

- A **name** that we use to call the function.
- One or more input **arguments**
- The **body** the lines of R code that do the work

## Our first function

Let’s write a silly little function called `add()` to to add some
numbers (the input arguments)

``` r
add <- function(x, y) {
  x + y
}
```

Now we can use this function

``` r
add(100, 1)
```

    [1] 101

``` r
add( x= 10, y = 10)
```

    [1] 20

``` r
add(x = c(100, 1, 100), y = 1)
```

    [1] 101   2 101

> Q. What if I give a multiple element vector to `x` and `y`

``` r
add(x = c(100, 1), y=c(100,1))
```

    [1] 200   2

> What if I give three inputs to the function

``` r
#add( x = x(100, 1), y = 1, z = 1)
```

> Q. What if I give only one input to the add fucntion?

``` r
addnew <- function(x, y=1) {
  x + y
}
```

``` r
addnew(x=100)
```

    [1] 101

``` r
addnew(c(100, 1), 100)
```

    [1] 200 101

If we write our function with input arguments having no default value
then the user will be required to set them when they use the function.
We can give our input arguments “default” values by setting them equal
to e.g. `y=1`

## A second function

Let’s try something more interesting: Make a sequence generating tool…

The `sample()` function can be a useful starting point here:

``` r
sample(1:10, size = 4)
```

    [1] 9 7 5 1

> Q. Generate 9 random numbers taken from the input vector x=1:10?

``` r
sample(1:10, size = 9)
```

    [1]  4  6  5 10  1  3  7  9  8

> Q. Generate 12 random numbers taken from the input vector x=1:10?

``` r
sample(1:10, size = 12, replace = TRUE)
```

     [1] 10  7  6  2  6  7  7  6  2  6 10  8

> Q. Write code for the `sample()` function that generates nucleotide
> sequence of length 6?

``` r
sample(c("A", "C", "T", "G"), size = 6, replace = TRUE)
```

    [1] "A" "A" "G" "G" "A" "C"

> Q. Write a first fucntion `generate_dna()` that returns a *user
> specified length* DNA sequence

``` r
generate_dna <- function(x = 6) {sample(c("A", "C", "T", "G"), size = x, replace = TRUE)
  
}
```

``` r
generate_dna(3)
```

    [1] "G" "G" "C"

``` r
generate_dna(
)
```

    [1] "C" "T" "A" "G" "G" "C"

``` r
generate_dna(x=100)
```

      [1] "T" "G" "T" "A" "A" "G" "C" "A" "T" "T" "A" "C" "C" "T" "C" "G" "C" "C"
     [19] "T" "G" "A" "A" "T" "T" "G" "T" "T" "T" "T" "C" "G" "C" "G" "T" "G" "C"
     [37] "G" "C" "C" "G" "C" "T" "A" "T" "G" "A" "C" "G" "A" "G" "G" "A" "T" "G"
     [55] "A" "C" "C" "T" "C" "A" "A" "C" "T" "G" "A" "C" "A" "T" "A" "C" "G" "T"
     [73] "C" "G" "G" "C" "C" "A" "G" "A" "C" "T" "A" "T" "G" "A" "G" "G" "T" "G"
     [91] "A" "T" "C" "T" "G" "G" "G" "G" "G" "T"

> **Key-Points**

Every function in R looks fundamentally the same in terms of its
structure. Basically 3 things: name, input, and body


    name <- function(input) {
      body
    }

> Functions can have multiple inputs. These can be **required**
> arguments or **optional** arguments. With optional arguments having a
> set default value.

> Q. Modify and improve our `generate_data()` function to return it’s
> generated sequence in a more standard format “AGTAGTA” rahter than the
> vector “A”, “C”, “G”, “A”

``` r
generate_dna <- function(x = 6, fasta = TRUE) {
  ans <- sample(c("A", "C", "T", "G"), 
                                  size = x, 
                                 replace = TRUE)
  if(fasta) {
    cat("Single-element vector output")
  ans <- paste(ans, collapse="") }
  else {
    cat("Multi-element vector output")}
  return(ans)
}

generate_dna(fasta = FALSE)
```

    Multi-element vector output

    [1] "A" "A" "G" "C" "C" "G"

The `paste()` function - it’s job is to join up or stick together (a.k.a
paste)

``` r
paste(c("alice", "loves R"), sep = "")
```

    [1] "alice"   "loves R"

Flow control means where the R brain goes in your code

``` r
good_mood <- FALSE 

if (good_mood) {
  cat("Great!")
  
} else {
  cat("Bummer!")
}
```

    Bummer!

## A Protein generating function

> Q. Write a function, called `generate_protein()` that generates a
> user-specified length protein sequecne.

> Q. Use that function to generate random protein sequences length 6 and
> 12

> Q. Are any of your sequences unique i.e. not found anywhere in nature

> Q. Write a function, called `generate_protein()` that generates a
> user-specified length protein sequecne. \#The amino acids to sample
> from sample \<-c(“A”, “R”, “N”, “D”, “C”, “Q”, “G”, “E”, “H”, “I”,
> “L”, “K”, “M”, “F”, “P”, “S”, “T”, “W”, “Y”, “V”) \# Generate the
> function and specify size and replace size = x, replace = TRUE) \#
> Remove the “” paste(ans, collapse=““) }

> Q. Use that function to generate random protein sequences length 6 and
> 12

``` r
generate_protein <- function(x) {
  ans <- sample(c("A", "R", "N", "D", "C", "Q", "G", "E", "H", "I", "L", "K", "M", "F", "P", "S", "T", "W", "Y", "V"), 
                                  size = x, 
                                 replace = TRUE)
paste(ans, collapse="") }


generate_protein(12)
```

    [1] "HIMCMTKFVNLM"

``` r
generate_protein <- function(x = 6) {
  ans <- sample(c("A", "R", "N", "D", "C", "Q", "G", "E", "H", "I", "L", "K", "M", "F", "P", "S", "T", "W", "Y", "V"), 
                                  size = x, 
                                 replace = TRUE)
paste(ans, collapse="") }


generate_protein()
```

    [1] "ELTGNE"

``` r
generate_protein <- function(x = 12) {
  ans <- sample(c("A", "R", "N", "D", "C", "Q", "G", "E", "H", "I", "L", "K", "M", "F", "P", "S", "T", "W", "Y", "V"), 
                                  size = x, 
                                 replace = TRUE)
paste(ans, collapse="") }


generate_protein
```

    function (x = 12) 
    {
        ans <- sample(c("A", "R", "N", "D", "C", "Q", "G", "E", "H", 
            "I", "L", "K", "M", "F", "P", "S", "T", "W", "Y", "V"), 
            size = x, replace = TRUE)
        paste(ans, collapse = "")
    }

``` r
for(i in 6:12) {
  #FASTA ID line ">id"
  cat(">", i, sep="", "\n")
  # Protein sequence line
  cat(generate_protein(i), "\n")
}
```

    >6
    QPEREQ 
    >7
    VAHPFDD 
    >8
    SALMPYWT 
    >9
    SPCHSVTPP 
    >10
    NGRLVGEACI 
    >11
    DIGTHIPWDLY 
    >12
    VCRSRYSVMIRF 

> Q. Are any of your sequences unique i.e. not found anywhere in nature

Yes - there is uniqueness starting at 8aa for my generated protein
sequences.
