# class06: R functions
Sylvia Ho (PID: a18482382)

## background

functions are at the heart of using r everything insvolves calling and
using functions all fns have at least 3 thigns:

1.  a **name** the thing we use to call it
2.  input **args** that are comma separated
3.  **body** lines of code btwn curly {} that does work of fn

``` r
add<- function(x){
  x+1
}
```

``` r
add(c(100,200,300))
```

    [1] 101 201 301

``` r
add<- function(x,y){
  x+y
}
```

``` r
add(100,10)
```

    [1] 110

``` r
log(10,base=10)
```

    [1] 1

> **n.b** input args can be either reqd or opt the latter have fall back
> default that is spec in fn w an equal sign

``` r
#add(x=100,y=200,z=300)
```

## a second fn

all fns in R look like this

`name<fn(arg){ body }`

the`sample()` fn in R samples randomly from arg

``` r
sample(1:10)
```

     [1]  7  2  6  4 10  8  1  3  5  9

> Q writea first version fn called `generate dna()` that gens a user
> spec length n random dna seq

``` r
generate_dna<-function(n=6){
  bases<-c("a","t","g","c")
  sample(bases, size=n, replace = TRUE)
}

generate_dna(100)
```

      [1] "c" "a" "a" "c" "t" "g" "t" "c" "t" "g" "g" "a" "g" "t" "g" "g" "g" "a"
     [19] "a" "t" "t" "t" "a" "t" "t" "t" "a" "a" "g" "a" "t" "t" "c" "c" "c" "c"
     [37] "a" "a" "a" "a" "t" "c" "a" "g" "c" "c" "t" "a" "g" "c" "a" "g" "t" "a"
     [55] "g" "t" "a" "t" "a" "a" "c" "a" "g" "g" "a" "a" "g" "a" "g" "c" "t" "g"
     [73] "a" "c" "a" "c" "c" "a" "g" "t" "c" "g" "a" "a" "a" "t" "c" "a" "g" "g"
     [91] "t" "c" "g" "t" "c" "c" "c" "g" "g" "g"

> Q mod to return actual seq

``` r
generate_dna<-function(n=6){
  bases<-c("a","t","g","c")
  ans<-sample(bases, size=n, replace = TRUE)
 an<-paste(ans,collapse="")
 return(an)
}

generate_dna(10)
```

    [1] "cacgcgagag"

> Q option FASTA or vector

``` r
generate_dna<-function(n=6, fasta = TRUE){
  bases<-c("a","t","g","c")
  ans<-sample(bases, size=n, replace = TRUE)
 
 if (fasta){
   ans<-paste(ans,collapse="")

 }
 return(ans)
 
}
```

``` r
generate_dna(10)
```

    [1] "tcctgcaaac"

``` r
generate_dna(10, fasta = F)
```

     [1] "c" "g" "g" "a" "t" "g" "c" "g" "a" "c"

``` r
generate_protein<- function(){
  aa<-c("A", "R", "N", "D", "C", "E", "Q", "G", "H", "I",
"L", "K", "M", "F", "P", "S", "T", "W", "Y", "V")
  
}
```

``` r
generate_protein<-function(n=6, fasta = TRUE){
aa<-c("A", "R", "N", "D", "C", "E", "Q", "G", "H", "I",
"L", "K", "M", "F", "P", "S", "T", "W", "Y", "V")
  
  ans<-sample(aa, size=n, replace = TRUE)
 
 if (fasta){
   ans<-paste(ans,collapse="")

 }
 return(ans)
 
}
generate_protein(10, fasta = F)
```

     [1] "D" "C" "Y" "C" "E" "Q" "V" "S" "Y" "I"

> Q gen protein gn to gen seqs between 6 to 12, check in uniqueue aka
> against NR database at NCBI

``` r
generate_protein<-function(n=6, fasta = TRUE){
aa<-c("A", "R", "N", "D", "C", "E", "Q", "G", "H", "I",
"L", "K", "M", "F", "P", "S", "T", "W", "Y", "V")
  
  ans<-sample(aa, size=n, replace = TRUE)
 
 if (fasta){
   ans<-paste(ans,collapse="")

 }
 return(ans)}
```

``` r
for (i in 6:12) {
  cat(">",i, "\n")
  cat(generate_protein(i), "\n")
}
```

    > 6 
    VMSQRP 
    > 7 
    ENPPHLG 
    > 8 
    AIFPNLKE 
    > 9 
    RVHRHGAYF 
    > 10 
    KWYYLGMLWG 
    > 11 
    MRACPKVKRNK 
    > 12 
    IWPVGVYATNFW 
