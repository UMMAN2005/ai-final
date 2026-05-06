### 📊 Classification Fundamentals: Final Exam Master Summary

**1. The Core Definition and Decision Trees**
* **Classification:** A supervised learning task where the goal is to find a descriptive profile of a class to assign unlabeled data objects to the appropriate category.
* **Decision Trees:** Build rules by drawing straight, axis-parallel boundaries. 
    * **Pros:** Fast and highly interpretable (you can easily read the rules). 
    * **Cons:** Prone to overfitting and struggle with diagonal (oblique) relationships.

**2. Random Forests and Ensemble Learning**
A Random Forest combines multiple decision trees to create a highly accurate, robust "wisdom of the crowd" prediction.
* **Bagging (Bootstrap Aggregating):** Creating multiple datasets by sampling the original training data *with replacement*. 
    * Statistically, each bootstrap sample contains $\approx 63\%$ unique instances, leaving $\approx 37\%$ as Out-of-Bag (OOB) samples for validation.
* **Feature Bagging:** At each split in the tree, the algorithm only looks at a random subset of $m$ features out of the total $p$ features. For classification, typically $m = \sqrt{p}$.
* **Result:** This completely decorrelates the trees, reducing variance and improving stability, though it sacrifices the interpretability of a single tree.

**3. k-Nearest Neighbors (k-NN)**
Classifies a new data point by looking at the majority vote of its $k$ closest labeled neighbors.
* **Lazy Learning:** k-NN builds no explicit model during training (zero training time). All the heavy mathematical lifting is deferred until prediction time, making classifications slow.
* **Distance Metric:** Typically relies on Euclidean distance. Because it calculates physical distance, you *must* normalize or scale your features beforehand.
* **Choosing $k$:** A small $k$ ($k=1$) is too sensitive to noise (overfitting). A very large $k$ blurs class boundaries. A common rule of thumb is $k = \sqrt{n}$ (where $n$ is total data points).

**4. Naïve Bayes Classification**
Uses probability to guess the class based on prior historical knowledge and new evidence.
* **Mathematical Operation (Bayes Theorem):** $P(C|X) = \frac{P(X|C) \cdot P(C)}{P(X)}$
    * $P(C)$: **Prior Probability** (Baseline chance of the class).
    * $P(X|C)$: **Likelihood** (Chance of seeing these features if the class is true).
    * $P(C|X)$: **Posterior Probability** (The final updated prediction).
* **The "Naïve" Assumption:** It assumes that all features are *conditionally independent* of each other. While rarely true in the real world, the model still performs surprisingly well.
* **The Zero-Frequency Problem:** If the model encounters a feature value it has never seen, it multiplies the entire probability by 0. This is fixed using **Laplace Smoothing**.

**5. Support Vector Machines (SVM)**
An algorithm designed to find the absolute safest, widest boundary between two groups.
* **The Goal:** Maximize the **margin** (the empty space) between the separating line (hyperplane) and the data.
* **Support Vectors:** The specific data points sitting closest to the boundary. These are the *only* points that dictate where the line is drawn.
* **The Kernel Trick:** When data is tangled and cannot be separated by a straight line, SVM applies a Kernel (like Polynomial or RBF/Gaussian) to map the data into a higher dimension where a flat hyperplane can easily slice them apart.

**6. Evaluation Metrics and Testing**
Never test a model on its training data. Use a **Confusion Matrix** to track True Positives (TP), True Negatives (TN), False Positives (FP), and False Negatives (FN).
* **Accuracy:** Overall correctness. *Warning:* Highly misleading if the data has class imbalance.
* **Precision:** $\frac{TP}{TP + FP}$. Out of all the positive *claims* the model made, how many were actually right?
* **Recall (TPR):** $\frac{TP}{TP + FN}$. Out of all the *actual* positives in the world, how many did the model catch?
* **F1-Score:** The harmonic mean that balances Precision and Recall. Essential for imbalanced datasets.
* **Cross-Validation:** Splitting the dataset into $k$ equal folds and rotating which fold is used for the practice test, ensuring the model generalizes well.
* **ROC Curve & AUC:** The ROC plots the True Positive Rate vs. False Positive Rate across different threshold "dial settings." The **AUC (Area Under the Curve)** scores the whole graph (1.0 is perfect, 0.5 is random guessing).

---

### ✅ Exam Procedure Checklist

* **If asked which algorithm is highly interpretable:** Choose **Decision Trees**.
* **If asked about the weakness of Naïve Bayes:** Mention the **independence assumption** and the **zero-frequency problem** (fixed by Laplace smoothing).
* **If asked how SVM handles non-linear data:** State that it uses the **Kernel Trick** to project data into higher dimensions.
* **If asked why accuracy is a bad metric:** Explain that it fails on **imbalanced datasets** (e.g., 99 normal, 1 fraud), and suggest **F1-Score** or **AUC** instead.
* **If asked to define Bagging:** Remember it involves sampling *with replacement* to train multiple parallel models.
