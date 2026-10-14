# House Prices Prediction (Kaggle)

Predicting house sale prices from 79 features, for the Kaggle competition
[House Prices - Advanced Regression Techniques](https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques).

## Results

| Model | Kaggle score (RMSE on log price, lower is better) |
|---|---|
| Random Forest | 0.14408 |
| Gradient Boosting (full data) | 0.13216 |
| Gradient Boosting (2 outliers removed) | 0.13645 |
| **XGBoost (full data)** | **0.13132** |

## What I did

1. Loaded and explored the data, then encoded the categorical features (317 columns after encoding).
2. Trained on the log of the price, which is what the competition metric measures.
3. Compared models using 5-fold cross-validation, then confirmed on Kaggle.

## What I learned

- **Removing outliers can hurt.** I removed two very large, very cheap houses from the training set. Cross-validation improved, but the Kaggle score got worse. The cross-validation got easier because I had removed the hardest examples, so the comparison was unfair.
- When I looked into it, the test set contains one very large house (Id 2550). The model trained without the outliers predicted about 765K for it, versus about 269K before. I did not know its true price, but the score change was consistent with this one house.
- **Small score differences are mostly noise.** XGBoost beat Gradient Boosting by about 0.001, which is within the variation between CV folds. I would not claim it is better with confidence.

## How to run

1. Download `train.csv` and `test.csv` from the Kaggle competition page.
2. Put them in a Google Drive folder named `house-prices`.
3. Open the notebook in Google Colab and run all cells.

## Tools

Python, pandas, NumPy, scikit-learn, XGBoost, Google Colab.
