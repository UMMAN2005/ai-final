### Decision Trees & Impurity Metrics Cheat Sheet

Use this guide for quick recall on exams or during technical interviews.

#### 1. Core Principles
* **Goal:** Decision trees split data to maximize "purity" in the resulting child nodes. A pure node contains samples from only one class.
* **Rule of Thumb:** Lower Impurity = Higher Purity = Better Split.
* **Information Gain (IG):** The actual reduction in impurity. You want to *maximize* Information Gain. 
    * $$IG = Impurity(Parent) - Weighted\_Impurity(Children)$$

#### 2. Gini Impurity (CART Algorithm)
Measures the probability of incorrectly classifying a randomly chosen element if it were labeled randomly according to the distribution of labels in the node.

* **Node Formula:** $$GINI(t) = 1 - \sum_{j} [p(j|t)]^2$$
* **Split Formula:** Weighted average of child nodes. $$GINI_{split} = \sum_{i=1}^{k} \frac{n_i}{n} GINI(i)$$
* **Min/Max Values (Binary Classification):**
    * **Min:** 0.0 (Perfectly pure node)
    * **Max:** 0.5 (Perfectly mixed node, e.g., 50/50 split)
* **Pros:** Computationally faster because it doesn't require calculating logarithms.

#### 3. Entropy (ID3 / C4.5 Algorithms)
Measures the level of "disorder" or unpredictability in a node, based on Information Theory.

* **Node Formula:** $$Entropy(t) = -\sum_{j} p(j|t) \log_2 p(j|t)$$
* *(Exam Tip: If $p=0$, then $p \log_2 p$ is defined as 0 to avoid errors).*
* **Split Formula:** Weighted average of child nodes. $$Entropy_{split} = \sum_{i=1}^{k} \frac{n_i}{n} Entropy(i)$$
* **Min/Max Values (Binary Classification):**
    * **Min:** 0.0 (Perfectly pure node)
    * **Max:** 1.0 (Perfectly mixed node, e.g., 50/50 split)

#### 4. Gini vs. Entropy Quick Comparison

| Feature | Gini Impurity | Entropy |
| :--- | :--- | :--- |
| **Max Value (Binary)** | 0.5 | 1.0 |
| **Computation Speed** | Faster (Squares only) | Slower (Requires Logarithms) |
| **Tree Shape** | Tends to isolate the most frequent class in its own branch. | Tends to create more balanced, symmetrical trees. |
| **When to use?** | Default for standard classification (e.g., Scikit-Learn's default). | When balancing the tree structure is a priority. |
