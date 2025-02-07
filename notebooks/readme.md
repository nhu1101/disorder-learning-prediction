This folder contains the notebooks used to: 
1. Feature-Engineering data 
2. Cross-validation
3. Model-training & Evaluation

## B. Cross-Validation: 

Cross-validation strategy designed to optimize classification thresholds for the 'sii' label column, derived from binning a continuous numeric column 'PCIAT-PCIAT_Total'. The strategy leverages k-fold cross-validation, threshold optimization using the Powell method, and evaluates performance using Cohen's kappa score

#### Step 1: Data Preparation

The label column sii consists of discrete values [0, 1, 2, 3], which are derived by binning the continuous pdi column based on a set of thresholds.

The goal is to optimize these thresholds to improve classification performance.

#### Step 2: K-Fold Cross-Validation

Implement k-fold cross-validation, where the dataset is split into k folds.

In each iteration, (k-1) folds are used as the training set, and the remaining fold is held out for validation (out-of-folds).

Repeat this process for each fold, ensuring every data point is used for both training and validation once.

#### Step 3: Learning and Predicting 'PCIAT-PCIAT_Total'

Train a predictive model on the training folds to learn the pdi values.

Use the trained model to predict pdi on the out-of-fold validation set.

#### Step 4: Threshold Optimization for sii Using Powell’s Method

Optimize the binning thresholds for sii based on the pdi predictions from the training set.

Utilize Powell’s method, a derivative-free optimization technique, to find the set of thresholds that maximize Cohen’s kappa score.

#### Step 5: Applying Optimized Thresholds to Out-of-Fold Predictions

Apply the optimized thresholds to convert pdi predictions into sii categorical labels in the validation set.

#### Step 6: Evaluate Performance Using Cohen's Kappa Score

Compute Cohen's kappa score between the predicted sii labels and the actual sii labels in the out-of-fold set.

Store the computed kappa score for further analysis.

