# Regression

To explore the association between multiple predictors and a continuous dependent variable, regression analysis can be used. In this example, a dataset/dataframe called `dat` contains three continuous variables, `independentVariable`, `secondIndependentVariable` and `dependentVariable`.

## SPSS

```
DATASET ACTIVATE dat.
REGRESSION
  /DEPENDENT dependentVariable
  /METHOD ENTER independentVariable secondIndependentVariable
  /STATISTICS COEF CI(95) R ANOVA.
```

To order a plot:

```
GRAPH
  /SCATTERPLOT=independentVariable WITH dependentVariable BY secondIndependentVariable.
```

Note that this only works if the second variable, `secondIndependentVariable`, is categorical. If it is continuous, it is probably a good idea to create a categorical variable to enable visualisation.

## R

```r
regr(dependentVariable ~ independentVariable * secondIndependentVariable,
     data=dat);
```

To also order a plot:

```r
regr(dependentVariable ~ independentVariable * secondIndependentVariable,
     dat=dat, plot=TRUE);
```