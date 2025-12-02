This project builds an end-to-end data pipeline for analyzing restaurant ingredient usage, computing quarterly profitability, and forecasting supply needs using machine learning.

1. Data Preparation
Loads sales and production recipe datasets.
Cleans column names, fixes date formats, removes currency symbols, and computes:
Gross margin
Gross margin %
Corrects recipe typos and standardizes ingredient names.

2. Ingredient Demand Calculation

Merges sales with recipes to derive ingredient demand per dish.
Calculates:
Total ingredient usage
Daily ingredient demand
Ingredient demand with 5% wastage adjustment
Detects outlier usage days.
Generates trend visualizations and heatmaps for top ingredients.

3. Cost Allocation

Allocates dish-level food cost proportionally across ingredients using recipe shares.
Computes the average cost per ingredient (RM) for modeling.

4. Quarterly Analysis

Assigns each sale to a quarter (Q1–Q4).
Calculates for every ingredient per quarter:
Total supply, demand, and shortage/surplus
Revenue, cost, profit, and profit margin
Saves the combined results to quarterly_ingredient_data.csv.

5. Forecasting Model
Loads the quarterly dataset and performs:
Label encoding
Quarter indexing
Exponential Smoothing (ES) forecast as a new feature
Trains an XGBoost regressor to predict future supply quantity.
Uses Group K-Fold to ensure ingredient-level separation.
Evaluates model performance using:
MAE
Profit & loss comparison between predicted and actual supply

6. Outputs
quarterly_ingredient_data.csv — processed dataset for modeling
Model performance metrics
Profit/loss comparison for each ingredient and quarter
Visualizations (trends, heatmaps, outlier reports)
