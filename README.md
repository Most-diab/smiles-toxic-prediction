
#  Molecular Bioactivity Prediction Using Random Forests

## Overview
This project builds a **multi-label classification** model to predict the bioactivity of molecules using their SMILES representations. It leverages **Morgan fingerprints**, addresses class imbalance with **SMOTE**, and uses **Random Forests** to perform binary classification across multiple biological targets.

**Best validation score (mean ROC AUC):** `0.7646`

---

## Structure

```
data_train.csv          # Training dataset (SMILES + 11 bioactivity labels)
smiles_test.csv         # Test dataset (SMILES only)
final_output.csv        # Submission file with prediction probabilities
main.ipynb              # Main notebook for training and evaluation
README.md               # This file
```

## Usage

1. **Prepare the data:**
   - Place `data_train.csv` and `smiles_test.csv` in the root directory.

2. **Run the notebook or script:**
   - This will:
     - Convert SMILES to Morgan fingerprints.
     - Train one Random Forest per target using SMOTE for balancing.
     - Evaluate validation AUC.
     - Retrain on full data and output `final_output.csv`.

---

##  Methodology

- **Featurization:** SMILES strings are transformed into 1024-bit **Morgan fingerprints** using RDKit.
- **Modeling:** A separate **Random Forest classifier** is trained for each bioactivity target using:
  - `n_estimators=500`
  - `max_depth=12`
  - `class_weight='balanced'`
- **Handling Imbalance:** **SMOTE** is applied to each task to oversample the minority class.
- **Evaluation:** Performance is assessed using **ROC AUC**, averaged over all tasks.

---

## Results

| Phase        | Mean AUC |
|--------------|----------|
| Validation   | 0.7646   |
| Submission   | Generated in `final_output.csv` |


---

## Author

**Mostafa Ali**  
Built as part of a bioinformatics coursework.
