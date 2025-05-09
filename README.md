# Student Intervention Risk Prediction

This project explores the use of machine learning models to predict **Intervention Risk (IR)** scores for students based on academic performance, participation, and other engagement indicators. The goal is to assist educators in identifying students who may require additional support — even those who are trying hard but still barely getting by.

## Project Overview

We developed and evaluated classification models to:
- Predict student Intervention Risk according to the Response to Intervention (RTI) Tier system
- Calculate a custom **Intervention Risk Score** using weighted academic and behavioral data
- Categorize RTI_Categories based on z-score thresholds. 

## Motivation

Academic intervention is the first step in identifying students who may need additional educational support due to learning disabilities or other academic challenges. In public schools, especially those with high student-to-teacher ratios and limited resources, special education (SPED) departments often struggle to proactively identify all students who require services.
This project introduces a machine learning model that computes an Intervention Risk (IR) Score, a continuous value between 0 and 1, for each student. The IR Score reflects the likelihood that a student may need academic intervention based on a combination of performance, engagement, wellness, and contextual factors. Rather than functioning as a diagnostic tool, the score serves as an early warning system for educators, helping them spot students who might otherwise fall through the cracks.
To support the interpretation of the IR Score, we classify students using the RTI (Response to Intervention) framework. RTI is a widely adopted multi-tiered system for monitoring student progress and delivering targeted support:
  - Tier 1: Core instruction. The majority of students receive classroom teaching and show typical academic progress.
  - Tier 2: Targeted small-group, in-class interventions for students who are at moderate risk of falling behind.
  - Tier 3: Intensive, individualized interventions for students identified as high risk.

*There is also a "Tier 2 Watchlist" to flag students who are trending toward Tier 2 but haven’t crossed the intervention threshold yet to serve as an early warning system for teachers to implement low-cost actions like teacher/parent conversations, or extra attention.*

By mapping IR scores to RTI tier categories using z-score thresholds, this model allows educators to prioritize intervention efforts more effectively and proactively.

## Dataset: Student Performance & Behavior Dataset (Mahmoud Elhemaly) 
- https://www.kaggle.com/datasets/mahmoudelhemaly/students-grading-dataset/

- Features include:
  - `Midterm_Score`
  - `Final_Score`
  - `Quizzes_Avg`
  - `Projects_Score`
  - `Participation`
  - `Study_Hours_Per_Week`
  - `Sleep_hours_per_Night`
  - `Parent_Education_Level`
  - `Family_Income_Level`

- Target variable: `RTI_Category` (multi-class classification)

## 🔍 Methodology

1. **Preprocessing**: Handled missing values, normalized features, and engineered IR scores.
2. **IR Score Calculation**:  
   Weighted as follows:
   - Midterm: 40%
   - Final: 20%
   - Quizzes: 20%
   - Participation: 20%
3. **Models Tested**:
   - K-Nearest Neighbors
   - Support Vector Machine 
   - Random Forest
   - Logistic Reggresion
4. **Evaluation Metrics**:
   - Accuracy
   - Confusion Matrix
   - Cross-Validation (5-fold, Stratified)

## Results

- SVM performed best in multi-class classification using One-vs-One.
- IR score proved helpful in identifying borderline cases that traditional grading missed.

## Technologies

- Python 3
- pandas, NumPy
- scikit-learn
- matplotlib, seaborn
- Jupyter Notebooks
- 
