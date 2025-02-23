# FIFA 18 Player Valuation Project

## Project Overview
This project aims to help a football club with a tight budget identify high-potential players with strong resale value. We use data from FIFA 18 to develop a classification model that predicts player profitability.

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
1. **Data Preprocessing:**
   - Handled missing values
   - Encoded categorical variables
   - Scaled numerical features
   
2. **Feature Engineering:**
   - Created percentile-based metrics to evaluate player value efficiency
   - Used Value Efficiency Ratio (VER) to estimate cost-effectiveness
   
3. **Modeling Approach:**
   - **Baseline Model:** We started with a simple logistic regression model to establish a reference point.
   - **Decision Tree:** Introduced to capture non-linear patterns in player valuation.
   - **Random Forest:** Used for improved predictive power and robustness, helping us understand the impact of various features on future resale value.

## Evaluation Metrics
Since this is a classification problem, we focused primarily on **precision**, ensuring that the model correctly identifies profitable players while minimizing false positives.

## Visualizations & Interpretations
We generated several visualizations to support our analysis:

### 1. Cluster Analysis of Players
![Cluster Analysis](images/4_clusters.png)
- Players were segmented into four clusters based on key attributes like age, potential, and market value.
- This helped us identify distinct groups of players who might be undervalued gems.

### 2. Age vs. Market Value
![Age vs. Market Value](images/age%20and%20value.webp)
- Younger players tend to have a higher resale value potential, while older players depreciate quickly.
- Clubs should prioritize investing in players under 25 to maximize resale opportunities.

### 3. Age Distribution
![Age Distribution](images/Age%20Distribution.png)
- The dataset is skewed towards younger players, which aligns with the scouting approach of top clubs.

### 4. Average Age vs. Wage and Market Value
![Average Age vs. Wage and Market Value](images/average%20age%20wage_value.png)
- Shows how wages and market value change with age.
- High-value players tend to be in the mid-20s, indicating peak resale potential.

### 5. Average Wage & Value by Rating
![Average Wage & Value by Rating](images/Average%20Wage_Value%20by%20Rating.png)
- Highlights how wage scales with a player's overall rating.
- Some players may be overpaid relative to their resale potential.

### 6. Overall & Potential vs. Age
![Overall & Potential vs. Age](images/Overall%20and%20Potential%20vs%20Age.png)
- Players with high potential tend to be younger, reinforcing the importance of scouting for future growth.

## Conclusion
- **Precision was the key metric**, ensuring we minimize investment in unprofitable players.
- **Random forest provided better insights** into which features drive future resale value.
- **Investing in young, high-potential players is the best strategy for financial sustainability.
