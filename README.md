# Engine Size Prediction in High-Performance Sports Cars

## Introduction

This project aims to predict the **engine size** (in liters) of high-performance sports cars using various performance and design characteristics such as horsepower, torque, 0-60 mph acceleration time, and car price. Engine size is a crucial determinant of a car's power, efficiency, and market value.

We use **regression analysis** to model this continuous response variable. The dataset consists of **1,007 observations** from well-known manufacturers like **Porsche, Ferrari, Lamborghini, and McLaren**, capturing a rich set of numerical and categorical features.

To ensure a representative evaluation, the dataset was **stratified by engine size** during train-test splitting, preserving distributional balance.

## Why?

Understanding what drives engine size is valuable for:

1. **Manufacturers** — to inform engineering, performance optimization, and regulatory compliance.  
2. **Consumers** — to evaluate performance vs. affordability.  
3. **Researchers** — to explore how powertrain variables interact.

By modeling engine size, we reveal insights into how characteristics like horsepower, torque, and acceleration relate to engine displacement. This can support **design decisions, pricing strategies, and consumer guidance**.

## Pre-Processing

We performed the following preprocessing steps:

1. Removed commas and converted the **Price** column to numeric.
2. Converted all performance metrics (**Horsepower, Torque, 0-60 MPH Time, Engine Size**) to numeric types.
3. Imputed missing values using **column means** to retain dataset integrity.
4. Ensured a clean structure with **0 missing values** after preprocessing.

We also checked for **multicollinearity** using Variance Inflation Factor (VIF) and found strong correlations between **horsepower and torque**, which is addressed in model selection.

## Summary Insights

- Engine Size shows a **bimodal distribution** centered around ~4L.
- Horsepower and Engine Size have a **strong positive correlation**.
- Horsepower and Price are also positively correlated, but with **high variability** at extreme values.
- Engine size varies significantly by **year** and **car make**, indicating shifts in design trends and brand performance focus.

## Visualizations Included

- Histogram of engine sizes  
- Scatter plots (Engine Size vs. Horsepower, Price vs. Horsepower)  
- Box plots (Engine Size by Year, 0–60 MPH Time by Car Make)  
- Bubble plot: Price vs. Horsepower (color = Torque, size = Engine Size)  
- Correlation heatmap for numeric variables  

![MLRepoFR](/images/EngineSizeGraph.png)  
![MLRepoFR](/images/EngineSizevs.Horsepower.png)  
![MLRepoFR](/images/Horsepowervs.Price.png)  
![MLRepoFR](/images/EngineSizeByYear.png)  
![MLRepoFR](/images/CorrelationMatrix.png)  
![MLRepoFR](/images/CarTypesAcceleration.png)

## Key Takeaways

- **Higher horsepower** often translates into **higher price** and **larger engines**.
- **Acceleration times** are best among **hypercar brands** like Rimac and Koenigsegg.
- The **price spread** is enormous ($25,000 to $5.2M), indicating a mix of luxury, mainstream, and exotic sports cars.
- **Multicollinearity** is evident, especially between **horsepower and torque** (correlation ≈ 0.94).

## Data

- File: `Sport Car price.csv`  
- **1,007 observations**  
- **8 variables**, including:  
  - `Car.Make`, `Model`, `Year`  
  - `Engine.Size..L.`, `Horsepower`, `Torque..lb.ft.`  
  - `X0.60.MPH.Time..seconds.`, `Price..in.USD.`  

## Libraries Used

- `tidyverse`
- `caret`
- `recipes`
- `rsample`
- `parsnip`
- `workflows`
- `tune`
- `yardstick`
- `randomForest`
- `e1071`
- `xgboost`
- `corrplot`
- `ggplot2`
- `car`

## Next Steps

The next phase involves:

- **Data splitting** (training vs. testing)  
- **Modeling** using various algorithms:  
  - Linear Regression  
  - Random Forest  
  - SVM  
  - XGBoost  
- **Hyperparameter tuning** with `tune` and `caret`  
- **Evaluation** using RMSE, R², and MAE  
