## A Structured Way to Observe Decision Boundary Behavior

This chapter defines the analytical axes I use to interpret model behavior
through decision boundary visualization.
Rather than treating accuracy as the primary signal,
the focus is on how a model *behaves* under controlled perturbations.

The following dimensions are not independent tricks,
but complementary lenses for diagnosing model dynamics.

---

### 1. Capacity — How Much Can the Model Represent?

**Question:**  
Does the model have sufficient but not excessive capacity for the data geometry?

**Observation Focus:**
- Whether the tensor shape and hidden dimension are appropriate.
- Whether increased depth actually improves the decision boundary.

**Key Insight:**  
More capacity does not guarantee better structure.
Excess capacity often amplifies noise rather than improving geometry.

---

### 2. Activation — Can the Signal Propagate?

**Question:**  
Is nonlinearity effectively preserved across layers?

**Observation Focus:**
- Whether gradients flow without collapsing.
- Whether the decision boundary changes meaningfully across training.

**Key Insight:**  
Activation functions are not about expressiveness alone,
but about maintaining a viable signal path during optimization.

---

### 3. Noise — Exposing Inductive Bias

**Question:**  
How does the model behave when the data is no longer perfectly clean?

**Observation Focus:**
- Boundary smoothness under increasing data noise.
- Sensitivity to local perturbations.

**Key Insight:**  
Noise is intentionally introduced to expose a model’s inductive bias.
Perfectly clean data often hides structural assumptions.

---

### 4. Imbalance — Stress-Testing the Decision Surface

**Question:**  
How does class imbalance distort the learned boundary?

**Observation Focus:**
- Boundary shift toward majority classes.
- Divergence between training loss, validation loss, and accuracy.

**Key Insight:**  
Imbalance is not the target of optimization,
but a controlled stress test to reveal bias in decision making.

---

### 5. Confusion Matrix — Diagnosing Error Structure

**Question:**  
What kinds of errors does the model prefer to make?

**Observation Focus:**
- False positives vs. false negatives.
- Asymmetry between positive and negative classes.

**Key Insight:**  
Overall accuracy hides directional error tendencies.
The confusion matrix reveals how decisions fail, not just how often.

---

### 6. Threshold — Decision Logic Beyond the Model

**Question:**  
How does post-hoc thresholding alter risk behavior?

**Observation Focus:**
- Recall–precision trade-offs.
- Sensitivity of predictions near the decision boundary.

**Key Insight:**  
The threshold introduces conditional logic *after* representation learning.
It is a decision policy, not a property of the model itself.

---

### Summary

These six axes form a diagnostic framework rather than a training recipe.
They are used repeatedly throughout subsequent experiments
to interpret how and why decision boundaries change.
