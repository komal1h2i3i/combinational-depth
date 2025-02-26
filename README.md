# Predicting Combinational Logic Depth using Machine Learning  
This project focuses on predicting the combinational logic depth of signals in RTL designs using Machine Learning (ML). Traditional synthesis tools take significant time to determine logic depth, making them inefficient for large-scale designs.

[updated_combinational_logic_depth_dataset.xlsx](https://github.com/user-attachments/files/18976968/updated_combinational_logic_depth_dataset.xlsx)
This is the dataset I used to train my model.


## Introduction  
This project presents a machine learning-based approach to predicting the combinational logic depth of signals in RTL designs. Traditional synthesis tools take significant computation time to analyze circuit depth, while our model provides real-time estimations with high accuracy. By leveraging an ensemble of ML models, we achieve improved prediction reliability.  

## Objective  
The goal of this project is to:  
- Develop a machine learning model to predict logic depth based on various circuit parameters.  
- Minimize the computational overhead compared to traditional synthesis tools.  
- Enhance RTL design efficiency by providing rapid logic depth estimations.  

## Dataset Overview  
The dataset consists of **1500 RTL signals**, each characterized by multiple circuit parameters affecting logic depth.  

| **Feature**              | **Description**                                      |  
|--------------------------|------------------------------------------------------|  
| **Fan-In**               | Number of input connections to a signal             |  
| **Fan-Out**              | Number of output connections from a signal          |  
| **Gate Count**           | Total number of logic gates associated with the signal |  
| **Gate Delay (ns)**      | Delay introduced by logic gates                     |  
| **Line Delay (ns)**      | Delay caused by wire interconnects                  |  
| **Transition Delay (ns)**| Delay due to signal transitions                     |  
| **Logic Depth (Target)** | The depth of the signal in terms of gate levels     |  
| **Delay per Gate (ns)**  | Average delay per logic gate                        |  
| **Fan Complexity**       | Derived feature: **Fan-In × Fan-Out**               |  

---

## Methodology  

### 1. Data Preprocessing  
- **Dataset Cleaning:** Removed any identifier columns (e.g., "Signal") that are irrelevant to training.  
- **Feature Engineering:** Introduced a derived feature, **Fan Complexity** (Fan-In × Fan-Out), to capture interconnect complexity.  
- **Scaling & Transformation:**  
  - Handled missing values using **median imputation**.  
  - Applied **Polynomial Feature Expansion** (degree=2) to capture non-linear relationships.  
  - Standardized features using **StandardScaler**.  

### 2. Model Training  

#### **Train-Test Split:**  
- **80%** training data  
- **20%** testing data  

#### **Machine Learning Models Used:**  
- **XGBoost Regressor** – Captures complex non-linear dependencies.  
- **Random Forest Regressor** – Reduces overfitting and improves generalization.  
- **Gradient Boosting Regressor** – Enhances predictive accuracy.  
- **Stacking Ensemble** – Combines the above models using **Linear Regression** as the meta-model.  

#### **Cross-Validation:**  
- Implemented **5-fold cross-validation** to ensure model robustness.  

### 3. Model Evaluation  

The trained ensemble model was evaluated using **Mean Absolute Error (MAE)** and **R² Score**.  

| **Metric**                  | **Value** |  
|-----------------------------|----------|  
| **Mean Absolute Error (MAE)** | 4.12 ns   |  
| **R² Score**                 | 0.986 (98.6% accuracy) |  

---

## Performance & Correctness Verification  
- **Cross-validation** (**5-fold CV**) ensures generalization and model stability.  
- **Residual analysis** confirms the model’s low bias and variance.  
- **Predictions were benchmarked against synthesis-based ground truth values.**  

---

## Complexity Analysis  
| **Complexity Type**     | **Analysis** |  
|-------------------------|-------------|  
| **Training Time Complexity** | **O(n log n)** per tree-based model |  
| **Inference Time Complexity** | **O(1)** (real-time predictions) |  
| **Space Complexity** | Proportional to dataset size and feature expansion |  

---

## Comparison with Other Approaches  
| **Method**                    | **Limitation** |  
|--------------------------------|---------------|  
| **Single Model (XGBoost, RF, GBR Alone)** | Lower accuracy compared to ensemble |  
| **Neural Networks**           | Requires large dataset, lacks interpretability |  
| **LSTM-Based Models**         | High complexity, unnecessary for static circuits |  
| **Traditional Synthesis Tools** | Very slow, computationally expensive |  

---



