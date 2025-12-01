---
layout: page
title: Conclusion
permalink: /conclusion/
---

#### **Non-Technical Summary**
<div style="text-align: justify;">
Our analysis shows that predicting air quality is far more complex than applying a single simple model. Air Quality Index (AQI) values are influenced by many interacting factors such as geography, seasonal variation, monitoring inconsistencies, and unexpected events like wildfires. Different counties and states behave in fundamentally different ways—some show smooth improvements over time, while others experience erratic spikes that break any predictable pattern. Because of these differences, it is not feasible to build one generalized AI model that accurately predicts air quality for every region. Instead, our results strongly suggest that air-quality forecasting must rely on specialized, hyper-local models that adapt to local dynamics and pollutant behavior.
</div>

#### **Key Insights and Discoveries**
<div style="text-align: justify;">
Our findings show that air quality is not governed by a simple linear relationship but by highly non-linear and locally influenced patterns. This is demonstrated by the strong performance of the RandomForestRegressor compared to the OLS regression model, which struggled to explain variation across counties. Geographic identifiers such as StateFIPS and CountyFIPS emerged as critical predictors, showing that location-specific environmental, industrial, and regulatory factors significantly influence pollutant levels. The LSTM model revealed that temporal behavior varies greatly: it performed well in counties where pollutant levels changed smoothly over time but struggled in counties with abrupt fluctuations or inconsistent data. These observations reinforce that air-quality trends cannot be understood from a single perspective. Instead, they require multiple modeling approaches—linear, non-linear, temporal, and clustering—to capture different aspects of the underlying complexity. This diversity of required methods is strong evidence that a single generalized AI model is unsuitable for AQI prediction.
</div>

#### **Real-World Impact**
<div style="text-align: justify;">
A key application of our work is incident-based deviation analysis. By training models exclusively on historical data, we can construct a statistical baseline for expected AQI behavior. This baseline serves as a counterfactual model—it predicts what the AQI should have been if no disruptive incident had occurred. When an event such as a wildfire causes sharp increases in AQI levels, the difference between the observed AQI and the baseline prediction quantifies the true magnitude of the incident’s impact. Because the LSTM captures sequential dependencies over years, it provides a multi-layered understanding of both spatial and temporal deviation.
</div>

<div style="text-align: justify;">
Beyond impact quantification, our LSTM model can be repurposed for post-incident recovery forecasting. After a pollution spike, the model can be fine-tuned or re-fed with the elevated AQI values as the most recent time steps. This allows the LSTM to generate forward predictions estimating how pollutant concentrations will decline over the following weeks or months. Since LSTMs are sensitive to long-term dependency patterns, the predicted recovery curve provides insight into how long a county may take to return to its pre-incident AQI equilibrium—informing risk communication, resource allocation, and environmental restoration planning.
</div>

<div style="text-align: justify;">
Another high-impact use case is evaluating environmental interventions and regulatory changes. By comparing observed AQI after an intervention (e.g., emission controls or traffic restrictions) with the counterfactual AQI predicted by the baseline model, we can compute a quantitative estimate of the intervention’s real-world effectiveness. This approach mirrors econometric techniques such as difference-in-differences but leverages machine learning to model complex, non-linear counterfactual scenarios. Overall, our results show that specialized, localized models are not only more accurate but also more versatile for environmental analytics—enabling real-time deviation monitoring, incident assessment, recovery forecasting, and policy evaluation. These capabilities would be lost in a single generalized AI model attempting to represent the entire U.S. air-quality system.
</div>

#### **Limitations, Improvements, and Future Directions**
<div style="text-align: justify;">
The main limitation of this work is the dataset. Air quality depends heavily on external factors such as weather patterns, wildfire frequency, regulatory enforcement, industrial emissions, and traffic behavior—elements not included in our dataset but essential for comprehensive prediction. Another major inconsistency is the variation in measurement units used across counties, making county-level pollutant comparisons difficult. These limitations emphasize the importance of expanding data sources in future work. Integrating meteorological data, satellite wildfire records, and industrial activity reports would allow models to better capture the true drivers of AQI fluctuations.
</div>

<div style="text-align: justify;">
Future improvements should include developing pollutant-specific or county-specific models, constructing a modular forecasting system rather than a single general model, and incorporating spatial-temporal methods capable of capturing pollutant movement between neighboring counties. The long-term goal is to move from isolated models to an adaptive, context-aware air-quality prediction framework that reflects the complexity revealed in our analysis.
</div>

#### **Results**
<div style="text-align: justify;">
The OLS regression model, used as a baseline, achieved an RMSE of 0.0571 and an R² of only 0.2074, indicating that linear relationships alone explain very little of the variation in AQI. This weak performance confirms that pollutant behavior is strongly non-linear and heavily dependent on interactions that simple linear models cannot capture. In contrast, the RandomForestRegressor achieved an RMSE of 0.0320 and an R² of 0.7511 after tuning, more than tripling the explanatory power of OLS. Geographic identifiers such as CountyFIPS and StateFIPS ranked highest in feature-importance analysis, aligning with environmental intuition: local emissions, regulatory differences, and geographical topology create unique pollutant signatures that tree-based models can effectively capture.
</div>

<div style="text-align: justify;">
The LSTM model, trained on sequential pollutant data for individual counties, performed well in regions with stable year-to-year pollutant behavior. Its rapid reduction in validation loss (reaching approximately 0.0016) shows that it successfully learned temporal dependencies when sequences were complete and smooth. However, the model struggled in counties with irregular or volatile patterns due to missing years or abrupt pollutant spikes. This performance gap highlights both the advantages and limitations of deep temporal models: they excel when the underlying signal is consistent but degrade when sequences are fragmented or dominated by unpredictable events. Together, these results demonstrate that no single model can capture all aspects of AQI behavior. Instead, each model type illuminates different dimensions—linear trends, non-linear spatial structure, and temporal evolution—providing a more holistic understanding of how air quality changes across regions and time.
</div>
