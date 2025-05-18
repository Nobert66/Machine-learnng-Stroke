**Machine-learning-Stroke**

This repository contains various machine learning models trained on a stroke dataset using caret in R. The repository contain various screening tool developed by shny to assess individuals who are at risk of developing stroke 

**Study Objectives**

This study aimed to develop a high-performing machine learning model trained on a stroke dataset and deploy it within an interactive Shiny web application. The integrated system is designed for practical use in real-world healthcare settings to facilitate stroke risk assessment, support early diagnosis, and promote personalized treatment strategies.

**Data importation and inspection**

The dataset was imported into R from a CSV file for analysis. Preliminary data exploration was conducted to understand the overall structure of the dataset, including the types and number of variables. A thorough assessment was carried out to identify and address any missing values or duplicate entries, which could potentially bias the results. Additionally, the distribution of the primary study outcome variable was examined using appropriate summary statistics.

**Data Preprocessing**

The variables were converted to their appropriate data types to ensure compatibility with downstream analyses. Categorical variables were label-encoded, assigning them corresponding numeric values to facilitate their use in machine learning models. Anomalies within the dataset were addressed, including the identification and removal of an unknown character in the 'BMI' variable. Additionally, a non-informative column, 'id', which held no predictive value for the machine learning models, was excluded from the analysis. To address class imbalance within the target variable, the majority class was downsampled to achieve a more balanced class distribution, thereby improving model fairness and performanc

**Features Selection**

Feature importance analysis was conducted using the Boruta algorithm, a robust wrapper method built around the random forest classifier, to identify the most relevant attributes for machine learning implementation. The Boruta analysis confirmed that the following variables were important predictors: age, hypertension, heart disease, marital status, work type, average glucose level, BMI, and smoking status. Conversely, gender and residence type were consistently identified as non-informative and thus excluded from the final model to enhance its efficiency and interpretability.

**Splitting the Dataset**
To prepare the data for model development and evaluation, the dataset was partitioned into training and testing subsets using the caTools package in R. Specifically, 80% of the data were randomly allocated to the training set, which was used to train the machine learning models, while the remaining 20% were reserved as the testing set to assess the models’ generalization performance. This stratified split ensured that both subsets maintained a representative distribution of the outcome variable, thereby reducing the risk of sampling bias.

**Preparing the training scheeme.**

To ensure robust and reliable model training, a training control object (fitControl) was defined using the trainControl() function from the caret package in R. The training process employed a repeated 10-fold cross-validation approach, specified by method = "repeatedcv", with number = 10 indicating that the dataset was divided into 10 equal subsets (folds). In each iteration, 9 folds were used for training the model while the remaining fold was used for validation. This process was repeated 3 times (repeats = 3) with different random partitions to reduce variability and provide a more accurate estimate of model performance.

The parameter classProbs = TRUE enabled the computation of class probabilities, which is essential for performance metrics like AUC (Area Under the ROC Curve). Additionally, summaryFunction = twoClassSummary specified that model evaluation should be based on metrics suitable for binary classification problems—specifically ROC (Receiver Operating Characteristic), sensitivity, and specificity. This configuration ensures that model selection is driven by metrics that capture both the discriminatory power and the balance between false positives and false negatives.

