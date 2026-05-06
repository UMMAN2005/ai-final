# 🧠 Deep Learning Fundamentals: Final Exam Master Summary

## 1. The Core Definition and Evolution
**Deep Learning (DL)** is a subset of Machine Learning consisting of computational models with multiple processing layers that learn representations of data with multiple levels of abstraction.

### Traditional ML vs. Deep Learning
* **Traditional ML:** Relies on **hand-crafted features** (e.g., HoG for gradients, SIFT for keypoints). Humans must engineer the rules the classifier uses.
* **Deep Learning:** Uses **trainable feature extractors** and classifiers. The model learns low-level, mid-level, and high-level features automatically from raw data.
* **The "Deep" Requirement:** A network is technically considered "deep" if it has **more than one stage of non-linear feature transformation**.


## 2. The Artificial Neuron (Perceptron)
The basic unit of a neural network mimics a decision-making process by weighing evidence.
* **Anatomy:**
    * **Inputs ($x$):** The raw data features.
    * **Weights ($w$):** Parameters that determine the importance of each input.
    * **Bias ($b$):** An additional trainable parameter that allows the model to shift the activation function.
* **Mathematical Operation:** $z = \sum (w_i \cdot x_i) + b$. The final output is $y = \sigma(z)$, where $\sigma$ is an activation function.

### Activation Functions (The Non-Linearity)
Activation functions allow the network to learn complex, non-linear boundaries.
* **Unit Step:** A binary "hard decision" (0 or 1). It is **not differentiable**, making it unsuitable for modern training.
* **Sigmoid:** Squeezes values into $(0,1)$. It is smooth but suffers from **saturation** (gradients become near-zero at extremes), which slows down learning.
* **Tanh:** Squeezes values into $(-1, 1)$. It is **zero-centered**, which helps training, but still saturates.
* **ReLU (Rectified Linear Unit):** $max(0, x)$. It is the **modern default** because it is computationally cheap, converges faster, and reduces saturation for positive values.
* **Leaky ReLU:** Fixes the "dying ReLU" problem (where neurons stay at 0) by allowing a tiny slope ($\alpha \approx 0.01$) for negative values.


## 3. Training: The Iterative Learning Process
Training is a loop aimed at minimizing the **Loss Function**, which measures the error between predictions ($y$) and true targets ($t$).

### The 4-Step Training Pipeline 
1.  **Forward Propagation:** Data passes through the layers to compute a prediction ($y' = W_3f(W_2f(W_1x+b_1)+b_2)+b_3$).
2.  **Compute Loss:** The error is calculated using a formula like Mean Squared Error: $L = \sum (y^{(i)} - t^{(i)})^2$.
3.  **Backpropagation:** The **Chain Rule** is used to propagate the error backward, calculating **Gradients** for every weight to see how much each contributed to the error.
4.  **Update Weights:** Parameters are updated using **Gradient Descent**: $w_{new} = w_{old} - \eta \cdot \text{gradient}$. $\eta$ is the **Learning Rate**.


## 4. Multi-Layer Perceptron (MLP) and Optimization
An MLP consists of an input layer, one or more hidden layers, and an output layer. It is **fully connected**, meaning every neuron in one layer links to every neuron in the next.

### Variants of Gradient Descent
* **Batch GD:** Updates weights only after seeing the **entire** dataset. It is accurate but very slow for large data.
* **Stochastic GD (SGD):** Updates weights after **every single sample**. It is fast but very unstable (high oscillations).
* **Mini-batch SGD:** The standard practice. It updates after a small batch of samples (e.g., 32 or 64). It is faster than Batch GD, more stable than SGD, and allows **GPU parallelization**.

### Advanced Optimizers
* **Momentum:** Accumulates "velocity" from past gradients to speed up learning and push through flat regions.
* **RMSProp:** Uses an adaptive learning rate for each parameter.
* **Adam:** Combines **Momentum and RMSProp**. It is the common default optimizer because it handles diverse data types effectively.

## 5. Overfitting and Regularization
**Overfitting** occurs when a model performs exceptionally well on training data but poorly on unseen test data.


### Regularization Solutions
* **L2 Regularization (Weight Decay):** Adds a penalty to the loss function based on the size of the weights ($L = L_{data} + \lambda \sum w_i^2$). This prevents the model from relying too heavily on any single feature.
* **Dropout:** Randomly ignores a subset of neurons (e.g., $p=0.5$) during training. This forces the network to learn **robust features** and prevents "co-adaptation" where neurons rely too much on each other.
* **Early Stopping:** Monitoring the validation error and stopping training as soon as it begins to worsen, even if the training error is still dropping.
* **Data Augmentation:** Artificially increasing the training set size (e.g., flipping or rotating images) to help the model generalize.

## Exam Procedure Checklist
* **If asked to explain "Deep":** Mention "more than one stage of non-linear feature transformation".
* **If asked for the training cycle:** List: Forward Pass $\rightarrow$ Loss $\rightarrow$ Backprop (Gradients) $\rightarrow$ Weight Update.
* **If asked how to fix overfitting:** Suggest Dropout, L2, Early Stopping, or Data Augmentation.
* **If asked about activation:** Recommend **ReLU** for hidden layers and explain it converges faster and is cheaper than Sigmoid.
