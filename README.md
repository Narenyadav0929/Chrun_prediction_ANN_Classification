# Bank Customer Churn Prediction Using Artificial Neural Network (ANN)

## 📌 Project Overview

Customer churn is one of the major challenges faced by banks. Retaining existing customers is essential for maintaining long-term customer relationships and business growth.

This project uses an **Artificial Neural Network (ANN)** to predict whether a bank customer is likely to leave the bank based on customer demographics and account-related information.

The project covers the complete machine learning workflow, including exploratory data analysis, data preprocessing, handling class imbalance, ANN model development, hyperparameter tuning, model evaluation, and an interactive Streamlit application.

## 🎯 Business Problem

The objective is to identify customers who are likely to leave the bank so that appropriate customer retention strategies can be implemented.

Predicting customer churn can help banks:

- Identify customers who are at risk of leaving.
- Develop targeted customer retention strategies.
- Improve customer engagement.
- Make data-driven business decisions.

## 📂 Dataset

The project uses the Bank Customer Churn dataset containing **10,000 customer records and 14 original columns**.

**Target variable: `Exited`**

| Value | Meaning |
|---|---|
| 0 | Customer stays with the bank |
| 1 | Customer exits the bank |

### Features Used

- CreditScore
- Geography
- Gender
- Age
- Tenure
- Balance
- NumOfProducts
- HasCrCard
- IsActiveMember
- EstimatedSalary

The following columns were removed during preprocessing:

- RowNumber
- CustomerId
- Surname

## 🛠️ Technologies & Libraries

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-learn
- TensorFlow / Keras
- SciKeras
- Streamlit
- TensorBoard
- Jupyter Notebook

## ⚙️ Project Workflow

### 1. Exploratory Data Analysis (EDA)

- Analyzed the structure and distribution of the dataset.
- Explored numerical and categorical features.
- Examined customer churn patterns.
- Identified class imbalance in the target variable.

### 2. Data Preprocessing

- Removed unnecessary columns.
- Applied Label Encoding to Gender.
- Applied One-Hot Encoding to Geography.
- Scaled numerical features using StandardScaler.
- Split the dataset into training and testing sets.

### 3. Handling Class Imbalance

During exploratory data analysis, class imbalance was identified.

The target distribution was approximately:

- 79.63% customers stayed with the bank.
- 20.37% customers exited the bank.

To address this imbalance, **class weights** were calculated using Scikit-learn's `compute_class_weight()`.

Class weights assign greater importance to the minority class during model training.

**Observation:** After applying class weights:

- Recall increased, helping the model identify more actual churn customers.
- Precision decreased, indicating an increase in false-positive predictions.

This demonstrates the trade-off between precision and recall when handling imbalanced classification problems.

### 4. Artificial Neural Network (ANN)

A Sequential Artificial Neural Network was developed using TensorFlow/Keras.

**Initial model architecture:**

| Layer | Configuration |
|---|---|
| Input Layer | 12 input features |
| Hidden Layer 1 | 64 neurons, ReLU |
| Hidden Layer 2 | 31 neurons, ReLU |
| Output Layer | 1 neuron, Sigmoid |

**Model configuration:**

- Optimizer: Adam
- Loss Function: Binary Crossentropy
- Output Activation: Sigmoid
- Evaluation Metrics: Accuracy, Precision, Recall and AUC.

### 5. Model Training

The ANN was trained using:

- Training data.
- Validation data.
- Class weights to address class imbalance.
- Early Stopping to reduce unnecessary training.
- TensorBoard to monitor training performance.

Early Stopping was configured to monitor validation loss and restore the best tracked weights.

### 6. Hyperparameter Tuning

Hyperparameter tuning was performed using **GridSearchCV with the SciKeras KerasClassifier wrapper**.

The following hyperparameters were explored:

| Hyperparameter | Values |
|---|---|
| Neurons | 16, 32, 64, 128 |
| Hidden Layers | 1, 2 |
| Epochs | 50, 100 |

Three-fold cross-validation was used to evaluate different hyperparameter configurations.

The F1-score was selected as the GridSearchCV scoring metric to balance precision and recall.

Class weights were included during hyperparameter tuning to address class imbalance.

Early Stopping was also incorporated to help control training duration.

### 7. Model Monitoring with TensorBoard

TensorBoard was used to monitor the training and validation performance.

The following metrics were analyzed:

- Training and validation accuracy.
- Training and validation loss.
- Precision.
- Recall.
- AUC.
- Learning rate.

The training and validation curves helped identify potential overfitting and understand model learning behaviour.

## 🚀 Streamlit Application

An interactive Streamlit application was developed to predict customer churn.

Users can enter customer information, including:

- Geography
- Gender
- Age
- Credit Score
- Balance
- Estimated Salary
- Tenure
- Number of Products
- Credit Card Status
- Active Membership Status

### Prediction Workflow

1. Accept customer information through the Streamlit interface.
2. Apply the saved encoders.
3. Scale the input features using the saved StandardScaler.
4. Pass the processed data to the trained ANN model.
5. Generate churn probability.
6. Display whether the customer is likely to churn.

## 📁 Repository Structure

```text
Churn_prediction_ANN_Classification/
│
├── Churn_Modelling.csv
├── experiment.ipynb
├── prediction.ipynb
├── app.py
├── model.keras
├── one_hot_encoder.pkl
├── lable_encoder.pkl
├── scaler.pkl
├── requirements.txt
└── README.md
```

## 💻 Installation & Usage

### 1. Clone the repository

```bash
git clone https://github.com/Narenyadav0929/Churn_prediction_ANN_Classification.git
```

### 2. Navigate to the project directory

```bash
cd Churn_prediction_ANN_Classification
```

### 3. Create a virtual environment

```bash
python -m venv venv
```

### 4. Activate the virtual environment

For Windows:

```bash
venv\Scripts\activate
```

### 5. Install dependencies

```bash
pip install -r requirements.txt
```

### 6. Run the Streamlit application

```bash
streamlit run app.py
```

Open the application in your browser:

```text
http://localhost:8501
```

## 📊 Model Evaluation

The model evaluation considers:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Confusion Matrix

Special attention is given to precision and recall because the dataset contains an imbalanced target variable.

The objective is to identify potential churn customers while understanding the trade-off between false positives and false negatives.

## 🔮 Future Improvements

- Further optimize ANN architecture and hyperparameters.
- Experiment with different classification thresholds.
- Compare ANN with Logistic Regression and Random Forest.
- Improve model interpretability using SHAP.
- Deploy the application to a cloud platform.
- Develop customer retention strategies based on model predictions.

## 👨‍💻 Author

**Narender Singh Yadav**

- GitHub: [Narenyadav0929](https://github.com/Narenyadav0929)
- LinkedIn: [Narender Singh Yadav](https://www.linkedin.com/in/narender-singh-yadav-36a42334b)
- Portfolio: [The Data Alchemist](https://www.vitaely.me/the_data_alchemist)

---

⭐ If you find this project useful, feel free to explore the repository and share your feedback.

**Disclaimer:** This project is developed for educational and analytical purposes. Predictions should be evaluated before being used for actual banking decisions.
