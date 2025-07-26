# Final Project for Data Mining Course (KOM1338)

## About
As part of the Data Mining course (KOM1338), each student is required to participate in and complete the Data Mining competition provided at https://www.kaggle.com/competitions/kom-1338-data-mining-prediksi-status-kelulusan/overview. Each student must also submit a report (maximum of 2 pages) describing the method and model used. The report should be accompanied by the source code and the trained model.

## Dataset Description
The dataset used is taken from the paper titled: "Predicting Student Dropout and Academic Success" (Valoriza et al., 2022) https://www.mdpi.com/2306-5729/7/11/146. All files (training set, test set, and submission file) are in CSV format with the first column named sample_id (sample number). The training data contains 4,000 observations, while the test set contains around 400 observations. There are 34 features (from "Marital Status" to "GDP") that can be used to predict the target class. There are three possible target classes: Enrolled, Graduated, and Dropout.

You can find the explanation for categorical features here: https://github.com/carmelh/SQL_projects/tree/main/student_data_analysis/Datasets

Columns
- sample_id – sample number
- Marital Status to GDP – features used for prediction
- Target – the label to be predicted

## Evaluation
Each submission is evaluated using Accuracy as the metric.

## Submission File
For each sample_id in the test set, you must predict the Target value (Enrolled, Graduated, Dropout).

---
## Result & Discussion
### EDA & Preprocessing
I started by performing feature exploration. Based on the results, I decided to drop the following columns:
- International: dropped due to lack of meaningful information (mostly contains 0)
- Nacionality: dropped because it lacks useful variation (mostly 1, representing Portuguese nationality, with 3901 out of 4000 data points)
- Educational special needs: dropped due to low variance (mostly 0)
- Previous qualification: dropped (mostly value of 1)
- Curricular units 1st sem (credited): dropped (mostly 0)
- Curricular units 1st sem (without evaluations): dropped (mostly 0)
- Curricular units 2nd sem (credited): dropped (mostly 0)
- Curricular units 2nd sem (without evaluations): dropped (mostly 0)
The target classes are imbalanced: 2000 "Graduated", 1286 "Dropout", and 714 "Enrolled". To address this imbalance, I applied SMOTE (Synthetic Minority Oversampling Technique).

Before modeling, I used LabelEncoder from sklearn.preprocessing to convert the string-based target class into numerical form. Then, all feature columns were standardized. SMOTE was applied afterward to balance the dataset so that each class had an equal number of samples.



### Modeling

**SVM**
- Best set of hyperparameters: {'C': 1, 'degree': 2, 'gamma': 0.1, 'kernel': 'rbf'}
- Private score = 0.71555; Public score = 0.72864

**Random Forest**
- Best set of hyperparameters: {'n_estimators': np.int64(50), 'min_samples_split': np.int64(4), 'min_samples_leaf': np.int64(1), 'max_features': 'log2', 'max_depth': None, 'class_weight': None, 'bootstrap': False}
- Private score = 0.73777; Public score = 0.79396 (all features)
- Private score = 0.74666; Public score = 0.79396 (top 20 feature importance)
- Private score = 0.74222; Public score = 0.76884 (top 10 feature importance)

**XGBoost**
- Best set of hyperparameters: {'subsample': np.float64(0.9), 'scale_pos_weight': 5, 'reg_lambda': 0.1, 'reg_alpha': 0, 'n_estimators': np.int64(250), 'min_child_weight': np.int64(2), 'max_depth': np.int64(9), 'learning_rate': 0.1, 'gamma': 0, 'colsample_bytree': np.float64(0.9)}
- Private score = 0.78666; Public score =  0.76381

**Ensemble Learning**
- Estimator: SVC, RF, XGB
- Private score = 0.78222; Public score = 0.76884 (Hard voting)
- Private score = 0.77777; Public score = 0.76381 (Soft voting)

**Model Stacking**
- Estimator: SVC, RF, XGB
- Meta model: Logistic Regression
- Private score = 0.76888; Public score = 0.76381

---

## Citation
Mushthofa IPB. KOM1338 Data Mining - Prediksi Status Kelulusan. https://kaggle.com/competitions/kom-1338-data-mining-prediksi-status-kelulusan, 2025. Kaggle.
