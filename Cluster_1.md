### 1. Distance Metrics (Point-to-Point)
These formulas calculate the physical space between two individual data points, $A(x_A, y_A)$ and $B(x_B, y_B)$.

* **Euclidean Distance**
    * **Formula:** $$D(A, B) = \sqrt{(x_A - x_B)^2 + (y_A - y_B)^2}$$
    * **What it is:** The "straight-line" or "bird's-eye" distance. The most common default metric.
    * **Exam Tip:** Watch out for negative numbers when subtracting coordinates; squaring them will always make them positive.
* **Manhattan Distance (City Block/L1 Norm)**
    * **Formula:** $$D(A, B) = |x_A - x_B| + |y_A - y_B|$$
    * **What it is:** The distance if you could only travel along gridlines (like city blocks). 
    * **Exam Tip:** Absolute value bars $|x|$ mean you drop any negative signs.

---

### 2. Distance $\leftrightarrow$ Similarity Conversions
Distance measures how *far* apart things are (0 means identical). Similarity measures how *alike* things are (1 or 100% means identical). 

* **Distance to Similarity**
    * **Formula:** $$Similarity = \frac{1}{1 + Distance}$$
    * **How it works:** If Distance = 0, Similarity = 1. As Distance gets infinitely large, Similarity approaches 0.
* **Similarity to Distance (Inverse Formula)**
    * **Formula:** $$Distance = \frac{1}{Similarity} - 1$$
    * **How it works:** Use this to reverse-engineer the exact distance if an exam gives you a similarity score based on the above standard metric.
* **Similarity to Distance (Linear $[0,1]$ Scale)**
    * **Formula:** $$Distance = 1 - Similarity$$
    * **How it works:** Use this simple subtraction *only* if the similarity metric used is strictly bounded between 0 and 1 (like normalized Cosine Similarity or Correlation).

---

### 3. Linkage Metrics (Cluster-to-Cluster)
Once you merge points into clusters ($C_1$ and $C_2$), you must define the distance between those new groups.

* **MIN (Single Linkage)**
    * **Formula:** $$D_{MIN}(C_1, C_2) = \min(D(a, b)) \quad \text{for } a \in C_1, b \in C_2$$
    * **What it is:** The shortest possible distance between any point in Cluster 1 and any point in Cluster 2.
    * **Behavior:** Tends to create long, chain-like clusters (chaining effect).
* **MAX (Complete Linkage)**
    * **Formula:** $$D_{MAX}(C_1, C_2) = \max(D(a, b)) \quad \text{for } a \in C_1, b \in C_2$$
    * **What it is:** The longest possible distance between any point in Cluster 1 and any point in Cluster 2.
    * **Behavior:** Tends to create tightly bound, compact, and spherical clusters.
* **Centroid Linkage**
    * **Formula:** $$D_{Centroid}(C_1, C_2) = D(\bar{c}_1, \bar{c}_2)$$
    * **What it is:** The distance between the exact center point (centroid) of Cluster 1 and the center point of Cluster 2.
    * **How to find the Centroid:** Calculate the average of all $x$-coordinates and the average of all $y$-coordinates in that cluster.
        $$Centroid = \left( \frac{\sum x_i}{n}, \frac{\sum y_i}{n} \right)$$
    * **Exam Tip:** You must calculate the new center of gravity for the cluster *before* you calculate the distance to other clusters.
