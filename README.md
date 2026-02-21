# CS5760 – Natural Language Processing  
## Homework 2

**University:** University of Central Missouri  
**Department:** Computer Science & Cybersecurity  
**Course:** CS5760 – Natural Language Processing  
**Semester:** Spring 2026  
**Student Name:** Guntur Murali Lakshmi Prasanna  

---

## 📌 Overview

This repository contains the complete solutions for Homework 2 in Natural Language Processing.  
The assignment includes both theoretical explanations and programming implementations.

### Topics Covered:
- Document Classification using Probabilistic Models
- Harms in NLP Classification Systems
- Bigram Language Models
- Zero-Probability Problem & Laplace Smoothing
- Backoff Models
- Evaluation Metrics (Macro vs Micro Averaging)
- Python Implementation of Bigram Model

---

# 📖 Part I – Written Solutions

## Q1 – Document Classification

- Computed probability scores for the document:
- - Used smoothed likelihoods and priors.
- Compared Positive vs Negative class probabilities.
- Final Decision: **Negative Class** (higher probability score).

---

## Q2 – Harms of Classification

### 1. Representational Harm
- Explained how sentiment systems may encode bias.
- Discussed findings from Kiritchenko & Mohammad (2018).
- Systems assigned more negative sentiment to sentences containing African American names.

### 2. Risk of Toxicity Classification
- Toxicity systems may incorrectly flag identity terms (e.g., “gay”, “blind”).
- Risk: Censorship and silencing of marginalized communities.

### 3. Performance Disparity
- Classifiers perform worse on African American English (AAE) and Indian English.
- Cause: Training data imbalance.
- Impact: Misclassification and reduced confidence.

---

## Q3 – Bigram Probabilities & Zero-Probability Problem

### Bigram Sentence Probabilities (MLE)

Compared:
S1: <s> I love NLP </s>
S2: <s> I love deep learning </s>

Results:
- P(S1) = 1/3 = 0.333
- P(S2) = 1/6 = 0.167

Model Preference: **Sentence S1**

Reason: S2 includes an additional probability multiplication that lowers the final score.

---

### Zero-Probability Problem

Using MLE:
P(noodle | ate) = 0

Problem:
- Any sentence containing this bigram gets probability 0.
- Perplexity becomes infinite.
- The model treats unseen events as impossible.

### Laplace (Add-1) Smoothing

Using:
- Count(ate) = 12
- Vocabulary size = 10
P(noodle | ate) = (0 + 1) / (12 + 10) = 1 / 22 ≈ 0.0455

Smoothing assigns a small non-zero probability and prevents model failure.

---

## Q4 – Backoff Model

Training Corpus:
<s> I like cats </s>
<s> I like dogs </s>
<s> You like cats </s>

Results:
- P(cats | I, like) = 1/2
- P(dogs | You, like) = 1/3 (using trigram → bigram backoff)

Why Backoff is Necessary:
- Prevents zero probability for unseen trigrams.
- Uses lower-order n-grams to generalize better.
- Improves robustness of the language model.

---

## Q5 – Evaluation Metrics (Multi-Class Confusion Matrix)

### Per-Class Metrics

| Class  | Precision | Recall |
|--------|----------|--------|
| Cat    | 0.25     | 0.25   |
| Dog    | 0.444    | 0.444  |
| Rabbit | 0.40     | 0.40   |

---

### Macro-Averaged Metrics
- Precision ≈ 0.365  
- Recall ≈ 0.365  

Macro averaging treats all classes equally.

---

### Micro-Averaged Metrics
- Precision ≈ 0.389  
- Recall ≈ 0.389  

Micro averaging reflects overall system performance.

---

# 💻 Part II – Programming Implementation

## Bigram Language Model

### Training Corpus
<s> I love NLP </s>
<s> I love deep learning </s>
<s> deep learning is fun </s>

### Program Features
- Computes unigram counts
- Computes bigram counts
- Estimates bigram probabilities using MLE
- Calculates probability of any input sentence
- Compares sentence probabilities
- Prints the preferred sentence with explanation

### Tested Sentences
<s> I love NLP </s>
<s> I love deep learning </s>


The program outputs probability values and identifies the more probable sentence.

---

# 🛠 Technologies Used

- Python 3
- Dictionaries for frequency counts
- Basic probability calculations
- No external libraries required
