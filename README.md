## 🫀 Project 1: Heart Disease Prediction

**Objective:** To predict the presence of heart disease in a patient based on their medical parameters using Machine Learning.

### 🛠️ Steps Implemented:

1. **Data Loading & Cleaning 🧹**
   - Loaded the dataset (`heart_disease_internship.csv`).
   - Cleaned the `sex` column by mapping string values ('male'/'female') into binary numbers (1/0).
   - Handled missing values in continuous features (`trestbps`, `chol`, `thalach`) by replacing them with their respective column medians.

2. **Feature Selection (Smart Approach) 🎯**
   - Instead of feeding all 13 features and confusing the model, selected only the top 5 most highly correlated features: `ca`, `thalach`, `cp`, `age`, and `oldpeak`.
   - This approach prevented overfitting and made the model lightweight.

3. **Data Splitting & Scaling ⚖️**
   - Split the dataset into an 80-20 ratio (80% for training, 20% for testing).
   - Applied `StandardScaler` to bring all features to a common scale, ensuring that features with larger numeric values don't dominate the model.

4. **Model Selection & Training 🤖**
   - **Algorithm Used:** `Logistic Regression`
   - **Why?** Real-world medical data shouldn't have a 99% accuracy (which usually indicates severe overfitting). Logistic Regression with L2 penalty (`C=0.1`) was chosen to build a generalized, practical model that strictly fits within the realistic target accuracy range of 70% - 89%.

5. **Evaluation & Results 📊**
   - **Training Accuracy:** ~71.75%
   - **Test Accuracy:** ~74.00%
   - Generated a **Confusion Matrix** and **Classification Report** to analyze True Positives and False Negatives. 
   - **Conclusion:** The model shows high stability and is exceptionally good at identifying healthy patients (88% Recall for Class 0).


## 🍷 Project 2: Wine Quality Prediction

**Objective:** To predict the quality of wine (rated on a scale from 3 to 8) based on its chemical properties such as acidity, pH, alcohol, and sugar levels.

### 🛠️ Steps Implemented:

1. **Data Loading & Cleaning 🧹**
   - Loaded the dataset (`winequality.csv`).
   - Handled missing data by imputing null values in columns like `chlorides`, `pH`, and `sulphates` with their respective column medians to preserve data integrity.

2. **Data Splitting & Scaling ⚖️**
   - Separated the dataset into features (X) and the target variable `quality` (y).
   - Split the data into an 80-20 ratio (80% for training, 20% for testing).
   - Applied `StandardScaler` to normalize the dataset. **Note:** This step was absolutely crucial because distance-based algorithms like SVM perform poorly if the data is not scaled.

3. **Model Selection & Training 🤖**
   - **Algorithm Used:** `Support Vector Machine (SVM)`
   - **Configuration:** Used the Radial Basis Function (`kernel='rbf'`) with `C=1.0`.
   - **Why?** Predicting wine quality is a **Multi-Class Classification** problem. Real-world wine data has significant overlap (e.g., the chemical makeup of a '5' rated wine is very similar to a '6' rated wine). SVM with an 'rbf' kernel is excellent at finding complex, non-linear decision boundaries between these closely overlapping classes.

4. **Evaluation & Results 📊**
   - **Test Accuracy:** ~61% - 62%
   - **Conclusion:** Unlike binary classification, achieving a 90%+ accuracy on this multi-class dataset is highly prone to overfitting due to the subjective nature of human wine ratings. A 61% accuracy is a highly realistic, stable, and practical benchmark for this specific dataset, proving that the model generalizes well rather than just memorizing the training data.
## 🩸 Project 3: Diabetes Prediction

**Objective:** To predict whether a patient is diabetic or not based on diagnostic medical measurements such as Glucose levels, BMI, Age, and Insulin.

### 🛠️ Steps Implemented:

1. **Data Preparation 🧹**
   - Loaded the dataset (`diabetes.csv`).
   - Separated the independent medical features (Pregnancies, Glucose, BloodPressure, etc.) from the target variable (`Outcome`).

2. **Data Splitting & Scaling ⚖️**
   - Split the data into Training and Testing sets.
   - Applied `StandardScaler` to ensure all medical parameters are on a uniform scale. This is a critical step because features like 'Insulin' naturally have much larger numerical ranges than features like 'DiabetesPedigreeFunction', and without scaling, the model would become biased.

3. **Model Selection & Training 🤖**
   - **Algorithm Used:** `Support Vector Machine (SVM)`
   - **Configuration:** Configured the model with a Radial Basis Function (`kernel='rbf'`).
   - **Why?** Medical conditions are rarely triggered by a single clear threshold. SVMs with non-linear kernels like RBF are exceptionally good at finding complex, curved boundaries in biological datasets to separate diabetic and non-diabetic patients.

4. **Evaluation & Results 📊**
   - **Training Accuracy:** ~77.20%
   - **Test Accuracy:** ~66.88%
   - **Conclusion:** The model successfully learns the general biological patterns without falling into the trap of severe overfitting (memorizing the data), making it a realistic baseline for health condition predictions.

---

## 🏠 Project 4: House Price Prediction (Regression)

**Objective:** To predict the exact market price of a house based on property attributes like square footage, number of rooms, house age, and distance to the city.

### 🛠️ Steps Implemented:

1. **Data Preparation 🧹**
   - Loaded the real estate dataset (`house_prices.csv`).
   - Isolated the continuous target variable (`price`) from predictive features (`sqft_living`, `bedrooms`, `quality_score`, etc.).

2. **Data Splitting & Scaling ⚖️**
   - Split the data into Training and Testing sets.
   - Standardized all features using `StandardScaler` so that massive numbers like `sqft_living` don't completely overshadow smaller-scale yet highly important features like `bathrooms` or `floors`.

3. **Model Selection & Training 🤖**
   - **Algorithm Used:** `Random Forest Regressor`
   - **Configuration:** Set `n_estimators=200` (combining 200 individual decision trees) and `max_depth=10` to control the growth of the trees.
   - **Why?** Unlike Classification (which predicts categories like 0 or 1), this is a **Regression** problem. Random Forest excels here by capturing complex, real-world pricing logic (e.g., how the unique combination of 'High Quality Score' + 'Low Distance to City' drastically multiplies a property's value).

4. **Evaluation & Results 📊**
   - **Training R² Score:** 0.991 (99.1%)
   - **Test R² Score:** 0.943 (94.3%)
   - **Conclusion:** Outstanding results! The model achieved an $R^2$ score of ~0.94 on unseen test data. This means the model can accurately explain and predict 94% of the real-world variance in house prices, proving it to be highly robust and production-ready.
