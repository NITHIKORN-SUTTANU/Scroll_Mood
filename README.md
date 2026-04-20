# 📱 ScrollMood
### Predicting University Student Satisfaction Levels Through Social Media Behavior Analysis

Social media has become an inseparable part of university student life. From scrolling through TikTok and Instagram to comparing lifestyles and chasing trends, the way students interact with social media can deeply influence how they feel about themselves and their lives. ScrollMood is a university research project that investigates this relationship — using real survey data and Machine Learning to predict whether a student is happy, neutral, or unhappy based on their social media habits.

---

## 🧠 The Idea

The core question behind ScrollMood is simple: **can we predict how satisfied a student is with life just by looking at how they use social media?**

To answer this, we designed a bilingual survey (English and Thai) and distributed it to university students. The survey asked about daily screen time, the types of content they consume, how often they compare themselves to others online, whether social media disrupts their sleep, and how much pressure they feel to follow trends — among other habits. Students also rated their own happiness and life satisfaction on a scale of 1 to 10.

This data was then used to train a Machine Learning model that learns the patterns between social media behaviour and student wellbeing, and uses those patterns to make predictions on new data.

---

## 📋 The Survey

The survey was created using Google Forms and contains **19 questions** divided into 4 sections:

- **Section A — Demographics:** age, gender, and year of study
- **Section B — Social Media Habits:** daily screen time, platforms used, content type, posting frequency, self-comparison, and trend pressure
- **Section C — Lifestyle & Wellbeing:** sleep hours, whether social media affects sleep, face-to-face interaction frequency, stress after using social media, and social media break habits
- **Section D — Satisfaction & Happiness:** self-rated scores on social life, academic life, overall life satisfaction, daily happiness, and perceived impact of social media on happiness

A total of **166 university students** completed the survey, providing a diverse dataset of real responses.

---

## 🎯 What the Model Predicts

The target variable is **Satisfaction Level** — derived by averaging the four self-rated happiness scores from Section D. Students are classified into one of three categories:

- 😊 **High** (score 7–10) — the student feels happy and satisfied with their life
- 😐 **Medium** (score 4–6) — the student has mixed or moderate satisfaction
- 😟 **Low** (score 1–3) — the student feels unhappy or unsatisfied

Looking at the dataset, most students fell into the Medium category (113 students, 68%), followed by High (36 students, 22%) and Low (17 students, 10%). This reflects a realistic distribution where most students experience moderate wellbeing, with smaller groups at either extreme.

---

## 🔧 How the Data Was Processed

Raw survey responses cannot be fed directly into a Machine Learning model — they need to be cleaned and transformed first.

**Data Cleaning** involved two steps. 

First, any missing responses were filled in using the median value for numerical questions and the most common answer (mode) for multiple-choice questions, ensuring no gaps in the data. 

Second, duplicate submissions were removed, and statistical outliers in the satisfaction scores were identified and excluded using the IQR (Interquartile Range) method — a standard technique for detecting values that are unusually far from the rest of the data.

**Data Transformation** also involved two steps. 

First, all text-based answers were converted into numbers through encoding — ordinal answers like "Never / Rarely / Sometimes / Often / Always" were mapped to 1–5, while the content type question was expanded into separate binary columns using One-Hot Encoding. 

Second, all numerical features were scaled to a uniform range of 0.0 to 1.0 using Min-Max Normalization, so that no single feature unfairly dominates the model's learning process.

---

## 🤖 The Machine Learning Model

ScrollMood uses a **Random Forest Classifier** — one of the most reliable and widely used Machine Learning algorithms for classification tasks. A Random Forest works by building many individual decision trees, each trained on a slightly different version of the data, and then combining their predictions through majority voting. This approach is much more accurate and stable than relying on a single decision tree.

The model was trained on **70% of the data** (116 students) and tested on the remaining **30%** (50 students). It uses 100 decision trees with a maximum depth of 10 levels per tree.

The model achieved a final accuracy of **72%**, meaning it correctly predicted the satisfaction level of 72 out of every 100 students in the test set.

---

## 🔍 Key Findings

After training the model, feature importance scores revealed which social media habits had the strongest influence on predicting student satisfaction:

1. **Year of study** — older students tended to report different satisfaction patterns
2. **Perceived impact of social media on happiness** — students who felt social media negatively affected them scored lower overall
3. **Posting frequency** — how often students share content correlated with their wellbeing
4. **Trend pressure** — feeling pressured to follow trends was linked to lower satisfaction
5. **Social media breaks** — students who regularly took breaks from social media showed more positive outcomes

These findings suggest that it is not just the amount of time spent on social media, but the **quality and nature** of the interaction that most affects student wellbeing.

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| **Python** | Core programming language |
| **Jupyter Notebook** | Interactive development environment |
| **Google Forms** | Survey creation and data collection |
| **pandas** | Data loading and manipulation |
| **numpy** | Numerical computations |
| **scikit-learn** | Machine Learning model and preprocessing |
| **matplotlib & seaborn** | Data visualization and charts |

---

*ScrollMood v1.0 — University Machine Learning Project*
