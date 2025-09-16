# FIFA 18 Player Valuation Project

## Project Overview
This project aims to help football clubs with tight budgets identify high-potential players with strong resale value. We use data from FIFA 18 to develop a classification model that predicts player profitability.

## Business Problem
Football clubs with limited budgets must make strategic player investments. Identifying undervalued players who can develop and be sold for a profit is crucial. Using historical FIFA 18 data, we apply machine learning techniques to predict which players will yield high resale value. We take the current value and try to predict the future reslae value 


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
  - While this model provided a solid foundation and showed good performance on the training data, it exhibited limitations when applied to the test data, particularly in handling the class imbalance between the two classes (Hidden Gem vs. Non-Hidden Gem). Here’s a summary of the results from the logistic regression model:

Training Accuracy: 85.85%
The model performed well on the training data, achieving high accuracy and recall for classifying hidden gems.

Test Accuracy: 78.89%
While the model maintained relatively good performance on the test data, we observed a significant difference in precision and recall between the two classes.

Precision-Recall Trade-off:

Class 0 (Non-Hidden Gem): High precision (0.98), but some false positives (464).
Class 1 (Hidden Gem): High recall (0.98) but low precision (0.38), indicating that the model was too liberal in predicting hidden gems, leading to false positives.
  - the Confusion Matrix:
  
![the Confusion Matrix](images/confusion%20matrix%20model%201%20tuned.png)

#### Decision Tree
Why Switch to Decision Tree?
To improve performance, particularly in handling the class imbalance and providing more interpretable results, we have decided to move towards a Decision Tree model
- Captures non-linear patterns in player valuation.
- **Why Transition to Decision Trees?** When Logistic Regression doesn’t capture the complexity of the data (linear relationships), Decision Trees provide a better fit.
- **Iteration Steps:**
  - **Model Initialization:** Train a Decision Tree model.
  - **Tuning:** Hyperparameters such as `max_depth` and `min_samples_split` may need tuning to avoid overfitting.
  - **Model Evaluation:** Evaluate using similar metrics as logistic regression. Visualize the tree if needed to understand the splits. Consider cross-validation to test robustness.
  - the Decision Tree model has outperformed the Logistic Regression model, even after feature engineering in the logistic model. Let's break down the comparison based on the performance metrics you've provided:

Decision Tree vs. Logistic Regression Performance:
Decision Tree Model:

Training Accuracy: 96.16%
Test Accuracy: 96.37%
Precision (Test Data):
Class 0 (Non-Hidden Gems): 99%
Class 1 (Hidden Gems): 94%
Recall (Test Data):
Class 0: 94%
Class 1: 99%
Key takeaway: The Decision Tree is very good at correctly identifying both classes with high recall, especially class 1 (Hidden Gems). The model also maintains high precision, indicating that it does not misclassify many instances.

Logistic Regression Model:

Training Accuracy: 85.85%
Test Accuracy: 78.88%
Precision (Test Data):
Class 0: 1.00 
Class 1: 0.38  
Recall (Test Data):
Class 0: 76%
Class 1: 98%
Key takeaway: The Logistic Regression model performs differently "worse". However, Decision Trees are generally more flexible in capturing non-linear relationships, making them potentially better suited for capturing the complexities in this particular dataset, leading to better performance in this case.


#### Random Forest
- Random Forest is an ensemble of Decision Trees. By averaging many trees (or using majority voting for classification), it generalizes better than a single Decision Tree.
- **Why Transition to Random Forest?** Random Forests are generally more robust and can handle overfitting much better than a single Decision Tree.
- **Iteration Steps:**
  - **Model Initialization:** Train a Random Forest model.
  - **Tuning:** Experiment with hyperparameters such as `n_estimators`, `max_depth`, and `min_samples_split`.
  - **Model Evaluation:** Compare performance to the Decision Tree and Logistic Regression models. Cross-validation can be helpful to ensure robustness.

## Random Forest Confusion Matrix
![Confusion Matrix](images/random%20forest%20matrix)

Logistic Regression (Baseline):
Simple and interpretable, but may struggle with non-linear relationships in the data.
Provides insight into feature importance (coefficients).
Decision Tree:
More flexible than logistic regression.
Easy to interpret but prone to overfitting without pruning or hyperparameter tuning.
Random Forest (Tuned):
Ensemble model that typically performs better than a single decision tree.
Less prone to overfitting compared to decision trees and capable of handling complex data patterns.
Best for feature importance, with a more robust overall performance.
Final Thoughts:
After evaluating all the models, the Random Forest (with tuned hyperparameters) is gave the best overall performance due to its ability to generalize better and reduce overfitting. While the decision tree and logistic regression are valuable models, Random Forest often outperforms them on real-world datasets, especially when there are complex relationships between features.

When focusing on precision (as your primary metric), Random Forest was the best option, especially when dealing with an imbalanced dataset or complex feature interactions. However, if you need interpretability and simplicity, logistic regression is still a solid choice, especially for initial analyses or when explaining model results to non-technical stakeholders.

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

### 9. Correlation between Features
![Feature Correlations](images/feature%20correlation.png)

### 10. Confusion Matrix
![the Confusion Matrix](images/confusion%20matrix%20model%201%20tuned.png)

## Conclusion
- **Precision was the key metric**, ensuring we minimize investment in unprofitable players.
- **Random Forest provided better insights** into which features drive future resale value.
- **Investing in young, high-potential players is the best strategy** for financial sustainability.
