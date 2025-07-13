# 🎥 TikTok Claims Classification: End-to-End Data Science Project

Welcome to my end-to-end data science project, simulating a real-world scenario as part of the TikTok data team. The goal of this project was to build a machine learning model that classifies whether a video contains a **claim** or an **opinion**, helping TikTok prioritize content review more efficiently.

This project spans the complete data science workflow: from problem framing and proposal writing to exploratory data analysis, statistical testing, regression analysis, and final model building using advanced machine learning techniques.

---

## 🧠 Project Context

At TikTok, users can report videos and comments they believe contain **claims**—statements that might need verification. This creates a high volume of reports, making manual moderation challenging.

To streamline moderation, TikTok tasked its data team with building a model that predicts whether a video is a **claim** or an **opinion**, using video metadata and user engagement features.

---

## 🧱 Project Structure

This project was structured in **6 phases**, each designed to reflect real data team milestones:

| Phase | Description |
|-------|-------------|
| ✅ 1. [Project Proposal](#1-project-proposal) | Planning, stakeholders, and workflow setup |
| ✅ 2. [Data Understanding](#2-data-understanding) | Initial data exploration, structure, and Investigating variables |
| ✅ 3. [Exploratory Data Analysis (EDA)](#3-exploratory-data-analysis) | Visual insights and engagement trends |
| ✅ 4. [Statistical Testing](#4-statistical-testing) | Hypothesis testing between account verification and views |
| ✅ 5. [Regression Analysis](#5-regression-analysis) | Modeling `verified_status` to understand user behavior |
| ✅ 6. [ML Modeling & Evaluation](#6-machine-learning-models) | Final claim classification using Random Forest & XGBoost |

---

## 📂 Data Summary

- **Rows:** 19,383
- **Columns:** 12
- **Target Variable:** `claim_status` — "claim" or "opinion"
- **Additional Target:** `verified_status` — for user behavior modeling

### 📘 Data Dictionary Highlights:
| Column | Description |
|--------|-------------|
| `video_duration_sec` | Length of the video |
| `video_view_count` | Total views |
| `video_like_count` | Total likes |
| `video_comment_count` | Total comments |
| `video_share_count`, `video_download_count` | Sharing metrics |
| `verified_status` | Whether the author is verified |
| `author_ban_status` | Author account status |
| `video_transcription_text` | Text transcription of the video |
| `claim_status` | Target variable — "claim" or "opinion" |

📌 _Note: The dataset is synthetically generated in partnership with TikTok._

---

## 🔍 1. Project Proposal

In the first phase, I created a **project proposal** outlining:

- Goals
- Milestones
- Stakeholders
- The PACE (Plan, Analyze, Construct, Execute) framework

📄 <a href = "([./1_project_proposal/project_proposal.md](https://github.com/divyakadava61/TikTok-Claims-Classification/blob/main/TikTok-project-proposal.pdf))"> "Project Proposal" </a>

---

## 📊 2. Data Understanding

### Key Insights:

- Data is balanced between claims (9,608) and opinions (9,476)
- The mean and median view count show the impact of each category of video (claim or opinion)
- Identified two important variable to consider, video duration (in seconds), video view count for future prediction models.
  

<img width="321" height="448" alt="image" src="https://github.com/user-attachments/assets/f58595dc-bcb8-4669-9441-11e09a350659" />

The mean and median view counts of each category of video (claim or opinion)

<img width="370" height="183" alt="image" src="https://github.com/user-attachments/assets/1fc3e057-c7bc-46a0-9bf4-efa99092bead" />

<a href ="https://github.com/divyakadava61/TikTok-Claims-Classification/blob/main/Activity_Course%202%20TikTok%20project%20lab.ipynb"> "Understanding dataset using python Jupyter Notebook File" </a>


📄<a href = "([./2_data_understanding/milestone2_summary.md](https://github.com/divyakadava61/TikTok-Claims-Classification/blob/main/executiveSummaryCourse2.pdf))"> "Executive Summary of dataset understanding" </a>

---

## 📈 3. Exploratory Data Analysis

EDA focused on how engagement metrics (views, likes, comments, shares) relate to `claim_status`.

### Key Insights:
- Most videos have **very low engagement** (<100k views, <100 likes)
- Strong **right-skew** across engagement variables
- Opinions are **only posted by active users**

📷 **Include:**
- Histograms of views, likes, comments  
- Boxplots comparing claims vs. opinions  
- Tableau Dashboard 📊:  
  🔗 [Link to Dashboard - Viewer Engagement by Content Type](#)  
  🔗 [Link to Boxplot Visuals in Tableau](#)

📄 [EDA Summary (Milestone 3)](./3_exploratory_data_analysis/milestone3_summary.md)

---

## 📏 4. Statistical Testing

We ran a **two-sample hypothesis test** to evaluate if `verified_status` affects `video_view_count`.

### Findings:
- Unverified accounts have **significantly higher average views**
- The mean difference was **statistically significant**
- Suggests potential differences in posting behavior or manipulation

📈 Include:
- Distribution plots of `video_view_count` by `verified_status`
- Table comparing mean & standard deviation
- Results of t-test with confidence interval

📄 [View Hypothesis Test Results](./4_statistical_testing/milestone4_summary.md)

---

## 📉 5. Regression Analysis

We used a **logistic regression model** to predict whether an account is verified based on video features.

### Model Performance:
- **Precision:** 67%
- **Recall:** 65%
- **F1-score:** 64%

### Key Insight:
- Longer videos tend to be associated with **verified accounts**
- Other features had limited predictive value

📷 Include:
- Confusion matrix for logistic regression ![logistic-confusion](./5_regression_model/confusion_matrix_lr.png)
- Bar plot of logistic regression coefficients

📄 [Regression Summary (Milestone 5)](./5_regression_model/milestone5_summary.md)

---

## 🤖 6. Machine Learning Models

We built and evaluated two classification models to predict `claim_status`:

- **Random Forest** ✅ *Final Model*
- **XGBoost**

### Final Results (Test Set):
- **Random Forest Accuracy:** 99.8%
- **Recall:** 0.995
- **Misclassifications:** Only 5 out of 3,817
- Top features: `video_view_count`, `video_like_count`, `share_count`, `download_count`

📷 Include:
- Confusion matrix for final model ![rf-confusion](./6_ml_modeling/rf_confusion_matrix.png)
- Feature importance plot (Random Forest)
- Performance metrics table

📄 [Final Model Summary (Milestone 6)](./6_ml_modeling/milestone6_summary.md)

---

## 🧪 Model Deployment Recommendations

- Monitor engagement metrics over time for data drift
- Re-train model periodically to adapt to changes
- Consider adding **NLP analysis** on `video_transcription_text` for richer context

---

## ✅ Future Improvements

- Add natural language processing (NLP) to analyze speech/text from video
- Tune hyperparameters using grid search / cross-validation
- Deploy model using a Flask app or on OCI Data Science Platform

---

## 🧰 Tech Stack

| Category       | Tools Used |
|----------------|-------------|
| Languages      | Python (Pandas, NumPy, SciPy, Sklearn) |
| ML Models      | Logistic Regression, Random Forest, XGBoost |
| Visualization  | Tableau, Matplotlib, Seaborn |
| Reporting      | Markdown, Jupyter, Tableau Dashboards |

---

## 🧭 Repo Navigation Guide

| Folder | Description |
|--------|-------------|
| `/1_project_proposal/` | Project proposal and stakeholder planning |
| `/2_data_understanding/` | Data schema, summary statistics |
| `/3_exploratory_data_analysis/` | Python & Tableau visualizations |
| `/4_statistical_testing/` | Hypothesis test notebooks |
| `/5_regression_model/` | Logistic regression model and results |
| `/6_ml_modeling/` | Final machine learning models and test results |

---

## 🚀 Getting Started

To run this project locally:

```bash
git clone https://github.com/yourusername/tiktok-claims-classification.git
cd tiktok-claims-classification
pip install -r requirements.txt
jupyter notebook

