<span style="color:RED; font-weight: Bold; font-size: 45px;"> Machine Learning Project</span>
___

## 📊 Datasets Used in This Project

We have worked on three datasets:

- 🏪 **`coffee_shop_revenue`**: Used for evaluating the **Linear Regression** and **Polynomial Regression** models.
- 🏥 **`healthcare_stroke_data`**: Used for evaluating the **Logistic Regression** & **K-Nearest Neighbors (KNN)** models.
- 🌸 **`iris`**: Used for evaluating the **Support Vector Machine (SVM)** & **Neural Network** models

___


## 📈 **Linear Regression Evaluating Phases**
___
---

### 🧹 **1. Data Preprocessing**
We begin by preparing the dataset for modeling:

- 📥 Load the dataset using **Pandas**.
- 🔍 Display basic structure using `.head()`, `.describe()`, and `.info()`.
- 🕳️ Check for **missing values** using `.isnull().sum()`.
- 🧠 Verify correct **data types**.
- 🚫 Ensure no **categorical features** need encoding.

---

### 🔍 **2. Exploratory Data Analysis (EDA)**
Understanding the data visually:

- 📊 Use **pairplots** to explore relationships between features.
- 📉 Plot **scatter graphs** between features and the target variable (`Daily_Revenue`).
- 🧲 Identify features with strong **correlation** to the target.

---

### ➕ **3. Simple Linear Regression**
We build two simple models using individual features.

#### 📌 Model 1: `Number_of_Customers_Per_Day` 👥
- ✂️ Split data (80% training / 20% testing).
- 🧠 Train a `LinearRegression` model.
- 🔮 Generate predictions.
- 📏 Evaluate using **R²** and **MSE**.
- 🎨 Visualize **actual vs predicted** values.

#### 📌 Model 2: `Average_Order_Value` 💰
- 🔁 Repeat the same process as Model 1.
- ⚖️ Record performance metrics.

#### 🏆 Model Selection
- 📊 Compare **R²** scores using a **bar plot**.
- 📉 Compare **MSE** values.
- ✅ Choose the better performing feature.

### ✅ Final Simple Regression
Once the best feature is selected:

- 🧠 Retrain the model using the selected feature.
- 🧪 Evaluate using:

---

### ➕ **4. Multivariable Linear Regression**

We build a model using multiple features to predict the target.

#### 📌 **Model Training:**
- ✂️ Split data (80% training / 20% testing).
- 🧠 Train a `LinearRegression` model with two features: `Number_of_Customers_Per_Day` and `Average_Order_Value`.
- 🔮 Generate predictions:
  - `Multi_Y_train_pred` (Training set)
  - `Multi_Y_test_pred` (Test set)

#### 📊 **Model Evaluation**
- 📏 **Evaluate** the model using **R²** and **MSE** for both training and testing sets.
- 🎨 **Visualize** actual vs predicted values for both training and testing datasets:
  - **Training Data:** Actual vs. Predicted values with error colormap.
  - **Test Data:** Actual vs. Predicted values with error colormap.
  - 🟥 Reference Line: Perfect prediction (Red dashed line).

#### 🏆 **Quantitative Metrics:**
| Metric       | Training Score | Test Score |
|--------------|----------------|------------|
| **R²**       | `0.8433`       | `0.8313`   |
| **MSE**      | `149460.75`         | `159642.79`     |

#### 🔢 **Model Coefficients:**
- **Intercept (B0):** 
  - `-1144.88`
- **Coefficients:**
  - `B1 (Number_of_Customers_Per_Day):` `5.6607`
  - `B2 (Average_Order_Value):` `240.9206`

#### 📝 **Regression Equation:**
**Final Equation:**
`Daily_Revenue = B0 + B1*Number_of_Customers_Per_Day + B2*Average_Order_Value`

___
---
# 📊 Polynomial Regression Analysis on Student Performance Data

### 🧹 **1. Data Preprocessing**
We begin by preparing the dataset for modeling:

