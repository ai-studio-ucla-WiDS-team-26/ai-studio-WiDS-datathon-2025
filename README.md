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

**Provide step-by-step instructions so someone else can run your code and reproduce your results. Depending on your setup, include:**

* How to clone the repository
* How to install dependencies
* How to set up the environment
* How to access the dataset(s)
* How to run the notebook or scripts

---

## **🏗️ Project Overview**

The **WiDS Datathon 2025** competition asks participants to predict ADHD diagnosis and sex using **functional MRI data** and **socio-demographic data**. This challenge has critical real-world implications, especially regarding the **underdiagnosis of ADHD in females**. The competition is aligned with the **Break Through Tech AI Program** to empower women in AI, offering a platform for them to apply their data science skills while solving a societal issue.

### Objective:
The main objective of the WiDS Datathon 2025 is to create a multi-outcome model that can predict two target variables:
  1. **ADHD Diagnosis** (1 = ADHD, 0 = No ADHD)
  2. **Sex** (1 = Female, 0 = Male)
 
### Real-World Significance:
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

### Models Used:
* **XGBoost**: Utilized for both ADHD and Sex prediction due to its performance in handling imbalanced datasets and its capacity to learn complex relationships.

* **Random Forest**: Used for comparison to XGBoost, especially for ADHD prediction, which demonstrated strong performance.

### Hyperparameter Tuning:
* **XGBoost**: Tuned the **learning rate** to 0.1, **max_depth** to 3, and **n_estimators** to 100 for sex prediction, adjusting the **scale_pos_weight** parameter to address class imbalance.

* **Random Forest**: Used **50 estimators** with optimized hyperparameters to balance bias and variance for ADHD prediction.

### Training Setup:
**Cross-Validation**: We used **3-fold cross-validation** to ensure robustness and mitigate overfitting. The **F1-score** was the evaluation metric, focusing on balancing precision and recall for both target variables.

---

## **📈 Results & Key Findings**

**Describe (as applicable):**

* Performance metrics (e.g., Kaggle Leaderboard score, F1-score)
* How your model performed overall
* Insights from evaluating model fairness

**Potential visualizations to include:**

* Confusion matrix, precision-recall curve, feature importance plot, prediction distribution, outputs from fairness or explainability tools

---

## **🖼️ Impact Narrative**

**WiDS challenge:**

1. Brain Activity and ADHD: Our findings suggest that there are distinct brain activity patterns associated with ADHD. These patterns were observed differently between sexes, with females showing less obvious symptoms, highlighting the importance of early and accurate diagnosis.

2. Contribution to ADHD Research and Clinical Care: The model's ability to identify these patterns can help researchers and clinicians design more effective treatments for ADHD. Moreover, identifying underdiagnosed ADHD in females may help address the current gender disparity in ADHD diagnoses.

---

## **🚀 Next Steps & Future Improvements**

### Model Limitations:

Sex prediction was the most challenging aspect of the model, likely due to data imbalance and the subtle differences in brain activity between males and females. Future iterations could benefit from more balanced datasets or advanced deep learning approaches.

### Improvements:

* Incorporating additional features such as genetic data or more granular psychological assessments could enhance the model’s performance.

* Exploring advanced models like deep neural networks for fMRI data could potentially uncover more complex patterns that traditional models like Random Forests might miss.

### Future Directions:

Fairness and Bias Mitigation: Future work could focus on reducing bias further by ensuring the model performs equally well across different demographic groups.

---

## **📄 References & Additional Resources**

* Cite any relevant papers, articles, or tools used in your project

---

