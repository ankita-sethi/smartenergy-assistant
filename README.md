# Smart Energy Assistant

Final Project for  
AMS559 / CSE551: Smart Energy in the Information Age

GitHub Repository: https://github.com/ankita-sethi/smartenergy-assistant

---

## Overview

The Smart Energy Assistant is an intelligent system designed to help users monitor, predict, and manage energy consumption in a smart home environment. The project combines time series forecasting, anomaly detection, and Large Language Models (LLMs) to provide energy insights, appliance control, and explainable recommendations.

The assistant enables users to interact using natural language, understand energy usage patterns, detect anomalies, and make informed decisions to reduce energy costs and promote sustainability.

---

## Objective

The objective of this project is to develop a smart energy assistant that:

- Monitors appliance level energy consumption
- Predicts future energy usage using weather data
- Detects anomalies in energy patterns
- Allows appliance control through natural language
- Explains predictions and anomalies in a human readable way using LLMs

---

## Background

Residential energy consumption contributes significantly to overall electricity usage in the United States. With the increasing adoption of smart home technologies, there is a growing need for intelligent energy management solutions.

This project focuses on empowering users to better understand and manage their household energy usage, reducing costs while supporting a more sustainable lifestyle.

---

## Dataset

The project uses the **Smart Home Dataset with Weather Information** from Kaggle.

- File used: `HomeC.csv`
- Data includes:
  - One minute interval energy consumption data
  - Appliance level energy usage in kW
  - Weather attributes such as temperature, humidity, and cloud cover
  - Data collected over 350 days

This dataset provides a comprehensive view of energy usage within a smart home environment.

---

## Data Preprocessing

Several preprocessing steps were applied to ensure data quality and readiness for modeling:

- Removed highly correlated columns (`use` and `gen`) to reduce redundancy
- Standardized column names by removing unit suffixes
- Aggregated appliance data into meaningful categories such as:
  - Furnace
  - Kitchen appliances
- Handled invalid weather values using backfill
- Extracted temporal features including:
  - Month
  - Day
  - Weekday
  - Hour
  - Minute

The primary appliances analyzed were the refrigerator, furnace, and dishwasher.

---

## Prediction Models

Multiple forecasting approaches were explored during the analysis phase. After evaluation, **ARIMA (AutoRegressive Integrated Moving Average)** was selected as the final model due to its superior performance and lower error.

### ARIMA Forecasting

- Train test split: 70% training, 30% testing
- Model order: (2,1,1)
- Validation method: Walk forward validation
- Evaluation metrics:
  - Mean Squared Error (MSE)
  - Root Mean Squared Error (RMSE)
  - Mean Absolute Error (MAE)
  - R squared score
  - Akaike Information Criterion (AIC)

The ARIMA model demonstrated strong predictive performance across all selected appliances.

---

## Large Language Model Integration

### LLM Capabilities

The LLM enables:

- Natural language interaction with users
- Appliance control using functions such as:
  - turn_on()
  - turn_off()
  - status()
  - predict()
- Explanation of predictions and anomalies
- Structured responses for reliable execution

### Few Shot Learning

Both fine tuning and few shot learning approaches were explored. Based on empirical results, **few shot prompting** was selected due to better efficiency and performance.

Synthetic datasets were created to help the LLM generate structured outputs required for appliance control and predictions.

---

## Anomaly Detection

Anomaly detection identifies unusual energy consumption patterns by comparing predicted and actual values.

Approaches used:

- Statistical error based analysis with higher weight on energy usage
- Feature extraction including mean, median, and standard deviation
- Threshold based anomaly flagging
- LLM based explainability to replace traditional statistical methods

The LLM based approach provided comparable results with improved interpretability.

---

## Explainability

Explainability is a core component of this project.

The system provides:

- Chain of thought based explanations
- Context aware reasoning using historical and real time data
- Clear insights into why anomalies or predictions occur
- Visualizations to support understanding

Due to hardware limitations, GPT 4 with few shot prompting was used instead of deploying Llama 3.

---

## User Interface

A chatbot based user interface allows users to:

- Control appliances
- View current and predicted energy consumption
- Detect anomalies
- Interact with the assistant in real time

Appliance behavior was simulated due to the lack of physical devices.

---

## Future Scope

- Integration with real smart home devices
- Support for open source LLMs such as StabilityLM and Home LLM
- Integration with HomeAssistant
- Expansion to additional appliances
- Improved security and privacy mechanisms
- Long term energy usage trend analysis

---

## Conclusion

This project demonstrates how time series forecasting, anomaly detection, and Large Language Models can be combined to build an intelligent smart energy assistant. The system helps users understand, predict, and manage energy usage while promoting sustainability and informed decision making.

---

## References

- Smart Home Dataset with Weather Information, Kaggle
- OpenAI Cookbook
- SAGE: Smart Home Agent with Grounded Execution
- Residential Buildings Factsheet, University of Michigan
- ARIMA and IoT Energy Analysis resources
