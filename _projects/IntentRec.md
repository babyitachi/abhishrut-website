---
layout: page
title: IntentRec
description: with background image
img: assets/img/intentRec.png
importance: 1
category: work
related_publications: true
---

# IntentRec: An Advanced Recommender System Leveraging User-Item Intent

**Authors:** Abhishrut Vaidya, Niladri Chatterjee

---

## Summary

This paper introduces **IntentRec**, a novel recommender system that predicts user preferences by modeling the "intent" behind their rating patterns, rather than relying on explicit user or item descriptions[1]. The model is designed to be computationally efficient and robustly handle common challenges like **data sparsity** and the **cold start problem**[1]. Experimental results show that IntentRec achieves state-of-the-art (SOTA) performance on the Movielens-100K and Douban datasets without requiring any additional side information[1].

---

## Core Concept: User Intent

The central idea is that the *distribution* of ratings a user gives (e.g., the frequency of 1, 2, 3, 4, or 5-star ratings) represents their underlying **intent**[1]. Similarly, the pattern of ratings an item receives reflects its general characteristics. By analyzing and comparing these intent patterns, IntentRec identifies similar users and items to predict unknown ratings effectively[1].

---

## How It Works

IntentRec's architecture is built on an **Intent Layer** followed by a **kernelized AutoEncoder**. The process is as follows:

1.  **Calculate Initial Intent:** For each user and item, the model calculates a "prior-intent probability," which is a vector representing the distribution of their ratings[1].
2.  **Find Similar Neighbors:** It uses cosine similarity on these probability vectors to find the *k*-most similar users and items[1].
3.  **Extract Latent Features:** The Intent Layer uses a convoluted kernel to process information from these neighbors and extract latent features that represent the collaborative intent[1].
4.  **Reconstruct Ratings:** This refined output is passed to a kernelized AutoEncoder, which learns to reconstruct the full user-item rating matrix, effectively predicting the missing ratings[1].
5.  **Dynamic Updates:** During training, the model periodically updates the intent probabilities based on its performance, allowing it to dynamically refine its understanding of user and item similarities and handle the cold start problem[1].

---

## Key Advantages

-   **Reduced Complexity:** The model requires fewer parameters and a less complex architecture than many deep learning-based recommenders, leading to faster training[1].
-   **No Side Information:** It achieves SOTA results using only the user-item rating matrix, without needing external data like user demographics or item genres[1].
-   **Cold Start Mitigation:** By learning an initial probability distribution even for new users or items with few ratings, the model can infer similarities and provide better initial recommendations[1].

---

## Performance Highlights

IntentRec was evaluated against several strong baselines on three benchmark datasets. It achieved superior or highly competitive performance, as measured by Root Mean Square Error (RMSE), where a lower score is better[1].

| Dataset | IntentRec RMSE | Best Baseline RMSE | Model |
| :--- | :--- | :--- | :--- |
| **ML-100K** | **0.8868** | 0.8900 | MG-GAT+Extra |
| **ML-1M** | 0.8230 | **0.8227** | GLocal-K |
| **Douban** | **0.7208** | 0.7210 | IGMC |

The results demonstrate that IntentRec outperforms existing models on datasets with varying levels of sparsity, particularly on the highly sparse Douban dataset and the medium-density ML-100K dataset[1].

