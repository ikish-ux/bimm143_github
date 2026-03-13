# Class06
Ivan Henry Kish(PID:A17262923)

- [Background](#background)
- [A first function](#a-first-function)
- [A 2nd function](#a-2nd-function)
- [A new cool function](#a-new-cool-function)

## Background

Functions are at te heart of using R. Everything we do involves calling
and using functions (from data input, analysis to results output).

All functions in R have at least 3 things:

1.  A **name** the thing we used to called the function.
2.  One or more input **arguments** that are comma separated
3.  The **body**, lines of code between curly brackets {} that does the
    work of the function.

## A first function

Let’s write a silly wee function to add some numbers:

``` r
add <- function(x) {
  x + 1
}
```

Let’s try it out

``` r
add(100)
```

    [1] 101

Now will this work?

``` r
add(c(100,200,300))
```

    [1] 101 201 301

I am going to modify the function to be more useful.

``` r
add <- function(x,y=1) {
  x + y
}
```

``` r
add(100,10)
```

    [1] 110

``` r
add(100)
```

    [1] 101

> **N.I.K.** Input arguments can be either **required** or **optional**.
> The later have a fall-back efault that is specified in the function
> coed with an = sign.

``` r
#add(100,200,300)
```

## A 2nd function

All functions in R look like this

    name <- function(arg){
    body
    }

The `sample()` function in R selects random values at a specified number
of random selections. You can also specify whether or not you want
values to be repeatedly picked or not.

``` r
sample(1:10, size=4, replace=FALSE)
```

    [1] 3 7 2 5

> Q. Return 12 numbers picked randomly from the input 1:10

``` r
sample(1:10, size=12, replace=TRUE)
```

     [1] 3 3 7 7 5 2 1 4 2 1 8 9

> Q. Write the code to generate a random 12 nucleotide log DNA sequence

``` r
sample(c("A","T","G","C"), size=12, replace=TRUE)
```

     [1] "A" "G" "T" "G" "A" "A" "G" "A" "G" "T" "T" "A"

> Q. Write a first. version function called `generte_dna()` that
> generates a user specified length `n` random DNA sequnce.

``` r
generate_dna<- function(n){
  sample(c("A","T","G","C"), size=n, replace=TRUE)
}
generate_dna(26)
```

     [1] "C" "T" "C" "T" "C" "T" "C" "C" "C" "G" "C" "T" "C" "C" "C" "A" "A" "C" "A"
    [20] "C" "T" "G" "A" "A" "G" "T"

``` r
generate_dna(45)
```

     [1] "C" "G" "G" "A" "C" "T" "G" "C" "C" "G" "C" "C" "A" "C" "G" "C" "A" "G" "C"
    [20] "G" "T" "A" "C" "C" "T" "T" "C" "T" "T" "C" "C" "T" "T" "C" "A" "A" "G" "C"
    [39] "A" "A" "G" "A" "T" "A" "T"

> Q. Modify our function to return a FASTA like sequence rather than the
> quoted nucleotides we have been getting.

``` r
generate_dna<- function(n){
  seq<-sample(c("A","T","G","C"), size=n, replace=TRUE,)
  paste(seq,collapse = "")
}
```

``` r
generate_dna(45)
```

    [1] "CAGTATGTAAAAAGGCTGTCACTACACTGGTTATAGGTGTCTCGA"

> Q. Give the user an option to return FASTA format output sequence or
> standard multi-element vector format.

``` r
generate_dna<- function(n, fasta=TRUE){
  seq<-sample(c("A","T","G","C"), size=n, replace=TRUE,)
  
  if(fasta){
  seq<-paste(seq,collapse = "") 
  }
  return(seq)
}
```

``` r
generate_dna(12,fasta=T)
```

    [1] "GAGACCGATTCC"

## A new cool function

> Q. Write a function called `generate_protein()` that generates a user
> specified length protein sequence in FASTA like format?

``` r
generate_protein<- function(n, fasta=TRUE){
  seq<-sample(c("A", "R", "N", "D", "C", "Q", "E", "G", "H", "I", 
        "L", "K", "M", "F", "P", "S", "T", "W", "Y", "V"), size=n, replace=TRUE,)
  
  if(fasta){
  seq<-paste(seq,collapse = "") 
  }
  return(seq)
}
```

``` r
generate_protein(12)
```

    [1] "IFIHTIRLFLEY"

> Q. Use your new `generate_protein()` function to generate sequences
> between length 6 and 12 amino acids in length and check any of these
> are unique in nature (found in the NR database at NCBI).

``` r
generate_protein<- function(n, fasta=TRUE){
  seq<-sample(c("A", "R", "N", "D", "C", "Q", "E", "G", "H", "I", 
        "L", "K", "M", "F", "P", "S", "T", "W", "Y", "V"), size=n, replace=TRUE,)
  
  if(fasta){
  seq<-paste(seq,collapse = "") 
  }
  return(seq)
}
```

``` r
for(i in 6:12){
  cat(">", i,sep="", "\n")
  cat(generate_protein(i),"\n")
}
```

    >6
    NICGRV 
    >7
    DMKAGFW 
    >8
    GWFHEHQW 
    >9
    KWTTFMGGT 
    >10
    ENVNCQVKIV 
    >11
    ADVHIWMPTRG 
    >12
    GAVKLHCHCATG 

Identical matches were only seen in the amino acids that were generated
with lengths 6 and 7.
