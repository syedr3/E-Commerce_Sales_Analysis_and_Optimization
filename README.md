# E-Commerce Sales Analysis and Optimization

## Project Title
**Predicting Online Sales: Analyzing Factors Influencing Product Pricing and Sales Performance**

## Authors
- Syed Ahmed Raza  
- Pranav Rajkumar  
- Vaibhav Sahai  
- Rutva Pandya

---

## Introduction
This project analyzes a dataset of over 120,000 online sales records sourced from Kaggle. The goal is to explore factors influencing product pricing and sales performance on an e-commerce platform. By building predictive models, the project seeks to answer questions such as:

- What features make a product more likely to sell?
- Can we predict sales revenue based on specific product features?

This analysis helps provide actionable insights to online businesses to optimize pricing, inventory, and marketing strategies for maximizing revenue.

### Dataset Overview
The dataset contains the following key variables:
- **Category**: Type of product sold (categorical).
- **Size**: Product size (categorical).
- **Date**: Date of the sale (date format).
- **Status**: Status of the sale (e.g., delivered, canceled; categorical).
- **Fulfillment**: Method of order fulfillment (categorical).
- **B2B**: Whether it is a business-to-business sale (binary).
- **Qty**: Quantity of the product sold (numeric).
- **Amount**: Sale amount in the respective currency (numeric, response variable).
- **Ship Service Level**: Shipping type (categorical).

### Objective
To develop predictive models to determine the factors contributing to pricing and sales performance and identify strategies for revenue optimization.

---

## Methodology
### Data Preprocessing
The dataset was cleaned and preprocessed as follows:
- Removed rows with missing or invalid data.
- Converted variables to appropriate data types.
- Extracted only relevant columns for analysis.

```R
main_data = read.csv("Amazon Sale Report.csv")
main_data = main_data[,c("Category", "Size", "Date", "Status", "Fulfilment", "B2B", "Qty", "Amount", "ship.service.level")]
main_data = na.omit(main_data)

# Converting variables to appropriate data types
main_data$Category = as.factor(main_data$Category)
main_data$Size = as.factor(main_data$Size)
main_data$Date = as.Date(main_data$Date, format = "%m-%d-%y")
main_data$Status = as.factor(main_data$Status)
main_data$Fulfilment = as.factor(main_data$Fulfilment)
main_data$B2B = as.factor(main_data$B2B)
main_data$ship.service.level = as.factor(main_data$ship.service.level)
```

### Models Tested
Five models were tested to evaluate performance:
1. **Additive Model**: All predictors included without transformation.
2. **Square Root Model**: Applied a square root transformation to `Qty`.
3. **Polynomial Model**: Included a quadratic term for `Qty`.
4. **Hypothesis 1 Model**: Explored interaction between `Qty` and `Status`.
5. **Hypothesis 2 Model**: Investigated interaction between `Category` and `B2B`.

### Model Performance
- **Adjusted R-Squared**: The Polynomial Model had the highest adjusted R-squared of 0.4696.
- **RMSE**: Hypothesis 1 Model performed best with the lowest RMSE for both training (204.86) and test (205.16) datasets.

---

## Results
### Key Findings
- **Polynomial Model**: Best overall model with strong predictive performance and reasonable complexity.
- **Hypothesis 1 Model**: Showed the lowest RMSE but was slightly outperformed by the Polynomial Model in adjusted R-squared.
- **Square Root Model**: Performed poorly, indicating that the square root transformation did not add value.

### Diagnostic Plots
Residuals and Q-Q plots for the Polynomial Model confirm that assumptions of linear regression (constant variance and normality) are met.

### ANOVA
The ANOVA results confirm that the Polynomial Model provides a statistically significant improvement in fit compared to simpler models.

---

## Conclusion
The Polynomial Model emerged as the best approach to predict sales revenue, effectively capturing the complex relationships between product features and sales performance. These insights can guide e-commerce platforms in:
- **Product Pricing**: Identifying optimal price points.
- **Inventory Management**: Stocking high-performing product categories.
- **Marketing Strategies**: Targeting features that drive sales.

---

## How to Use This Repository
1. Clone the repository:
   ```bash
   git clone https://github.com/syedr3/E-Commerce_Sales_Analysis_and_Optimization.git
   ```
2. Load the R script `Data_Analysis_Project.Rmd` in your RStudio.
3. Ensure the dataset `Amazon Sale Report.csv` is in the working directory.
4. Run the analysis to reproduce the results and plots.

---

## Contact
For questions or collaborations, please contact:
- **Syed Ahmed Raza**: [GitHub Profile](https://github.com/syedr3)
