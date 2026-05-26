# Class 12 HW: Q13 and Q14

> Q13: Read this file into R and determine the sample size for each
> genotype and their corresponding median expression levels for each of
> these genotypes.

``` r
expr <- read.table("rs8067378_ENSG00000172057.6.txt")
head(expr)
```

       sample geno      exp
    1 HG00367  A/G 28.96038
    2 NA20768  A/G 20.24449
    3 HG00361  A/A 31.32628
    4 HG00135  A/A 34.11169
    5 NA18870  G/G 18.25141
    6 NA11993  A/A 32.89721

``` r
nrow(expr)
```

    [1] 462

``` r
table(expr$geno)
```


    A/A A/G G/G 
    108 233 121 

This result shows the sample size for each genotype.

``` r
tapply(expr$exp, expr$geno, median)
```

         A/A      A/G      G/G 
    31.24847 25.06486 20.07363 

This result shows the corresponding median expression level for each
genotype.

> Q14: Generate a boxplot with a box per genotype, what could you infer
> from the relative expression value between A/A and G/G displayed in
> this plot? Does the SNP effect the expression of ORMDL3?

``` r
library(ggplot2)
```

``` r
ggplot(expr) + aes(geno, exp, fill=geno) + 
  geom_boxplot(notch=TRUE)
```

![](class12_files/figure-commonmark/unnamed-chunk-5-1.png)

From the boxplot, relative expression value between A/A and G/G is
clearly different - order of expression level is genotype A/A \> A/G \>
G/G. Thus, the SNP does affect the expression level of ORMDL3.
