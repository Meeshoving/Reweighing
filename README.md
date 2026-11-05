# Bias mitigation with Reweighing

This repository evaluates **Reweighing** (Kamiran & Calders, 2012) as a pre-processing method for reducing bias in classification. It uses three benchmark datasets: Adult, German Credit and COMPAS.

The notebook `reweighing_bias_mitigation.ipynb`:

1. measures demographic parity difference (DP_Diff), the disparate impact ratio (DIR) and consistency on the original labels,
2. makes a stratified 70/30 train/test split,
3. learns the reweighing weights on the training data with [AIF360](https://github.com/Trusted-AI/AIF360) and trains a logistic regression with them,
4. reports DP_Diff, DIR, consistency and accuracy on the test set,
5. compares the results before and after mitigation.

## How to run

AIF360 supports Python 3.8–3.11, so a Python 3.11 environment is recommended.

Open `reweighing_bias_mitigation.ipynb` in Jupyter or VS Code and run all cells. The first cell installs the required packages (`aif360`, `scikit-learn`, `pandas`).

The datasets are read directly from their online sources (UCI and ProPublica), so no data files are needed.

## Datasets and protected attributes

| Dataset | Protected attribute | Privileged group | Favourable label |
|---|---|---|---|
| Adult | sex | male | income > $50K |
| German Credit | age | older than 25 | good credit risk |
| COMPAS | race | Caucasian | no reoffence within two years |

## Reference

F. Kamiran and T. Calders (2012). Data preprocessing techniques for classification without discrimination. *Knowledge and Information Systems*, 33(1), 1–33. https://doi.org/10.1007/s10115-011-0463-8
