# WiDS Datathon 2025
_Unraveling the Mysteries of the Female Brain: Sex Patterns in ADHD_

---

### **👥 Team Members**

| Name | GitHub Handle | Contribution |
| ----- | ----- | ----- |
| Mandy Vien | @ManVien | Data preprocessing, built models |
| Virounika Mina | @virounika | Built models |

---

## **🎯 Project Highlights**

**Example:**

* Built a \[insert model type\] using \[techniques used\] to solve \[Kaggle competition task\]
* Achieved an F1 score of \[insert score\] and a ranking of \[insert ranking out of participating teams\] on the final Kaggle Leaderboard
* Used \[explainability tool\] to interpret model decisions
* Implemented \[data preprocessing method\] to optimize results within compute constraints

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

* The WiDS Datathon 2025 is a global competition where participants are tasked with building machine learning models to predict both an individual’s sex and their ADHD diagnosis using functional brain imaging data. This challenge is particularly meaningful as it focuses on ADHD diagnosis, which often affects males and females differently, with females being more likely to be undiagnosed. The competition is aligned with the Break Through Tech AI Program's goal to empower women in AI by providing them with a platform to develop their data science skills while tackling real-world problems.
* The main objective of the WiDS Datathon 2025 is to create a multi-outcome model that can predict two target variables:
  1. ADHD (1=yes, 0=no)
  2. Sex (1=female, 0=male)
* Participants will work with fMRI data and socio-demographic, emotional, and parenting information to address the challenge question: "What brain activity patterns are associated with ADHD, and how do they differ between males and females?"
* This challenge has significant real-world implications, especially in improving the diagnosis and treatment of ADHD, which is often underdiagnosed in females due to their symptoms being less obvious. By identifying patterns in brain activity associated with ADHD, particularly for females, this work could lead to earlier diagnoses and more effective, personalized treatments. This can have a transformative impact on mental health outcomes, helping individuals with ADHD lead healthier, more functional lives. Additionally, this research can enhance the understanding of neuropsychiatric disorders and improve brain health, particularly for women.

---

## **📊 Data Exploration**

### Datasets:
The datasets for the WiDS Datathon 2025 consists of two primary folders:
1. Training Folder (1,200+ subjects):
   * **Targets**:
       * **ADHD Diagnosis (ADHD_Outcome)**: This binary variable indicates whether a participant has been diagnosed with ADHD (1 = ADHD, 0 = No ADHD).
       * **Sex (Sex_F)**: This binary variable indicates the sex of the participant (1 = Female, 0 = Male).
   * **Functional MRI Connectome Matrices**: Functional brain imaging data in the form of connectome matrices, which capture brain activity across different regions over time.
   * **Socio-demographic Information**:
       * **Quantitative Metadata**: Includes numerical data such as scores from the Edinburgh Handedness Questionnaire (EHQ_EHQ_Total), Ishihara Color Vision Test (ColorVision_CV_Score), and scores from the Alabama Parenting Questionnaire (APQ_P_APQ_P_CP).
       * **Categorical Metadata**: Includes demographic and parental data, such as ethnicity, race, and education level (e.g., Barratt_Barratt_P1_Edu representing the educational level of the participant's parent).

2. Test Folder (300+ subjects):
   * **Functional MRI Connectome Matrices**: Functional MRI data for new subjects, which will be used for predictions in the competition.
   * **Socio-demographic Information**: Similar to the training set, this includes quantitative and categorical socio-demographic metadata, but without the target labels (ADHD and sex) for the subjects. These are used to test the models.

Datasets and support are provided by the Healthy Brain Network (HBN), the signature scientific initiative of the Child Mind Institute, and the Reproducible Brain Charts project (RBC).

### Data exploration and preprocessing approaches
The dataset includes a mixture of quantitative and categorical variables, and various preprocessing steps are required to prepare it for modeling:

1. **Categorical Variables**: Categorical columns such as ethnicity, race, and occupation are one-hot encoded to create binary features for each category. This is crucial to avoid misleading ordinal relationships that could arise from directly encoding categorical variables as numbers.

2. **Quantitative Variables**: Quantitative variables like age and scores from emotional assessments are handled by checking for outliers and missing values. These are visualized using histograms and boxplots to understand their distribution and potential impact on the model.

3. **Handling Missing Data**: Missing values in the dataset are addressed by imputing the mean for numerical features (like MRI scan age), and filling missing categorical data with appropriate values.

4. **Combining Data**: After preprocessing, the datasets (categorical, quantitative, and fMRI data) are merged into a single comprehensive training and testing set using the participant ID as the unique key.

### Challenges and assumptions when working with the dataset(s)
1. **Missing Data**: Handling missing values, especially in socio-demographic information, presents a challenge. Imputation methods like mean imputation, forward/backward filling, KNN are used, but these might not always capture the underlying distribution of the data, potentially impacting model accuracy.

2. **Data Imbalance**: There is a noticeable gender imbalance in the dataset (more males than females), which could introduce bias in model predictions. Special attention is given to this imbalance during model training, such as by using weighted loss functions or resampling techniques.

3. **High Dimensionality**: The fMRI connectome matrices are high-dimensional, making feature selection and dimensionality reduction essential for building an efficient model. Not all features are equally important for predicting ADHD and sex, so techniques like Recursive Feature Elimination (RFE) and L1 regularization are used to identify and retain the most impactful features​.

### Potential visualizations to include:

* Plots, charts, heatmaps, feature visualizations, sample dataset images
  
The training dataset includes the Socio-demographic Information and the Functional MRI Connectome Matrices.

![train_df](https://github.com/user-attachments/assets/ca35c580-1181-4fb1-9530-542ca9d947cd)

---

## **🧠 Model Development**

**Describe (as applicable):**

* Model(s) used (e.g., CNN with transfer learning, regression models)
* Feature selection and Hyperparameter tuning strategies
* Training setup (e.g., % of data for training/validation, evaluation metric, baseline performance)

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

**Answer the relevant questions below based on your competition:**

**WiDS challenge:**

1. What brain activity patterns are associated with ADHD; are they different between males and females, and, if so, how?
2. How could your work help contribute to ADHD research and/or clinical care?

---

## **🚀 Next Steps & Future Improvements**

**Address the following:**

* What are some of the limitations of your model?
* What would you do differently with more time/resources?
* What additional datasets or techniques would you explore?

---

## **📄 References & Additional Resources**

* Cite any relevant papers, articles, or tools used in your project

---

