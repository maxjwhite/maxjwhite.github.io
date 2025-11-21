---
layout: page
title: Models Implemented
permalink: /model/
---
#### **Regression**
<div style="text-align: justify;">
Linear regression is a simple, interpretable model that quantifies how different air-quality measures relate to a continuous outcome, such as annual PM2.5 concentration. It serves as a strong baseline because it is fast, easy to evaluate, and helps reveal key predictor relationships before experimenting with more complex models.
</div>

<div style="text-align: justify;">
Linear regression assumes linear relationships between predictors and the target, minimal multicollinearity, homoscedastic residuals, and normally distributed errors. Because the model contains no traditional hyperparameters, tuning focused on data preprocessing choices—such as feature scaling, interaction terms, and regularization variants like Ridge or Lasso to handle noise and reduce overfitting.
</div>

<div style="text-align: justify;">
High variance, nonlinear behavior, and heterogeneity in the dataset made it easy for a simple linear model to either underfit or produce unstable coefficients. This was addressed through feature engineering, regularization, and diagnostic checks to improve generalization and interpretability.
</div>

#### **LSTM**
<div style="text-align: justify;">
We chose an LSTM because it is well-suited for learning long-term temporal patterns in air-quality trends across years. Its ability to model sequential dependencies makes it useful for forecasting pollutant levels and answering time-based research questions.
</div>

<div style="text-align: justify;">
For the LSTM model, we assumed that pollutant levels follow a sequential pattern over time and that an LSTM can effectively capture these long-term temporal dependencies. We tuned the number of LSTM units, the sequence window size, and the learning rate, and incorporated dropout and early stopping to stabilize training.
</div>

<div style="text-align: justify;">
The main challenges involved handling missing years, irregular intervals, and sudden spikes in pollutant values. These issues were addressed using normalization, sliding-window sequence generation, and regularization methods to help reduce overfitting.
</div>

#### **KMeans**
<div style="text-align: justify;">
KMeans was selected because the dataset contains continuous pollutant concentration variables (e.g., PM2.5 and ozone-related measurements), and because there were no default target labels within the dataset. This made clustering a useful tool for discovering hidden groupings or structures across regions and time periods.
</div>

<div style="text-align: justify;">
KMeans assumes that clusters are roughly spherical, equally sized, and separable using Euclidean distance. It also assumes that features are on comparable scales, which makes preprocessing techniques like standardization essential. The primary hyperparameter tuned was the number of clusters (k). Using the elbow method, inertia was evaluated across multiple values of k to identify where additional clusters produced diminishing returns.
</div>

<div style="text-align: justify;">
The main challenge we faced was preprocessing the dataset before clustering. Creating a pivot table that captured all necessary features required several iterations. Once the data was structured properly, training and analyzing the KMeans model became straightforward.
</div>


#### **RandomForest**
<div style="text-align: justify;">
Random Forest was chosen because the classification task involves predicting categorical air-quality outcomes based on numeric features which fit perfectly with the task we were trying to accomplish in identifying high/low risk groupings within our dataset. Random Forests also handle high-dimensional data well, are robust to noise, and naturally provide feature-importance insights. These feature importance measures also helped us identify which measures to focus on in further work.
</div>

<div style="text-align: justify;">
Random Forest does not make strong assumptions about data distribution. It does not require linear relationships or normally distributed features, which makes preprocessing fairly easy.
</div>

<div style="text-align: justify;">
The tuning process focused on <code>n_estimators</code> (number of trees), <code>max_depth</code> (to control overfitting), and <code>min_samples_split</code> and <code>min_samples_leaf</code> (to regulate tree growth).
</div>

<div style="text-align: justify;">
This model was fairly easy to train, and although we did a fair amount of preprocessing for the KMeans clustering, the Random Forest would have handled the extra noise well. Testing different hyperparameter combinations allowed us to converge on a final solution.
</div>

### **Evaluation**
<div style="display: flex; justify-content: center; gap: 40px;">

  <div style="text-align: center; width: 500px;">
    <p><strong>Regression</strong></p>
    <img src="/image/eval_reg.png" alt="Before" width="500">
  </div>

  <div style="text-align: center; width: 500px;">
    <p><strong>LSTM</strong></p>
    <div style="display: flex; justify-content: center; gap: 10px;">
      <img src="/image/eval_lstm.png" alt="After 1" width="500">
    </div>
  </div>

</div>
<div style="display: flex; justify-content: center; gap: 40px;">

  <div style="text-align: center; width: 500px;">
    <p><strong>KMeans</strong></p>
    <img src="/image/eval_kmeans.png" alt="Before" width="500">
  </div>

  <div style="text-align: center; width: 500px;">
    <p><strong>RandomForest</strong></p>
    <div style="display: flex; justify-content: center; gap: 10px;">
      <img src="/image/eval_rf.png" alt="After 1" width="500">
    </div>
  </div>

</div>

<div style="text-align: justify;">
In the case of our approach, none of our models were necessarily trying to tackle the same problem, so it's hard to determine which model did best since they all did better/worse at different tasks. In terms of ease of implementation, the Random Forest was easiest to train, but in terms of insights derived, the LSTM model provided the most insightful forecast information in terms of our research questions.
</div>


### **Data Transformation**

<div style="display: flex; justify-content: center; gap: 40px;">

  <div style="text-align: center; width: 500px;">
    <p><strong>Before</strong></p>
    <img src="/image/before_pivot.png" alt="Before" width="500">
  </div>

  <div style="text-align: center; width: 500px;">
    <p><strong>After</strong></p>
    <div style="display: flex; justify-content: center; gap: 10px;">
      <img src="/image/after_pivot.png" alt="After 1" width="500">
    </div>
  </div>

</div>
