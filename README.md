# TensorBoard App for Visualizing Machine Learning Training Metrics

TensorBoard is a TensorFlow tool used for **experiment visualization and metrics tracking**.  
When building machine learning models such as neural networks, it is important to monitor whether the model is learning and evaluate its performance during training.

TensorBoard provides a convenient environment for this by launching a **local web application** that visualizes metrics, graphs, and training progress in real time.

---

# Neural Network Model

## 1. Importing Dependencies
All required libraries are listed in `requirements.txt`.

## 2. Dataset
The dataset used in this project contains **Ferrari stock market data** from Kaggle:

https://www.kaggle.com/datasets/alehcleal/ferrari-stock-data-2015-2026

## 3. Exploratory Data Analysis (EDA)
- Dropped missing values (none were present, but this ensures clean data)
- Removed the **Date** column
- Kept only numerical features for the model

## 4. Train/Test Split
The dataset is split into:

- **Training set:** 85%
- **Testing set:** 15%

## 5. Feature Scaling
All features and targets are normalized using **Min-Max Scaling** to ensure inputs and outputs are on the same scale.

This improves neural network training stability.

---

# Model Architecture

The neural network architecture consists of:

- **Input layer:** 4 features
- **Hidden layer 1:** 32 neurons (ReLU activation)
- **Hidden layer 2:** 16 neurons (ReLU activation)
- **Output layer:** 1 neuron for regression prediction (Volume of shares traded)

---

# Training Configuration

- **Loss function:** Mean Squared Error (MSE): MSE = average((y_true - y_pred)^2)

- **Optimizer:** Adam (learning rate = 0.001)

The learning rate controls how much model weights are updated during training.

- **Metric:** Mean Absolute Error (MAE): MAE = average(|y_true - y_pred|)

- **Epochs:** 50  
- **Batch size:** 32

---

# Model Evaluation

After training, the model is evaluated using the **test dataset** with the same scaled inputs and targets.

---

# TensorBoard Visualization

TensorBoard runs locally and displays:

- Training and validation loss
- Metrics across epochs
- Experiment comparisons

TensorBoard is launched on:Port 6006 (in our case)


---

# Results from one of my runs

Example results from training:

- Training loss decreased from **0.0014 → 0.000765** Training loss starts at 0.0014 and gradually decreases to 0.000765 → model is learning.
- Validation loss ended around **0.000383**
- MAE decreased from **0.02 → 0.01** --> starts at 0.02 and ends at 0.01 → on the scaled data, the model’s predictions are on average 1% off from the true scaled value.

These results indicate that the model successfully learned the relationship between stock prices and trading volume.

---

# Features Used

### Predictors

- **Close:** Stock price at market closing
- **High:** Highest price during the trading day
- **Low:** Lowest price during the trading day
- **Open:** Stock price at market opening

### Target

- **Volume:** Total number of Ferrari shares traded during the day
