# combinational-depth
This project focuses on predicting the combinational logic depth of signals in RTL designs using Machine Learning (ML). Traditional synthesis tools take significant time to determine logic depth, making them inefficient for large-scale designs.

[updated_combinational_logic_depth_dataset.xlsx](https://github.com/user-attachments/files/18976968/updated_combinational_logic_depth_dataset.xlsx)
This is the dataset I used to train my model.

Project Overview
I developed a machine learning model to predict combinational logic depth of signals in RTL designs. Traditional synthesis tools take minutes to hours for this task, while my ML model predicts in milliseconds, providing a faster alternative for digital designers and verification engineers.

Dataset Used
The dataset contains signal parameters affecting logic depth. I processed the dataset and used feature engineering to improve model performance.

Main features in the dataset:

Fan-In: Number of input connections

Fan-Out: Number of output connections

Gate Count: Total number of logic gates

Gate Delay (ns): Delay caused by logic gates

Line Delay (ns): Delay due to wiring/interconnects

Transition Delay (ns): Delay due to signal transitions

Logic Depth (Target Variable): The value we predict

Model Training Approach

I trained a Stacking Ensemble Model, combining multiple algorithms for better accuracy. The models used:

✔ XGBoost – Captures complex patterns

✔ Random Forest – Reduces overfitting

✔ Gradient Boosting – Improves performance

✔ Final Estimator: Linear Regression for blending outputs


Steps I followed:

Preprocessed the dataset (handled missing values, normalized features).

Trained multiple models and compared their accuracy.

Used stacking ensemble to combine the best models.

Performed hyperparameter tuning to improve performance.

Validated using 5-fold cross-validation for robustness.

Performance Results
✔ Mean Absolute Error (MAE): 4.12 ns
✔ R² Score: 0.986 (98.6% variance explained)
✔ Prediction Time: Milliseconds (vs. minutes/hours for synthesis tools)

I tested the model against synthesis-generated depth values and cross-validated results using 5-fold CV, confirming high accuracy and consistency.
