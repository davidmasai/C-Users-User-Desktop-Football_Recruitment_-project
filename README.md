# FIFA 18 Player Valuation and High-ROI Scouting

## Overview
This project focuses on **predicting high-ROI (Return on Investment) football players** using the **FIFA 18 dataset**. The objective is to help clubs with limited budgets identify undervalued players with high resale potential. By leveraging **machine learning models and exploratory data analysis (EDA)**, we aim to create a data-driven scouting framework that optimizes player recruitment.

## Business Understanding
Football clubs operate under financial constraints, making data-driven recruitment crucial. The project follows a **Moneyball-inspired approach** to scouting, identifying hidden gems who can provide strong on-field performance and significant future transfer value. We aim to develop a predictive model that estimates player value efficiently, helping clubs **maximize returns on player investments**.

## Libraries Used
The following Python libraries were used for **data manipulation, visualization, and modeling**:

- **Pandas**: Data manipulation and preprocessing
- **NumPy**: Numerical computations
- **Matplotlib & Seaborn**: Data visualization
- **Scikit-learn**: Machine learning modeling and evaluation
- **Statsmodels**: Regression analysis
- **XGBoost**: Advanced tree-based modeling

## Data & Preprocessing
### Data Source
The dataset is derived from **FIFA 18 player statistics**, including key attributes like **Overall, Potential, Age, Value, Wage, and various technical, mental, and physical attributes**.

### Data Cleaning
- **Handling missing values**: Players with incomplete data were either imputed or removed.
- **Feature engineering**: Creating aggregate attributes (e.g., **Technical, Mental, Physical attributes**).
- **Standardizing monetary values**: **Value and Wage were cleaned and scaled** for better model performance.
- **Log transformation**: Log-transformed **player Value** to handle skewness.

## Exploratory Data Analysis (EDA)
EDA was performed to uncover patterns and relationships among key player attributes. Key insights include:

- **High correlation between Potential and Market Value** 📈
- **Physical attributes are undervalued in player pricing** 🤔
- **Young players with high Potential but low Overall often present high ROI opportunities** 💡

### Key Visualizations:
1. **Correlation Heatmap**: Understanding relationships between player attributes and value.
   ![Correlation Heatmap](images/correlation_heatmap.png)
2. **Value vs. Age Scatter Plot**: Identifying undervalued young talents.
   ![Value vs. Age](images/age_and_value.png)
3. **Wage vs. Value Distribution**: Highlighting wage inefficiencies.
   ![Wage vs. Value](images/wage_vs_value.png)
4. **Position-Based ROI Analysis**: Comparing different positions to identify undervalued roles.
   ![Position-Based ROI](images/position_based_roi.png)

## Modeling Approach
We built predictive models to estimate **player value** based on relevant attributes.

### Baseline Model
- **Linear Regression (Statsmodels)**: Establishing initial relationships between attributes and value.

### Advanced Models
- **Decision Trees & Random Forests**: Handling non-linearity in player valuation.
- **XGBoost**: Optimized tree-based model for robust prediction.
- **GridSearchCV**: Hyperparameter tuning for model improvement.

### Performance Metrics
- **R² Score**: Measuring model explanatory power.
- **Mean Absolute Error (MAE)**: Assessing prediction accuracy.

## Insights & Application to Scouting
1. **High-Potential Youngsters**: Identifying **players under 25 with strong attributes** but undervalued market prices.
2. **Position-Based Value Gaps**: Some positions (e.g., defensive midfielders) tend to be underpriced relative to impact.
3. **Wage Efficiency**: Clubs can optimize wage-to-value ratio to maximize squad profitability.
4. **Transfer Market Arbitrage**: Data-driven negotiation strategies based on model predictions.

## Future Work
- **Expanding dataset** to include more historical FIFA editions.
- **Integrating real-world transfer data** for improved ROI measurement.
- **Enhancing feature engineering** by including playing style and performance metrics.
- **Deploying an interactive dashboard** for real-time scouting insights.

## Conclusion
This project showcases how **data science can revolutionize football scouting** by providing clubs with actionable insights on **high-ROI player acquisitions**. By combining **EDA, predictive modeling, and business strategy**, we create a **powerful recruitment tool for budget-conscious teams**.

---
🚀 *For code, analysis, and implementation details, check the Jupyter Notebook in this repository!*
