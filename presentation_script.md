# ScrollMood — Presentation Script

---

## Opening

"Hi everyone! So our project is called **ScrollMood**.

The idea is simple — can we tell how happy a student is just by looking at how they use social media? We surveyed **166 students** and built a model that guesses if they're **High, Medium, or Low** satisfaction. Let's get into it."

---

## Step 1 — Import Libraries

"First we just bring in all the tools we need. pandas for data, scikit-learn for the model, matplotlib for charts. Nothing fancy, just setting things up."

---

## Step 2 — Load Dataset

"We load the data straight from **Google Sheets** — no downloading, just a link. Then we shorten all the column names because the original ones were way too long. We also delete email and timestamp since we don't need them.

End result — **166 students, 19 columns**."

---

## Step 3 — Missing Values

"We check if any cells are empty. If a number column is missing we fill it with the **median**, if a text column is missing we use the **most common answer**.

Turned out everything was already filled — no missing values at all."

---

## Step 4 — Duplicates & Outliers

"We check for duplicate rows — didn't find any. Then we use **IQR** to catch scores that are way too extreme to be normal. Didn't find any of those either.

So all 166 students stayed."

---

## Step 5 — Create the Target

"This is the most important step — we define what we want to predict.

We average 4 satisfaction scores per student, then label them:
- **High** → 7–10
- **Medium** → 4–6  
- **Low** → 1–3

Most students (113) ended up as Medium, which becomes a problem later."

---

## Step 6 — Encode Text to Numbers

"The model can't read words like 'Always' or 'Gaming' — it only gets numbers.

So we convert everything. Ordered answers like Never/Rarely/Always become 1/2/3/4/5. For content type, we make separate columns — one per category, with 0 or 1."

---

## Step 7 — Normalize

"Different features have different ranges, so we scale everything to **0.0–1.0**. That way no feature has an unfair advantage just for being a bigger number."

---

## Step 8 — Split the Data

"We split into **70% for training** and **30% for testing**. The model learns from the first group and gets tested on the second — data it's never seen before."

---

## Step 9 — Train the Model

"We use **Random Forest** — basically 100 decision trees that each make a guess, then we go with the majority vote. It's more reliable than just one tree and doesn't overfit as easily."

---

## Step 10 — Results

"**Accuracy: 72%** — got 36 out of 50 right.

But breaking it down:
- **Medium** — almost perfect, 97% recall
- **High** — only got 27% right
- **Low** — got 0% right

Why? Because most of the data was Medium, so the model just kept guessing that. This is the **class imbalance problem**."

---

## Step 11–12 — Confusion Matrix & Feature Importance

"The confusion matrix shows it visually — most mistakes were High or Low students getting called Medium.

And the top features that actually mattered? **sm_impact**, **stress_after**, and **self_comparison** — basically how social media makes students feel."

---

## Closing

"So that's ScrollMood — we predict student satisfaction from social media habits and got **72% accuracy**.

The main issue is the model struggles with High and Low because there just weren't enough of them in the data. If we had more responses or used class balancing techniques it'd probably do better.

Thanks for listening!"
