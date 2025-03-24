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
   * **Targets**: ADHD Diagnosis and Sex
   * **Functional MRI Connectome Matrices**: fMRI data for brain activity mapping
   * **Socio-demographic Information**: This includes both quantitative and categorical metadata such as age, ethnicity, race, and educational levels of the participants.

2. Test Folder (300+ subjects):
   * **Functional MRI Connectome Matrices**: Functional MRI data for new subjects, which will be used for predictions in the competition.
   * **Socio-demographic Information**: Similar to the training set, this includes quantitative and categorical socio-demographic metadata, but without the target labels (ADHD and sex) for the subjects. These are used to test the models.

Datasets and support are provided by the Healthy Brain Network (HBN), the signature scientific initiative of the Child Mind Institute, and the Reproducible Brain Charts project (RBC).
### Data exploration and preprocessing approaches
* 
### Challenges and assumptions when working with the dataset(s)

**Potential visualizations to include:**

* Plots, charts, heatmaps, feature visualizations, sample dataset images

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
* How your model performed across different skin tones (AJL)
* Insights from evaluating model fairness (AJL)

**Potential visualizations to include:**

* Confusion matrix, precision-recall curve, feature importance plot, prediction distribution, outputs from fairness or explainability tools

---

## **🖼️ Impact Narrative**

**Answer the relevant questions below based on your competition:**

**WiDS challenge:**

1. What brain activity patterns are associated with ADHD; are they different between males and females, and, if so, how?
2. How could your work help contribute to ADHD research and/or clinical care?

**AJL challenge:**

As Dr. Randi mentioned in her challenge overview, “Through poetry, art, and storytelling, you can reach others who might not know enough to understand what’s happening with the machine learning model or data visualizations, but might still be heavily impacted by this kind of work.”
As you answer the questions below, consider using not only text, but also illustrations, annotated visualizations, poetry, or other creative techniques to make your work accessible to a wider audience.
Check out [this guide](https://drive.google.com/file/d/1kYKaVNR\_l7Abx2kebs3AdDi6TlPviC3q/view) from the Algorithmic Justice League for inspiration!

1. What steps did you take to address [model fairness](https://haas.berkeley.edu/wp-content/uploads/What-is-fairness_-EGAL2.pdf)? (e.g., leveraging data augmentation techniques to account for training dataset imbalances; using a validation set to assess model performance across different skin tones)
2. What broader impact could your work have?

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

