# House Price Prediction

## Overview

This repository contains the code and accompanying report for the House Price Prediction project, developed as the final coursework of our Introduction to Data Science course. The goal of this project is to predict house prices by leveraging advanced data collection, preprocessing, and machine learning techniques.

## Project Description

The project consists of several key stages:

- **Data Collection:**  
  Raw data was collected using two methods:  
  - **RegEx Extraction:** Initially used to scrape data from raw files.  
  - **LLM Extraction:** Employed to supplement the extraction process, especially for challenging features such as `bedroom`, `wc`, and `frontage`. This combination improved the feature correlation with the target variable.

- **Data Preprocessing:**  
  The dataset required significant cleaning:
  - **Handling Outliers:**  
    - For the target variable `price`, outliers were defined outside the range of 0.1B to 1000B.  
    - Two methods were evaluated: capping (using the 5th and 95th percentiles) and the IQR method—with IQR ultimately proving more effective.
  - **Handling Missing Values:**  
    - For `price`, the options were to impute missing values using semi-supervised learning or to drop them. Given the low frequency of missing target values, the latter was chosen.
    - For other features, two imputation methods were compared. Although mean imputation (Method 1) yielded better performance metrics, a complementary imputation strategy (Method 2) was ultimately selected to prevent overfitting and maintain data variability.
- **Feature Engineering**  
  To enhance model performance, we introduced several new features:  

    - Used KMeans clustering to group locations and capture spatial patterns.  
    - Added population density to provide insights into demand.  
    - Created the `area_used` feature by combining area and floor data, which turned out to be the most influential factor in predictions.  
 
- **Modeling:**  
  A variety of regression models were tested, including:
  - Linear Regression, Ridge, and Lasso
  - Decision Tree, Random Forest, XGBoost, and CatBoost  
  A Neural Network model using PyTorch was also built; however, it was excluded from the final analysis because its performance was not significantly better than that of traditional machine learning models.

- **Evaluation:**  
  Model performance was assessed using metrics such as Mean Squared Error (MSE), Mean Absolute Error (MAE), and R². The comparison between the two imputation methods is summarized in the table below:

<div align="center">

| Model         | MSE      | MAE      | R²      |
|--------------|----------|----------|----------|
| Random Forest | 47.0437  | 4.0738   | 0.2418   |
| CatBoost     | 47.1363  | 4.0725   | 0.2403   |
| XGBoost      | 47.4832  | 4.0879   | 0.2347   |
| Linear       | 49.1161  | 4.2253   | 0.2084   |
| Ridge        | 49.1163  | 4.2253   | 0.2084   |
| Lasso        | 49.1561  | 4.2266   | 0.2078   |

</div>

![image](https://github.com/user-attachments/assets/014255b6-a9d3-4759-8d14-3e36d96abaf8)


## Key Insights

- **Data Distribution:** A thorough understanding of the data distribution is essential during preprocessing.
- **Feature Engineering:** Combining related discrete features can lead to the creation of more powerful predictors.
- **Preprocessing Strategies:** There is no universal solution; each dataset may require a unique approach for handling outliers and missing values.
- **Model Evaluation:** A model that performs well on training data may not generalize to unseen data; hence, thorough experimental evaluation is critical.
- **Outlier Treatment:** Removing outliers should be done carefully, as some outliers might contain vital information regarding trends in the data.

![image](https://github.com/user-attachments/assets/64fb3516-d5c1-4a4c-8d29-f424190511e0)

## Repository Structure
```
House-Price-Prediction/
├── Data/ # Raw and processed data files 
│   ├── final_data.csv # # The final dataset ready for model training
│   ├── population_density.csv # Population density data of Vietnamese provinces (used for feature engineering)
│   ├── raw_data.csv # Scraped raw text data (unprocessed)
│   ├── transformed_data.csv # Extracted useful features using LLMs and RegEx
├── scr.ipynb # Main Jupyter Notebook with full project workflow
├── ExperimentalReport_Group12_22KDL1.pdf # Project report (PDF) 
├── ProjectRequirement.pdf # Project guidelines and requirements
├── README.md # Project overview and documentation
```

## Conclusion

This project explored various approaches to predicting house prices, from data collection and preprocessing to model training and evaluation. Through experimentation, we analyzed different techniques and identified the most effective methods for handling missing values, outliers, and feature engineering.  

While the models achieved promising results, there is always room for improvement. Future work could focus on expanding the dataset, optimizing hyperparameters, and exploring deep learning approaches for better performance.  

This project provided valuable insights into data-driven decision-making and reinforced the importance of thorough data preprocessing and feature engineering in predictive analytics.  
