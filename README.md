# README: Predicting High ROI Players in FIFA 18 Dataset

## Project Overview
This project aims to assist football clubs in **identifying high-ROI (Return on Investment) players** using data-driven scouting strategies. By leveraging the **FIFA 18 dataset**, we develop a predictive model to uncover undervalued talents with high resale potential. The objective is to enable cost-effective recruitment decisions, particularly for clubs with limited budgets, similar to the approach used by **Brentford FC before their 2021 Premier League promotion**.

## Business Understanding
The transfer market is often inefficient, with clubs overpaying for players while missing hidden gems. **Small and mid-tier clubs must optimize spending by acquiring players with high resale value**—young talents with strong attributes but undervalued in the market. Inspired by **Moneyball principles**, this project seeks to answer:

- **Which players provide the best ROI based on their attributes?**
- **How can we quantify a player's true market value?**
- **What metrics best predict a player's future worth?**

## Data & Methods
### Dataset
The project utilizes the **FIFA 18 dataset**, which includes player attributes such as:
- **General Information**: Name, Age, Nationality, Club, Value, Wage
- **Technical Attributes**: Dribbling, Passing, Shooting, etc.
- **Physical Attributes**: Stamina, Acceleration, Strength
- **Mental Attributes**: Vision, Composure, Work Rate
- **Defensive Attributes**: Marking, Standing Tackle, Interceptions

### Target Variable
The key outcome we aim to predict is **a player's market value (log-transformed for normalization)**.

### Feature Engineering
To enhance model performance, we engineered new features:
- **Potential - Overall Difference**: Indicates growth capacity
- **Percentile-Based Estimation**: Places players in comparative percentiles
- **Value Efficiency Ratio (VER)**: Compares performance against cost
- **Position-Specific Attributes**: Weighted attributes based on roles (e.g., a winger’s dribbling vs. a defender’s tackling)

### Data Preprocessing
- **Handling Missing Values**: Imputation and removal of null data
- **Standardization**: Features scaled using **StandardScaler**
- **Log Transformation**: `Value` converted to `log(Value + 1)` to handle skewness
- **Cleaning Wage Data**: Removing currency symbols (e.g., '€135K') and converting to numerical format

## Modeling Approach
We use a stepwise approach:
1. **Baseline Model**: Linear Regression to establish a reference
2. **Improved Model**: Decision Tree with hyperparameter tuning
3. **Fine-Tuned Model**: GridSearch-optimized model for precision improvement
4. **Feature Selection**: Recursive Feature Elimination (RFE) to refine the most predictive attributes
5. **Validation**: Cross-validation techniques to ensure model generalization

### Performance Metrics
Given our business goal, **precision is prioritized** to minimize false positives (overvaluing poor investments). Key evaluation metrics:
- **Mean Absolute Error (MAE) & Root Mean Squared Error (RMSE)**
- **R-Squared (R²) for model explainability**
- **Feature Importance Scores** to justify selection

## Insights & Application to Scouting
### Bivariate Analysis & Visualizations
We analyze key relationships between **player attributes and market value**, using:
- **Heatmaps**: Show correlation between attributes (e.g., Potential vs. Value)
- **Boxplots**: Compare high ROI vs. low ROI players across attributes
- **Scatter Plots**: Value vs. attributes for trend detection
- **Decision Boundary Visualizations**: Illustrate model classifications

### How This Helps in Scouting
- **Identifying Hidden Gems**: Find undervalued players who outperform their market price
- **Optimized Recruitment**: Filter candidates based on high potential growth at low cost
- **Position-Specific Insights**: Customize valuation strategies for different roles
- **Risk Assessment**: Mitigate transfer risks by avoiding overpriced low-ROI players

## Limitations & Future Work
### Current Limitations
- **Historical Dataset**: FIFA 18 data may not fully reflect modern trends
- **Market Dynamics**: External factors like injuries, transfers, and league competitiveness are not modeled
- **Sample Bias**: Dataset may over-represent certain leagues or positions

### Future Enhancements
- **Incorporate real-world transfer data** for improved ROI validation
- **Apply deep learning techniques** (e.g., neural networks for complex patterns)
- **Expand dataset** to include FIFA 19–21 for temporal validation

## Conclusion
This project provides a data-driven framework for football scouting, helping clubs make **informed, cost-effective transfer decisions**. By leveraging advanced analytics, we identify **high-potential, undervalued players** who can yield significant ROI—transforming recruitment strategies in the modern football market.


