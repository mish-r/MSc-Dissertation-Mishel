# Computational Text Analysis of Genuine, Retracted and AI-Generated Scientific Papers

## Project Overview

- Investigates **computational text-analysis and creativity-related measures** that can distinguish between **Genuine, Retracted and AI-generated scientific papers** in the **AI-for-healthcare** domain.

The dataset contains **60 papers**:

- 20 Genuine
- 20 Retracted
- 20 AI-generated

AI-generated papers were produced using **Stanford STORM** and **Google Gemini 2.5**.

## Methodology

The framework uses a combination of:

- **Structural features** – word count, sentence count, paragraph count, figures, tables and equations
- **Stylometric features** – vocabulary, Type-Token Ratio, lexical diversity, word length, punctuation and POS frequencies
- **Readability measures** – Flesch Reading Ease, Flesch-Kincaid, Gunning Fog and SMOG
- **Entropy measures** – character, word and lexical entropy
- **Perplexity** – GPT-2 language-model perplexity
- **Novelty** – local and global novelty using sentence embeddings and cosine similarity
- **Coherence** – adjacent sentence similarity
- **Creativity Index** – aggregated score based on the extracted numerical features

The resulting features were analysed using **statistical testing, PCA, t-SNE, UMAP, K-Means, hierarchical clustering and supervised machine learning**.

## Key Findings

- **AI-generated papers** were generally shorter (**4,817 words**), used longer sentences (**30.1 words**) and had lower readability (**Flesch 7.29**).
- AI-generated papers also recorded higher GPT-2 perplexity (**47.99**) and lower novelty and Creativity Index scores.
- **Genuine papers** were longer (**10,595 words**) and showed greater vocabulary diversity and novelty.
- **Retracted papers** were more similar to Genuine papers, averaging **9,910 words** and a Creativity Index of **430.62**.
- AI-generated papers were **significantly different from the human-authored papers across most features**, while Genuine and Retracted papers showed only minor differences.
- Unsupervised analysis showed that AI-generated papers formed **two distinct clusters**, while Genuine and Retracted papers largely overlapped.

## Feature Importance

The most influential features included:

| Feature | Importance |
|---|---:|
| Global Novelty | 0.159 |
| Adjective Frequency | 0.113 |
| Sentence Count | 0.073 |
| Local Novelty | 0.063 |
| SMOG Index | 0.063 |
| Gunning Fog Index | 0.051 |

**Global Novelty** was the most important feature, while the **Creativity Index** had the lowest importance (**0.003**).

## Machine Learning Results

A stratified **70/30 train-test split** was used, giving a test set of 18 papers: six Genuine, six Retracted and six AI-generated. Stratified K-Fold cross-validation was also used during training.

| Model | Accuracy | Precision | Recall | F1-Score | ROC AUC |
|---|---:|---:|---:|---:|---:|
| Logistic Regression | 94.44% | 95.24% | 94.44% | 94.41% | 1.0000 |
| Random Forest | 100.00% | 100.00% | 100.00% | 100.00% | 1.0000 |
| SVM | 100.00% | 100.00% | 100.00% | 100.00% | 1.0000 |
| XGBoost | 88.89% | 89.68% | 88.89% | 88.85% | 0.9954 |

**Random Forest and SVM achieved 100% performance** across the evaluated metrics.

## External Validation

An unseen MDPI paper, *Deep Neural Network Regression to Assist Non-Invasive Diagnosis of Portal Hypertension* by **Baldisseri et al. (2023)**, was used for external validation.

The paper was correctly classified as **Genuine**:

- Genuine: **81.00%**
- Retracted: **17.00%**
- AI-generated: **2.00%**

The paper contained **5,099 words**, **1,959 unique words** and a **Global Novelty score of 0.7430**.

## Conclusion

The results indicate that **NLP, stylometric analysis, creativity-related measures and machine learning** can provide useful evidence for distinguishing between **Genuine, Retracted and AI-generated scientific papers**.

The strongest separation was observed between **AI-generated and human-authored papers**, while Genuine and Retracted papers showed greater overlap.
