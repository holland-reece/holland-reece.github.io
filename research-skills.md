---
title: Holland Reece Brown
layout: default
---


# Research Skills
## Analysis of high-dimensional, multi-modal datasets
- As a research assistant, I analyzed high-dimensional brain imaging datasets comprised of image time series with repeated measures for clinical and non-clinical groups.

- Here is an example of a single measure (one brain scan) in which each voxel corresponds to a spatial location in the brain and each cell represents the signal in a voxel over every frame of the scan.

> |          | Frame_1 | Frame_2 | ⋯   | Frame_m |
> |----------|--------|--------|-----|--------|
> | Voxel_1   |   ⋯    |   ⋯    | ⋯   |   ⋯    |
> | Voxel_2   |   ⋯    |   ⋯    | ⋯   |   ⋯    |
> | ⋯        |   ⋯    |   ⋯    | ⋯   |   ⋯    |
> | Voxel_n   |   ⋯    |   ⋯    |  ⋯   |   ⋯    |

- I helped develop a [preprocessing pipeline](https://github.com/holland-reece/SE-fMRI-Pipeline-magnitude-fieldmaps) for human brain imaging data, incorporating machine learning-based tools such as Tedana to identify noise and separate it from signal to sharpen images and identify relevant changes over time.

- I then used mixed-effects linear models for repeated measures (mmrm) to quantify differences between clinical and non-clinical groups over several brain scans in randomized control trials for late-life depression and adolescent anxiety.

- In a cross-institutional colaboration, I helped develop analysis scripts for a brain imaging study in zebrafish larvae.

> Velez-Angel, 2024, [*bioRxiv*](https://doi.org/10.1101/2025.02.07.637118)
<br>

---

## Applying Explainable AI Methods to Real-World and Publicly Available Datasets

- Fitting deep learning models commonly used to analyze large datasets of medical images

- Experimentation with training techniques

- Comparison of [lasso and ridge regression techniques](https://github.com/holland-reece/ridge-vs-lasso-reg) using k-fold cross validation and forward feature selection

- Classification of MNIST data using a [logistic regression classifier](https://github.com/holland-reece/logreg-classifier-MNIST-demo)