# Titanic Survival Prediction

This learning project is based on the [Kaggle Titanic competition](https://www.kaggle.com/competitions/titanic). [`Titanic.ipynb`](Titanic.ipynb) prepares features with `Pipeline` and `ColumnTransformer`, compares `LogisticRegression` and `RandomForestClassifier`, evaluates both models on a holdout set and with five-fold cross-validation, and generates `submission.csv`.

## Setup

1. Download `train.csv` and `test.csv` from the [competition data page](https://www.kaggle.com/competitions/titanic/data). You may need to sign in and accept the competition rules.
2. Put both files next to `Titanic.ipynb` in this folder.
3. Run the following commands from this folder:

   ```bash
   python -m venv .venv
   source .venv/bin/activate
   python -m pip install -r requirements.txt
   jupyter lab Titanic.ipynb
   ```

4. Run the cells in order. The notebook reads CSV files from the current folder and writes `submission.csv` there. On Windows, activate the environment with `.venv\Scripts\activate` instead.

## Results from the saved run

| Model | Holdout accuracy | Mean five-fold CV accuracy on the training split |
| --- | ---: | ---: |
| Logistic Regression | 0.799 | 0.80 |
| Random Forest | 0.802 | 0.81 |

The data is split 70% for training and 30% for validation, stratified by survival, with `random_state=42`. After comparison, the random forest is trained on all of `train.csv` and produces predictions for the 418 rows in `test.csv`. The notebook does not report a Kaggle leaderboard score.

## Limitations

- The notebook includes outputs from an earlier run. Results can vary with different library versions.
- Model selection and evaluation use the same provided training dataset. There is no separate labeled test set.
- Some narrative notes in the notebook are outdated or imprecise. For example, they mention missing values in `Cabin`, although the model does not use that column. The metrics above come from the code outputs.
- Feature coefficients and importance values are exploratory; they do not establish causation.
