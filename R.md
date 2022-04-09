# R

__________________________________
* [Formulas](## Formulas)
* [TL;DR Rscript](## TL;DR Rscript)
* [Strings](## Strings)
    * [String composition](### String composition)
* [Handling NA](## Handling NA)
* [TraMineR](# TraMineR)

___________________________________

## Formulas

A formula is an  unevaluated expression that may capture the environment
in which it was defined. Formulas are often passed to functions to
define the model the function should compute.
For instance `y ~ x1 + x2 ` defines y as the response variable and
x1, x2 as the covariates in a regression model.

### linear model

```R

lm(Sepal.Width ~ Sepal.Length + Petal.Width, data=iris, subset = Species=='virginica')
Coefficients:
 (Intercept)  Sepal.Length   Petal.Width
      0.8066        0.1685        0.5217

```

### Inspecting formula objects

```R

> dat <- iris
> M <- Sepal.Width ~ Sepal.Length + Petal.Width
> terms(M)
Sepal.Width ~ Sepal.Length + Petal.Width
attr(,"variables")
list(Sepal.Width, Sepal.Length, Petal.Width)
attr(,"factors")
             Sepal.Length Petal.Width
Sepal.Width             0           0
Sepal.Length            1           0
Petal.Width             0           1
attr(,"term.labels")
[1] "Sepal.Length" "Petal.Width"
attr(,"order")
[1] 1 1
attr(,"intercept")
[1] 1
attr(,"response")
[1] 1
attr(,".Environment")
<environment: R_GlobalEnv>

```

## TL;DR Rscript


  Rscript

  Run a script with the R programming language.
  More information: https://www.r-project.org.

* Run a script:

    Rscript path/to/file.R

* Run a script in vanilla mode (i.e. a blank session that doesn't save the workspace at the end):

         Rscript --vanilla path/to/file.R

* Execute one or more R expressions:

         -e expression1 -e expression2

Display R version:
Rscript --version

_____________________________

## Dataframes

### Column names

```R

> df <- data.frame(
        c(1, NA, 3),
        c(0, 2 , NA),
        c(100,1, 20)
        )

> colnames(df) <- paste('var', 1:3, sep='')
> df
 var1 var2 var3
1    1    0  100
2   NA    2    1
3    3   NA   20

> colnames(df) <- c('foo', 'bar', 'baz')
> df
  foo bar baz
1   1   0 100
2  NA   2   1
3   3  NA  20

```

### Handling NA

    complete.cases

```R

> v1 <- c(1, NA, 3)
> v2 <- c(NA, 0.1, 0.3)

> df <- data.frame(v1, v2)
> df
  v1  v2
1  1  NA
2 NA 0.1
3  3 0.3

> complete <- complete.cases(df)
> complete
[1] FALSE FALSE  TRUE

> df[complete,]
  v1  v2
3  3 0.3


```

    na.omit


```R

> na.omit(d)
v1  v2
3  3 0.3

```
## Strings


### String composition

```R

> labels <- paste('+', 1:10, 's', sep='')
> labels

[1] "+1s"  "+2s"  "+3s"  "+4s"  "+5s"  "+6s"  "+7s"  "+8s"  "+9s"  "+10s"

> paste(1:5, 's', c('before', 'after'), sep='')

[1] "1s before" "2s after"  "3s before" "4s after"  "5s before"

```



# TraMineR

## dissmfacw
https://rdrr.io/cran/TraMineR/man/dissmfacw.html

    Multi-factor ANOVA from a dissimilarity matrix











* seqdef
* seqecreate
* seqefsub




