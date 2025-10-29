# WiDS Datathon 2025 
_Unraveling the Mysteries of the Female Brain: Sex Patterns in ADHD_

---

## **👥 Team Members**

### UCLA_WiDS_Team 26

| Name | GitHub Handle | Contribution |
| ----- | ----- | ----- |
| Mandy Vien | @ManVien | Data preprocessing pipeline, feature engineering, and model development |
| Virounika Mina | @virounika | Model building, tuning, cross-validation, and evaluation |

---

## **🎯 Project Highlights**

* Developed a **multi-output classification model** using **XGBoost** and **Random Forest** to predict both ADHD diagnosis and sex from complex neuroimaging data (fMRI) and socio-demographic features.

* Achieved an **F1-score of 0.8611** for ADHD prediction, but sex prediction was more challenging with an **F1-score of 0.5132**.

* Applied **PCA** for dimensionality reduction on the high-dimensional fMRI data to optimize performance and reduce overfitting.

* The final submission on Kaggle achieved a **leaderboard score of 0.71489**, indicating strong performance, especially on ADHD prediction.

🔗 [WiDS Datathon 2025 | Kaggle Competition Page](https://www.kaggle.com/competitions/widsdatathon2025/overview)

---

## **👩🏽‍💻 Setup & Execution**

To replicate and run this project:

**1. Clone the Repository:**
`git clone https://github.com/your-repository-url.git`

**2. Access the Dataset:**
* Download the dataset from the Kaggle WiDS Datathon 2025 page.
* Ensure the train_tsv and test_tsv folders are correctly placed under the same path direction for seamless integration.

**3. Run the Jupyter Notebook:**
* Launch Jupyter to run the project
* Execute the notebook to preprocess the data, train models, and generate predictions.

---

## **🏗️ Project Overview**

The **WiDS Datathon 2025** competition asks participants to predict ADHD diagnosis and sex using **functional MRI data** and **socio-demographic data**. This challenge has critical real-world implications, especially regarding the **underdiagnosis of ADHD in females**. The competition is aligned with the **Break Through Tech AI Program** to empower women in AI, offering a platform for them to apply their data science skills while solving a societal issue.

### 1. Objective:
The main objective of the WiDS Datathon 2025 is to create a multi-outcome model that can predict two target variables:
  1. **ADHD Diagnosis** (1 = ADHD, 0 = No ADHD)
  2. **Sex** (1 = Female, 0 = Male)
 
### 2. Real-World Significance:
* Participants will work with fMRI data and socio-demographic, emotional, and parenting information to address the challenge question: "What brain activity patterns are associated with ADHD, and how do they differ between males and females?"
  
* This challenge has significant real-world implications, especially in improving the diagnosis and treatment of ADHD, which is often underdiagnosed in females due to their symptoms being less obvious. By identifying patterns in brain activity associated with ADHD, particularly for females, this work could lead to earlier diagnoses and more effective, personalized treatments. This can have a transformative impact on mental health outcomes, helping individuals with ADHD lead healthier, more functional lives. Additionally, this research can enhance the understanding of neuropsychiatric disorders and improve brain health, particularly for women.

---

## **📊 Data Exploration**

### Datasets:
1. Training Data (1,200+ subjects):
   * **Targets**:
       * **ADHD Diagnosis (ADHD_Outcome)**: This binary variable indicates whether a participant has been diagnosed with ADHD (1 = ADHD, 0 = No ADHD).
       * **Sex (Sex_F)**: This binary variable indicates the sex of the participant (1 = Female, 0 = Male).
   * **Functional MRI Connectome Matrices**: Functional brain imaging data in the form of connectome matrices, which capture brain activity across different regions over time.
   * **Socio-demographic Information**:
       * **Quantitative Metadata**: Includes numerical data such as scores from the Edinburgh Handedness Questionnaire (EHQ_EHQ_Total), Ishihara Color Vision Test (ColorVision_CV_Score), and scores from the Alabama Parenting Questionnaire (APQ_P_APQ_P_CP).
       * **Categorical Metadata**: Includes demographic and parental data, such as ethnicity, race, and education level (e.g., Barratt_Barratt_P1_Edu representing the educational level of the participant's parent).

2. Test Data (300+ subjects):
   * **Functional MRI Connectome Matrices**: Functional MRI data for new subjects, which will be used for predictions in the competition.
   * **Socio-demographic Information**: Similar to the training set, this includes quantitative and categorical socio-demographic metadata, but without the target labels (ADHD and sex) for the subjects. These are used to test the models.

Datasets and support are provided by the Healthy Brain Network (HBN), the signature scientific initiative of the Child Mind Institute, and the Reproducible Brain Charts project (RBC).

### Data exploration and preprocessing approaches
The dataset includes a mixture of quantitative and categorical variables, and various preprocessing steps are required to prepare it for modeling:

1. **Categorical Variables**: Categorical columns such as ethnicity, race, and occupation are one-hot encoded to create binary features for each category. This is crucial to avoid misleading ordinal relationships that could arise from directly encoding categorical variables as numbers.

2. **Quantitative Variables**: Quantitative variables like age and scores from emotional assessments are handled by checking for outliers and missing values. These are visualized using histograms and boxplots to understand their distribution and potential impact on the model.

3. **Handling Missing Data**: Missing values in the dataset are addressed using **KNN imputation** for both **numerical features** (such as MRI scan age) and **one-hot encoded categorical features**. The **KNNImputer** is used to estimate missing values by considering the nearest neighbors in the dataset. For categorical features, the missing values are imputed based on the most similar rows in the **one-hot encoded feature space**.

4. **Combining Data**: After preprocessing, the datasets (categorical, quantitative, and fMRI data) are merged into a single comprehensive training and testing set using the participant ID as the unique key.

### Challenges and assumptions when working with the datasets
1. **Missing Data**: Handling missing values, especially in socio-demographic information, presents a challenge. Imputation methods like **mean imputation, forward/backward filling, KNN** are tried and used, but these might not always capture the underlying distribution of the data, potentially impacting the performance of the model.

2. **Data Imbalance**: There is a noticeable **gender imbalance** in the dataset (more males than females), which could introduce bias in model predictions. To address this issue, techniques like **weighted loss functions** and **resampling methods** were used to ensure that the model doesn't favor the majority class.

3. **High Dimensionality**: The **fMRI connectome matrices** are high-dimensional, making feature selection and dimensionality reduction essential for building an efficient model. Not all features are equally important for predicting ADHD and Sex, so techniques like **PCA** was applied to retain the most significant features, reducing noise and computational cost while maintaining model performance.

### Potential visualizations to include:

* Plots, charts, heatmaps, feature visualizations, sample dataset images
  
The training dataset includes the Socio-demographic Information and the Functional MRI Connectome Matrices.

![train_df](https://github.com/user-attachments/assets/ca35c580-1181-4fb1-9530-542ca9d947cd)

---

## **🧠 Model Development**

### 1. Models Used:
* **XGBoost**: Utilized for both **ADHD and Sex prediction** due to its performance in handling imbalanced datasets and its capacity to learn complex relationships.

* **Random Forest**: Used for comparison to XGBoost, especially for ADHD prediction, which demonstrated strong performance.

### 2. Hyperparameter Tuning:
* **Feature Selection:**
  * **PCA (Principal Component Analysis)** was applied to reduce dimensionality and retain only the most significant features. The first 10 components were used for model training.
  * **Correlation-based Feature Selection** was used to select top features that were most correlated with the target variables (ADHD and Sex).

* **Hyperparameter Tuning:**
  * **XGBoost**: Hyperparameters such as **learning rate**, **max_depth**, and **n_estimators** were fine-tuned using cross-validation. The **scale_pos_weight** was adjusted to address class imbalance in **Sex prediction**.
  * **Random Forest**: Tuned the **n_estimators** and **max_depth** to find a balance between model complexity and overfitting. Cross-validation was used to avoid overfitting and to determine the optimal settings.

### 3. Training Setup:
* **Cross-Validation**: We performed **3-fold cross-validation** on both tasks (ADHD and Sex prediction) to ensure that the models generalized well.

* **Data Split**: 100% of the available data was used for training and validation through cross-validation.

* **Evaluation Metric**: The **F1-score** was used as the evaluation metric for both tasks, ensuring a balance between precision and recall, particularly for the imbalanced **Sex prediction** task.

* **Baseline Performance**: We started with baseline models (e.g., logistic regression, basic decision trees) to compare against the final models. The **Random Forest** and **XGBoost** models showed significant improvements over the baseline in both F1-score and overall predictive power.

---

## **📈 Results & Key Findings**

### 1. Performance Metrics:
* **ADHD Prediction:**
  * F1-scores:
    * Fold 1: 0.8611
    * Fold 2: 0.8558
    * Fold 3: 0.8301
    * **Mean F1-score: 0.8490**

* **Sex Prediction:**
  * F1-scores:
    * Fold 1: 0.5161
    * Fold 2: 0.5235
    * Fold 3: 0.5000
    * **Mean F1-score: 0.5132**

* **Kaggle Leaderboard**: The final submission achieved a **score of 0.71489**, indicating strong model performance, particularly in **ADHD prediction**.

### 2. Overall Model Performance:
* **ADHD Prediction**: The model achieved solid performance with a mean **F1-score of 0.8490**, which indicates that the model can effectively identify individuals with ADHD.

* **Sex Prediction**: The model faced challenges, with a **mean F1-score of 0.5132**, suggesting that the subtle differences in brain activity between males and females were difficult to capture effectively with the given data.

### 3. Model Performance Across Different Groups (Fairness Insights):
* **Fairness for ADHD**: To address the underdiagnosis of ADHD, particularly in females, a **weighted loss function** was used to give **female ADHD cases** more importance during training. This helped improve performance for females in the **ADHD prediction** task.

* **Sex Prediction Fairness**: The **Sex prediction model** struggled with class imbalance and subtle differences in brain activity between sexes, resulting in lower performance in predicting **female sex**. This suggests a potential **bias** in the model’s learning.

### 4. Insights from Evaluating Model Fairness:
**Bias in Sex Prediction**: The **low F1-score** for **Sex prediction** highlights potential **gender biases** in the data. Further adjustments to model fairness, such as **rebalancing the dataset** or exploring **adversarial debiasing techniques**, could help address these biases.

Potential Visualizations to Include:
* **Confusion Matrix**:
A confusion matrix for both ADHD and Sex prediction will clearly show the true positives, false positives, true negatives, and false negatives, helping assess the model’s prediction quality.

* **Precision-Recall Curve**:
Given the class imbalance, particularly for ADHD, a Precision-Recall Curve will provide insights into the trade-off between precision and recall for each class.

* **Feature Importance Plot**:
A feature importance plot will highlight the most influential features from both the fMRI data and socio-demographic features, allowing us to understand which variables played the most significant role in making predictions.

* **Prediction Distribution**:
A plot of predicted probabilities will show how confident the model is in its predictions, which can be insightful for identifying any overconfidence or underconfidence in specific classes.

---

## **🖼️ Impact Narrative**

**WiDS challenge:**

1. **Brain Activity and ADHD**: Our findings suggest that there are distinct brain activity patterns associated with ADHD. These patterns were observed differently between sexes, with females showing less obvious symptoms, highlighting the importance of early and accurate diagnosis.

2. **Contribution to ADHD Research and Clinical Care**: The model's ability to identify these patterns can help researchers and clinicians design more effective treatments for ADHD. Moreover, identifying underdiagnosed ADHD in females may help address the current gender disparity in ADHD diagnoses.

---

## **🚀 Next Steps & Future Improvements**

### 1. Model Limitations:

* The **Sex prediction model** performed below expectations. This may be due to data imbalance and the subtle differences between male and female brain activity in ADHD.

* More advanced models, such as **deep learning techniques**, could potentially improve sex prediction accuracy by capturing more complex relationships within the data.

### 2. Improvements:

Exploring advanced models like deep neural networks for fMRI data could potentially uncover more complex patterns that traditional models like Random Forests might miss.

### 3. Future Directions:

Exploring the use of more advanced neural networks and techniques for handling class imbalance would be beneficial in refining the model further.

---

## **📄 References & Additional Resources**

* WiDS Workshops

---

