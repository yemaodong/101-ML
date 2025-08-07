Code Overview
Title: Ten Algorithmic Combinations for Variable Selection and Prognostic Model Construction

Algorithms Included: Lasso, Ridge, Elastic Net (Enet), Stepwise Cox (StepCox), Survival Support Vector Machine (survivalSVM), CoxBoost, SuperPC, Partial Least Squares Regression for Cox (plsRcox), Random Survival Forest (RSF), Gradient Boosting Machine (GBM)

Description
Under a cross-validation framework, this pipeline performs variable selection using one algorithm and constructs a prognostic model using another. A total of 101 combinations are evaluated by calculating the concordance index (C-index) on external datasets (or including the training set). The performance of each model combination is visualized using a heatmap.

Algorithm Inputs
Training Expression Matrix:

Rows represent features (e.g., SYMBOL/ENSEMBL, with partial overlap with test set)

Columns represent samples

Format: Train_expr.txt

Training Survival Data:

Rows represent samples

Columns include survival status and survival time (variable names must be specified in the code)

Format: Train_surv.txt

Test Expression Matrix:

Same format as training expression matrix

Format: Test_expr.txt

Test Survival Data:

Rows represent samples

Columns include survival status, survival time, and a variable indicating cohort information

Format: Test_surv.txt

Note: It is recommended to pre-filter the expression matrix to retain a few dozen to a few thousand relevant features for optimal model selection. Otherwise, the runtime may be significantly prolonged. (The example files use TGFB-related genes.)

Applicable Scenarios
This code is suitable for situations where numerous variables have unclear prognostic significance and simultaneous variable selection, model selection, and prognostic modeling are required.

Output
Trained models for all 101 algorithm combinations (model.rds)

Evaluation results on the test set (or including training set) as a concordance index matrix (Cindex_mat)

Heatmap visualization of model performance (Cindex.pdf)

Reference
Machine learning-based integration develops an immune-derived lncRNA signature for improving outcomes in colorectal cancer DOI: s41467-022-28421-6
