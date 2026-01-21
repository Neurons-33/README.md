# **3.Control the data noise level to observe how noise affects the decision boundary during training.**

- Neurons flow through the activation function to introduce nonlinearity into the model.
- We keep the logits, as they help reduce prediction errors, then pass the data into the training function and return the model output.
- Compute the validation loss at this step to compare it with the training loss, and show the decision boundary.

---

## **Experiment Setup**

**Dataset**

- Source: `sklearn.datasets.make_moons`
- Number of samples: 1200
- Noise levels: 0.05, 0.20, 0.40
- Train / Validation split: 75% / 25%

**Feature Processing**

- StandardScaler (fit on full dataset)

**Model**

- MLP with 2 hidden layers
- Architecture: 2 → 32 → 32 → 1
- Activation: ReLU

**Training**

- Loss: BCEWithLogitsLoss
- Optimizer: Adam
- Learning rate: 1e-2
- Epochs: 1500

**Evaluation**

- Decision boundary visualization

---


<img width="1200" height="400" alt="noise" src="https://github.com/user-attachments/assets/197497b9-8f6e-429d-b2a8-dd0bb14be490" />


## **Observations**

### **Noise = 0.05 (Low noise)**

- The decision boundary is smooth and well-aligned with the true data geometry.
- The two moon-shaped clusters are clearly separable.
- Training converges quickly and stably.
- The learned boundary closely matches intuitive expectations.

---

### **Noise = 0.20 (Moderate noise)**

- The decision boundary becomes less smooth.
- Local fluctuations appear near overlapping regions.
- The global structure is still preserved, but uncertainty increases.
- Validation accuracy remains reasonable, but loss oscillation increases.

---

### **Noise = 0.40 (High noise)**

- The decision boundary becomes irregular and fragmented.
- The model struggles to identify a consistent global structure.
- Many samples lie near or across the boundary.
- The learned boundary reflects noise rather than underlying geometry.

---

## **Interpretation**

Noise directly affects the **geometric clarity** of the dataset.

As noise increases:

- The effective margin between classes shrinks.
- The decision boundary becomes increasingly sensitive to local variations.
- Model capacity is partially spent fitting noise instead of structure.

<img width="497" height="276" alt="noise_val_loss" src="https://github.com/user-attachments/assets/eb8bd5dc-7fe5-4b20-8ac9-15740b06af8d" />


This experiment shows that:

- Decision boundary visualization reveals information not captured by accuracy alone.
- Noise primarily degrades *geometric separability*, not just optimization.
- A stable boundary requires both sufficient model capacity and clean structure.

---

## **Key Takeaway**

> Noise does not merely add randomness it reshapes the geometry that the model is trying to learn.
> 

---

Understanding model behavior requires observing how noise alters the learned decision boundary, not just tracking scalar metrics.
