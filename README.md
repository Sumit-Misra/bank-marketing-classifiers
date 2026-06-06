# Comparing Classifiers — Bank Telemarketing

Module 17, Required Assignment 17.1.

I compared four classifiers (KNN, Logistic Regression, Decision Tree, SVM) on a Portuguese bank's phone-marketing data to predict whether a client subscribes to a term deposit. Only ~11% of people contacted actually subscribe, so the real question is who's worth calling.

**Notebook:** [prompt_III_solution.ipynb](prompt_III_solution.ipynb)

## Data
- UCI Bank Marketing dataset (`bank-additional-full.csv`), 41,188 contacts from 17 campaigns, 2008–2010.
- Trained on client-profile features only (age, job, marital, education, default, housing, loan). Dropped `duration` since it's only known after a call ends.

## What I found
- With default settings, none of the models beat the "just predict no" baseline of 88.7% accuracy — which is the trap: when one class is 89% of the data, accuracy is meaningless.
- Switching to ROC-AUC and balancing the classes fixed this. All four landed close (AUC ~0.63–0.66), so the tiebreaker is practicality.
- **Logistic Regression wins** for everyday use: nearly the best score, trains in under a second, and you can actually read what it's doing. SVM and KNN were 15–35x slower for no real gain.
- Students and retired clients subscribe well above average; blue-collar workers and people with existing loans subscribe below.

## Recommendations
- Add the campaign and economic features I left out (`poutcome`, `euribor3m`, etc.) — they should lift performance noticeably.
- Set the call threshold to match the budget instead of a flat 0.5 cutoff.
- Target the high-yield segments and re-contact past subscribers first.

## Files
```
README.md
prompt_III_solution.ipynb
data/bank-additional-full.csv
```
