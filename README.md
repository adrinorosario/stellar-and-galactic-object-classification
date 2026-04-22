# Stellar and Galactic Object Classification

Classify stellar and galactic objects such as stars, galaxies, or quasars using photometric and spectral data by leveraging classical machine learning (ML).

## Objective
The goal is to automate the classification of celestial bodies using spectral and photometric data from the Sloan Digital Sky Survey (SDSS). We also apply feature importance analysis to interpret which parameters drive the classification and evaluate model robustness across different data distributions.

## Problem it Solves
Manual classification of millions of astronomical objects is impossible. This project provides a high-accuracy, interpretable pipeline to classify stars, galaxies, and quasars from massive photometric datasets.

## Why it Matters
Automated classification is the backbone of modern large-scale sky surveys. Efficient identification of quasars and galaxies is essential for cosmological studies and mapping the large-scale structure of the universe.

## Constraints
* **Data Bias**: The impact of data ordering (e.g., by $r$-magnitude) on classification bias and model performance.
* **Feature Selection**: High-dimensional datasets require dropping identifiers like `objID` to ensure the model learns true physical patterns.
* **Interpretability**: A critical requirement for astronomical research where the "why" of a classification is as important as the prediction itself.

## Approach
* **Exploratory Data Analysis (EDA)**: Investigating the distribution of magnitudes across different color filters ($u, g, r, i, z$).
* **Modeling Experiments**: Systematic evaluation of **Decision Trees** using multiple train-test split ratios ($80:20$, $67:33$, $90:10$).
* **Feature Importance**: Using entropy and information gain to identify the most discriminative photometric features.

## Architecture
The project utilizes a classical machine learning pipeline built with **Scikit-Learn**:
* **Baseline Model**: Decision Tree Classifier with entropy criterion and a max depth of 3 for high interpretability.
* **Preprocessing**: Feature scaling and removal of non-physical identifiers.

## Implementation Notes
* **Criteria**: `criterion='entropy'` used for splitting decisions.
* **Visualization**: `graphviz` used to generate and analyze the decision tree structure.
* **Evaluation**: Extensive use of confusion matrices and classification reports.

## Results
| Metric | Star (Class 0) | Galaxy (Class 1) | Quasar (Class 2) |
| :--- | :---: | :---: | :---: |
| **Precision** | $0.99$ | $0.96$ | $0.93$ |
| **Recall** | $1.00$ | $0.93$ | $0.96$ |
| **F1-Score** | $1.00$ | $0.94$ | $0.95$ |

* **Overall Accuracy**: $96.26\%$ on a 15,000 SDSS sample.

## Trade-offs
* **Simple Models**: Decision trees are highly interpretable but may suffer from high variance on larger, noisier datasets compared to ensemble methods like Random Forests.
* **Feature Space**: Dropping certain photometric features improved generalization at the cost of some fine-grain classification power.

## Reflection
Photometric and spectral data provide highly separable feature spaces for stellar and galactic classification, allowing simple models to achieve excellent performance. Future extensions could involve testing XGBoost or LightGBM for even higher accuracy.

## Tech Stack
* **Language**: Python
* **Libraries**: Scikit-Learn, Pandas, NumPy, Matplotlib, Seaborn, Graphviz

## Project Type
Machine Learning / Astronomy