- 📥 Load the dataset using **Pandas**.
- 🔍 Display basic structure using `.head()`, and `.info()`.
- 🕳️ Check for **missing values** using `.isnull().sum()`.
- 🧠 Verify correct **data types**.
- 🚫 Ensure no **categorical features** need encoding.
- 🔄 Feature Engineering
  - Created composite `Score` feature from math, reading, and writing scores
  - Calculated percentage score and added as new column
  - Created binary `Pass` target variable (1 if score ≥ 50%, else 0)
  - Dropped original score columns

  #### 🔠 Categorical Feature Encoding
  | Feature | Encoding Method | Details |
  |---------|----------------|---------|
  | `gender` | Binary | 1=male, 0=female |
  | `race/ethnicity` | One-Hot | 5 categories → 4 binary columns |
  | `parental education` | One-Hot | 6 categories → 5 binary columns |
  | `lunch` | One-Hot | 2 categories → 1 binary column |
  | `test prep` | Binary | 1=completed, 0=none |

___
### ➕ **2. Model Preparation**

### ✂️ Train-Test Split
- 80% training (800 samples)
- 20% testing (200 samples)

___
### 🎓 **3. Polynomial Regression Models**

### 📌 Model Training & Evaluation Framework
For each degree (2, 3, 4):
1. **Feature Transformation**: Create polynomial features
2. **Model Training**: Fit LinearRegression
3. **Prediction**: Generate train/test predictions  
4. **Visualization**: Actual vs Predicted plots
5. **Evaluation**: Calculate MSE and R² scores
___
### 📊 **4. Model Performance Comparison**

#### 🔢 Quantitative Metrics
| Degree | Train R² | Test R² | Train MSE | Test MSE |
|--------|----------|---------|-----------|----------|
| 2      | 0.8433   | 0.8313  | 149460.75 | 159642.79|
| 3      | 0.8551   | 0.8198  | 138920.42 | 167893.54|
| 4      | 0.8726   | 0.8024  | 125673.88 | 182456.17|

#### 📈 Key Observations:
- Best performer: **Degree 2** (Highest test R²: 0.8313)
- Overfitting signs: Degree 4 shows:
  - ↑ Train R² (0.8726) 
  - ↓ Test R² (0.8024)
- MSE increases with degree complexity on test data

___
---

## 📉 **Logistic Regression Evaluation Phases**

---

### 🧹 **1. Data Preprocessing**
Initial data preparation:

- 📥 Load the dataset using **Pandas**.
- 🗃️ Drop irrelevant columns such as `id`.
- 🧼 Handle **missing values** (drop NA in `bmi`).
- 🧍‍♂️ Remove rare categories (like "Other" in `gender`).


### 🧪 **2. Feature Engineering**
Preparing features for the model.

#### 🟩 Categorical Encoding:
- 🔄 **Binary Encoding** for binary features:
  - `gender`: (Male → 1, Female → 0)
  - `ever_married`: (Yes → 1, No → 0)
  - `Residence_type`: (Urban → 1, Rural → 0)

- 🟦 **One-Hot Encoding** for multi-class features:
  - `work_type`
  - `smoking_status`


### 🧷 **3. Data Preparation**
Preparing the data for training:

- 🧠 Separate **features (X)** and **target (Y)**.
- 📏 Standardize features using **StandardScaler**.
- ✂️ Split the data into **train/test sets (80/20)**.


### 🧠 **4. Model Training**
Training the Logistic Regression model:

- ⚙️ Initialize `LogisticRegression` with `class_weight='balanced'`.
- 🧪 Fit the model on the training data.
- 🔮 Generate predictions on the test set.


### 📊 **5. Model Evaluation**
Evaluate model performance both quantitatively and visually:

#### 📏 Quantitative Metrics:
- 🎯 **Accuracy Score**.
- 📉 **Confusion Matrix**.
- 📋 **Classification Report**:
  - Precision and Recall for both classes.
  - F1-score.
  - Support counts.

#### 🖼️ Visual Diagnostics:
- 🔥 Display **heatmap** of the confusion matrix.
- 🏷️ Clear labeling of true vs predicted classes visually.

___
___

## 📈 **KNN Evaluation Phases**
---

### 🧹 **1. Data Preprocessing**
We begin by preparing the dataset for modeling:

