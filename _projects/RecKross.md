---
layout: page
title: RecKross
description: with background image
img: assets/img/recKross.png
importance: 1
category: work
related_publications: true
---


# RecKross: A Novel Recommender System with k-Cross Kernel Net

**Authors:** Abhishrut Vaidya, Niladri Chatterjee[1]

---

## Summary

This paper introduces **RecKross**, a novel collaborative filtering model designed for personalized recommendations, particularly in data-constrained environments[1]. It conceptualizes the recommendation task as a matrix completion problem, proposing a new architecture that combines a **2D Kernel layer** for multi-dimensional feature extraction and a **k-Cross Kernel layer** to improve collaborative filtering[1]. The model achieves state-of-the-art (SOTA) performance on benchmark datasets like MovieLens and Douban, demonstrating significant improvements in training speed and effectiveness in handling the **cold start problem** without needing any extra side information[1].

---

## Key Innovations

### 2D Kernel Layer
An extension of standard kernelized networks, this layer adds an extra dimension to capture more complex, non-linear relationships and multi-dimensional latent features from the user-item interaction matrix[1]. It uses reparameterization (the "kernel trick") to sparsify network weights, which reduces the model's complexity and improves training efficiency[1].

### k-Cross Kernel Layer
This layer is specifically designed to enhance collaborative filtering by identifying similarities between users and items. It uses two distinct kernels—a **horizontal kernel** and a **vertical kernel**—that are convoluted across the user-item matrix[1].
- The **horizontal kernel** captures item correlations among different users.
- The **vertical kernel** captures user correlations across different items[1].

---

## How It Works: Model Architecture

RecKross employs an AutoEncoder-like structure that processes a user-item rating matrix. The optimal configuration found during experiments is a three-layer network[1]:
1.  **Input Layer:** A **2D Kernel layer** processes the initial user-item interaction matrix.
2.  **Hidden Layer:** A **k-Cross Kernel layer** performs the core collaborative filtering task and captures neighbor information efficiently.
3.  **Output Layer:** A final **2D Kernel layer** reconstructs the rating matrix, predicting the missing values[1].

---

## Key Advantages

-   **Superior Performance:** Outperforms previous state-of-the-art models on the ML-1M and ML-100K datasets in terms of Root Mean Squared Error (RMSE)[1].
-   **High Efficiency:** Trains significantly faster than competing models like GLocal-K. For instance, on the ML-1M dataset, RecKross took approximately 3,032 seconds to train, compared to GLocal-K's 7,880 seconds on the same hardware[1].
-   **Cold Start Effectiveness:** Demonstrates better performance than strong baselines in highly sparse data settings, making it highly effective for new users and items with limited interaction data[1].
-   **No Side Information Required:** Achieves top results using only the user-item interaction matrix, without needing additional data like user demographics or item attributes[1].

---

## Performance Highlights

RecKross was evaluated against several baseline models on three datasets. It achieved the lowest RMSE (lower is better) on the MovieLens-1M dataset, indicating its superior prediction accuracy[1].

| Model | ML-1M RMSE ↓ |
| :--- | :--- |
| I-AutoRec | 0.8310[1] |
| GC-MC | 0.8320[1] |
| SparseFC | 0.8240[1] |
| IntentRec | 0.8230[1] |
| GLocal-K | 0.8227[1] |
| **RecKross** | **0.8224**[1] |

The model also achieved the best performance on the ML-100K dataset with an RMSE of **0.8910** and was highly competitive on the Douban dataset[1].

