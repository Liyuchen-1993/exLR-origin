# **exLR-origin**

*A computational approach to robustly enumerating the abundance of tissue-cellular origins using circulating exLR-seq profiles*

 

## **Summary**

This repository contains the source R Codes and two reference signature matrixes of exLR-origin approach to estimate the relative and absolute fraction of hemopoietic and tissue components from exLR-seq data, it also applies the detail description of model constructing process so that others can replicate our deconvoluting results and use our candidate machine learning method on other types of sequencing data.

 

## **Download and Install**

Software requirements: R version 3.4.2 or later (dependencies below might not work properly with earlier versions). It is recommended to manipulate our R script on windows platform. You can type the following command to download the latest R packages for exLR-origin as follow:

```
install.packages("MASS")

install.packages("glmnet")

install.packages("pracma")

install.packages("nnls")

install.packages("e1071")

install.packages("parallel")

install.packages("preprocessCore")
```

After installing, you can respectively load these packages with R command library("xxx").

For more detailed usage instructions, see our manuscript on the journal of Molecules.

 

## **Main strategy and detail description of model construction**

The conception of exLR-origin is to find the solution of a convolution equation in the form: AX = B, where A is the transcriptome mixture of the exLR-seq sample, B is the comparable signature matrix for the expression of genes in all including types cells and X is the vector of relative/absolute proportions of all cell subsets. Additionally, we have compared the six state-of-the-art machine learning algorithm and a nu–support vector regression (ν-SVR) model was finally included. 

Three main steps were included in our exLR-origin approach. The first step is to perform zero-mean normalization on the input exLR-seq expression data. The second step is parameter selection. The ν -SVR model with a linear kernel was tested with different values of ν (range from 0 to 1) and the parameter with the lowest root mean square error (RMSE) was kept for variable shrinking and model construction. Finally, the relative/absolute proportions of exLRs origin in each sample were calculated based on these optimized parameters.