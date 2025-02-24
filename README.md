# FIFA 18 Player Valuation Project

## Project Overview
This project aims to help football clubs with tight budgets identify high-potential players with strong resale value. We use data from FIFA 18 to develop a classification model that predicts player profitability.

## Business Problem
Football clubs with limited budgets must make strategic player investments. Identifying undervalued players who can develop and be sold for a profit is crucial. Using historical FIFA 18 data, we apply machine learning techniques to predict which players will yield high resale value.

## Data Used
The dataset includes key attributes such as:
- Age
- Overall rating
- Potential rating
- Value
- Wage
- Special attributes (skills, weak foot, etc.)
- Position

## Methodology
### 1. Data Preprocessing
- Handled missing values
- Encoded categorical variables
- Scaled numerical features

### 2. Feature Engineering
- **Market Value Efficiency:** Measures how efficiently a player’s current attributes contribute to their market value. Helps identify undervalued players.
- **Value-for-Money Index:** Evaluates a player's potential against their market value. Crucial for identifying high-potential players available at a low price.
- **Adjusted Value Efficiency Ratio (VER):** Combines several factors to quantify a player's expected growth relative to their current status.
- **Hidden Gem Metric:** Identifies players who perform well in terms of Adjusted VER, Market Value Efficiency, and Value-for-Money Index, while being undervalued.

### 3. Modeling Approach
Correlation between features
![Feature Correlations](images/feature%20correlation.png)
#### Baseline Model
- **Logistic Regression:** Start with Logistic Regression because it's a simple model that offers a good baseline.
  - Logistic Regression is a linear model used for binary classification. It uses a sigmoid function to predict probabilities and assigns class labels based on a threshold.
  - **Why Start Here?** It's a great starting point for classification tasks as it’s easy to implement, understand, and interpret. You can gauge the baseline performance and establish benchmarks.
  - **Predictors:** Age, Potential, Overall, Wage
  - **Initial Performance:** Accuracy: 98%, Precision: 98%, Recall: 1.00 due to class imbalance
  - Addressed class imbalance using SMOTE.
  - Even after Tuning and SMOTE was applied to balance the training data, the imbalance still affects the performance.
  - The model shows excellent recall for the minority class (hidden gems), but precision suffers, leading to many false positives for class 1.
  - the Confusion Matrix :
    
  ![the Confusion Matrix](images/confusion%20matrix%20model%201%20tuned.png)

#### Overfitting Analysis
- **Training Performance:** Precision for Class 1 is 0.50, Recall for Class 1 is 1.00.
- **Indicators of Overfitting:** High recall for class 1 in training but poor precision.

#### Decision Tree
- Captures non-linear patterns in player valuation.
- **Why Transition to Decision Trees?** When Logistic Regression doesn’t capture the complexity of the data (linear relationships), Decision Trees provide a better fit.
- **Iteration Steps:**
  - **Model Initialization:** Train a Decision Tree model.
  - **Tuning:** Hyperparameters such as `max_depth` and `min_samples_split` may need tuning to avoid overfitting.
  - **Model Evaluation:** Evaluate using similar metrics as logistic regression. Visualize the tree if needed to understand the splits. Consider cross-validation to test robustness.

#### Random Forest
- Random Forest is an ensemble of Decision Trees. By averaging many trees (or using majority voting for classification), it generalizes better than a single Decision Tree.
- **Why Transition to Random Forest?** Random Forests are generally more robust and can handle overfitting much better than a single Decision Tree.
- **Iteration Steps:**
  - **Model Initialization:** Train a Random Forest model.
  - **Tuning:** Experiment with hyperparameters such as `n_estimators`, `max_depth`, and `min_samples_split`.
  - **Model Evaluation:** Compare performance to the Decision Tree and Logistic Regression models. Cross-validation can be helpful to ensure robustness.

## Evaluation Metrics
We focused primarily on **precision**, ensuring that the model correctly identifies profitable players while minimizing false positives.

## Visualizations & Interpretations
We generated several visualizations to support our analysis:

### 1. Player Distribution in the Dataset
![Top 10 Countries with Player Distribution](images/top%2010%20countries%20with%20player%20dsitribution.webp)

### 2. Cluster Analysis of Players
![Cluster Analysis](images/4_clusters.png)
- Players were segmented into four clusters based on key attributes like age, potential, and market value.
- This helped us identify distinct groups of players who might be undervalued gems.

### 3. Age vs. Market Value
![Age vs. Market Value](images/age%20and%20value.webp)
- Younger players tend to have a higher resale value potential, while older players depreciate quickly.
- Clubs should prioritize investing in players under 25 to maximize resale opportunities.

### 4. Age Distribution
![Age Distribution](images/Age%20Distribution.png)
- The dataset is skewed towards younger players, which aligns with the scouting approach of top clubs.

### 5. Average Age vs. Wage and Market Value
![Average Age vs. Wage and Market Value](images/average%20age%20wage_value.png)
- Shows how wages and market value change with age.
- High-value players tend to be in the mid-20s, indicating peak resale potential.

### 6. Average Wage & Value by Rating
![Average Wage & Value by Rating](images/Average%20Wage_Value%20by%20Rating.png)
- Highlights how wage scales with a player's overall rating.
- Some players may be overpaid relative to their resale potential.

### 7. Overall & Potential vs. Age
![Overall & Potential vs. Age](images/Overall%20and%20Potential%20vs%20Age.png)
- Players with high potential tend to be younger, reinforcing the importance of scouting for future growth.

### 8. Average Overall by Country
![Top 15 Avg. Overall by Country](images/top%2015%20Avg.%20Overall%20by%20Country.webp)

## Conclusion
- **Precision was the key metric**, ensuring we minimize investment in unprofitable players.
- **Random Forest provided better insights** into which features drive future resale value.
- **Investing in young, high-potential players is the best strategy** for financial sustainability.