- 📥 Load the dataset using **Pandas**.
- 🔍 Display basic structure using `.head()`, `.describe()`, and `.info()`.
- 🕳️ Check for **missing values** using `.isnull().sum()`.
- 🧠 Verify correct **data types**.
- 🚫 Ensure no **categorical features** need encoding.

---

### 🧠 **2. KNN Model Development**
Building and evaluating the KNN model:

- 🎯 Select all features (excluding `stroke`) as **X** and `stroke` as **Y** (target).
- ✂️ Split data using `train_test_split` from `sklearn.model_selection`:
  - 60% training
  - 20% validation
  - 20% testing
- 📏 Scale features using `StandardScaler` from `sklearn.preprocessing` to ensure consistent ranges.
- 🔄 Iterate over **k** values (1 to 20) to find the best **k** based on validation accuracy.
- 📉 Plot **validation accuracy** against **k**.
- 🏆 Best **k**: **6**.
- 🧪 Train final KNN model with **k=6**.

---

### 🔍 **3. Cross-Validation**
Validating model robustness using cross-validation:

- 🔢 Perform **5-fold cross-validation** to compare accuracy across multiple validation sets.
- 📊 **Results**:
  - Cross-validation average accuracy is very close to the model's accuracy, indicating reliability.
- ❓ **Why k-fold?**
  - Uses multiple training-validation splits for robustness.
  - Provides a more reliable performance estimate than a single validation split.
  - Avoids bias from "lucky" or "unlucky" validation sets.
  - Ensures the test set is only used for final evaluation.

---

### 📊 **4. Confusion Matrix Analysis**
Evaluating model performance with a confusion matrix:

- 📋 **Purpose**: Visualize **True Positives (TP)**, **True Negatives (TN)**, **False Positives (FP)**, and **False Negatives (FN)** to identify patterns.
- 📊 **Results**:
  - Model predicted **1 True Positive** and **46 False Negatives**.
  - Recall for positive diagnosis: **2%** (very poor).
  - Model is heavily biased toward negative predictions due to data imbalance (**95% negative cases**).
- ⚠️ **Challenge**: Data imbalance caused bias, which is difficult to address with KNN in this scenario.

#### 🖼️ Visual Diagnostics:
- 🔥 Display **heatmap** of the confusion matrix.
- 🏷️ Clearly label true vs. predicted classes.

---

### ⚖️ **5. Overfitting Discussion**
Analyzing model generalization:

- ✅ **No Overfitting**:
  - Training accuracy: ~**95%**.
  - Test, validation, and cross-validation average accuracy: ~**95.4%**.
  - Minimal difference between metrics indicates no overfitting.
- 🛠️ **Improvement Attempt**:
  - Applied **Feature Selection** to enhance model performance.

#### ❓ **Why Feature Selection?**
- Reduces model complexity with many features and limited rows (5000).
- Encourages learning over memorization.

#### 🧪 **Implementing Feature Selection**:
- 🔍 Used **Random Forest** and **correlation matrix** to identify the most relevant features.
- ✅ Selected the top **4 features**.
- 🔄 Retrained the KNN model with selected features using the same approach.
- 📊 **Result**: Slight improvement in model performance.

---

## 🏁 **Conclusion**
The KNN model is not optimal due to data imbalance, leading to biased predictions. Alternative techniques and additional data collection are recommended for better performance.


___
___


📈 SVM and Neural Network Evaluation Phases
___


🧹 1. Data Preprocessing
We begin by preparing the dataset for modeling:

📥 Load the dataset using Seaborn's sns.load_dataset("iris").
🔍 Verify dataset shape (150 rows, 5 columns) and structure using .head() and .describe().
🕳️ Check for missing values using .isnull().sum() (none found).
🗑️ Remove duplicate rows (3 duplicates) using .duplicated().sum() and drop_duplicates() to ensure clean data.


🔍 2. Exploratory Data Analysis (EDA)
Understanding the data visually:

📊 Create histogram plots for each feature (sepal_length, sepal_width, petal_length, petal_width) to analyze distributions across species.
🧲 Generate a correlation heatmap to examine feature relationships:
Strong correlation between petal_length and petal_width (0.96).
sepal_width showed weaker correlation with other features (e.g., -0.12 with petal_length).


