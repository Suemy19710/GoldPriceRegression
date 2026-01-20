# GoldPriceRegression

This project applies regression models to financial market data to predict gold prices based on related commodity prices, currency exchange rates, and market indicators.

---

## Dataset

Source: Kaggle — *Financial Data*  
(Contains daily financial indicators such as commodity prices, market indices, and currency pairs.)

**Target variable:**
- `gold_high` (gold price high value of each day)

**Example predictors:**
- silver prices & volume
- oil prices
- palladium prices
- EUR/USD exchange rate
- market activity features

---


## 🧠 Multicollinearity Analysis (VIF)

Financial markets are highly correlated — e.g., precious metals and commodities move together.  

Because in the dataset some features contain the same information meaning overlapping or redundant information, using Variance Inflation Factor (VIF) for reducing unnecessary features. 

Using Multicollinearity when linear-based model, if using Random Forest, XGBoost, NN dont need to use this method. 

These features which have VIF:

`Index(['sp500 volume', 'sp500 high-low', 'nasdaq volume', 'usd_chf', 'eur_usd',
       'silver high', 'silver volume', 'silver high-low', 'oil high',
       'oil volume', 'oil high-low', 'platinum volume', 'platinum high-low',
       'palladium high', 'palladium volume', 'palladium high-low', 'gold high',
       'gold volume', 'month', 'day', 'day_of_week'],
      dtype='object')`

---
## Regression Task

Unlike classification, this task predicts a **continuous value**.  
In this project, I trained different regression models: Linear Regression, Polynomial Regression, Ridge Regression, Lasso Regression, SVR, Decision Tree Regression, Random Forest Regression. 

I chosen Randome Forest as a final model with R² ≈ **0.99**. 

-- 

## 📉 Linear Regression Interpretation (Economics)

Coefficients indicated relationships such as:

| Feature         | Relationship | Interpretation |
|-----------------|-------------|----------------|
| silver high     |  18.140721     | Gold and silver co-move as monetary metals |
| oil high        | 10.540031     | Inflation hedge / commodity cycle correlation |
| palladium high  | 5.616050     | Precious metals cluster effect |
| silver volume   | 1.881492     | Market activity may indicate demand |
| eur_usd         | -11.177142     | Currency-gold inverse relation (USD dominance) |