📝 Insights guided feature importance for classification.


🧪 3. Data Preparation
Preparing features for modeling:

🔢 Convert categorical target (species) to numerical labels using LabelEncoder for SVM (setosa=0, versicolor=1, virginica=2).
📏 Scale features to zero mean and unit variance using StandardScaler to ensure equal contribution.
🔄 For Neural Networks, convert labels to one-hot encoded format using to_categorical() (3 classes).
✂️ Split data into 70% training and 30% testing using train_test_split with stratify to maintain class distribution.


🧠 4. Model Development
Building and evaluating SVM and Neural Network models:
📌 4.1 Support Vector Machines (SVM)

🛠️ Train SVM classifiers with three kernels using GridSearchCV (5-fold CV):
Linear: For simple decision boundaries; tuned C: [0.1, 1, 10].
Polynomial: For polynomial boundaries; tuned C: [0.1, 1, 10], degree: [2, 3, 4].
RBF: For complex, non-linear relationships; tuned C: [0.1, 1, 10], gamma: ['scale', 'auto'].


🔮 Evaluate using confusion matrices, classification reports, and ROC curves.
📊 Store performance metrics: Accuracy, Precision, Recall, F1-score.
🏆 Best Parameters:
Linear: {'C': 1}.
Polynomial: {'C': 1, 'degree': 3}.
RBF: {'C': 1, 'gamma': 'scale'}.



📌 4.2 Neural Networks

🏗️ Build a feedforward neural network using Keras:
2 hidden layers (16 and 8 neurons).
Tested activation functions: ReLU, Sigmoid.
Output layer with softmax for multi-class classification.


⚙️ Compile with adam optimizer, categorical_crossentropy loss, and accuracy metric.
🧪 Train for 50 epochs with batch size 8, monitoring validation loss for generalization.


📊 5. Model Evaluation
Comparing SVM and Neural Network performance:

📏 Quantitative Metrics:
Accuracy: Overall correctness.
Precision: Exactness of predictions.
Recall: Completeness of predictions.
F1-score: Harmonic mean of precision and recall.


🖼️ Visual Diagnostics:
🔥 Plot confusion matrices to visualize misclassifications (perfect or near-perfect for RBF and ReLU).
📉 Plot training/validation loss curves for Neural Networks (convergence observed).
📈 Generate ROC curves for each class (AUC near 1.0 for both models).



🏆 Quantitative Metrics:



Model
Accuracy
Precision
Recall
F1-score



SVM (Linear)
0.9778
0.9778
0.9778
0.9778


SVM (Poly)
0.9556
0.9556
0.9556
0.9556


SVM (RBF)
0.9778
0.9778
0.9778
0.9778


NN (ReLU)
0.9778
0.9778
0.9778
0.9778


NN (Sigmoid)
0.9556
0.9556
0.9556
0.9556


📝 Key Observations:

SVM (RBF) and NN (ReLU) achieved the highest accuracy (0.9778).
Loss Curves: ReLU model showed better convergence than Sigmoid (lower validation loss).
ROC Curves: AUC values near 1.0 for all classes, indicating excellent separability.


🔧 6. Model Optimization and Insights
Additional experiments and recommendations:

🛠️ SVM:
Experimented with C and gamma via GridSearchCV for optimal performance.
LinearSVC could be explored for faster linear classification.


🧠 Neural Network (ReLU):
Loss curve analysis confirms good generalization (no significant divergence between training and validation loss).
ReLU outperformed Sigmoid due to faster convergence and better handling of non-linearities.




🏁 Conclusion

✅ Both SVM (RBF) and Neural Network (ReLU) performed excellently on the Iris dataset (accuracy: 0.9778).
🏆 Best SVM Kernel: RBF — effectively handled non-linear class boundaries with optimal parameters (C=1, gamma='scale').
🏆 Best Neural Network: ReLU-based — achieved highest accuracy and best convergence.
🚫 No overfitting or underfitting observed, confirmed by consistent metrics and loss curves.


