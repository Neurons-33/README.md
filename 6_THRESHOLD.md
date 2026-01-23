# 6.Threshold Scanning to Expose Boundary-Level Uncertainty

### Threshold-Based Decision Risk Analysis

Based on the findings from the previous **confusion matrix analysis**, we observe that boundary-level errors and discrete outcome fluctuations can emerge even when overall model confidence appears stable.

To better address this behavior, this section explores the use of **decision thresholds** 
as a **mechanism** for risk-aware decision analysis, rather than treating the default threshold as a fixed rule.

Before conducting threshold-based experiments, two prerequisite checks are required to ensure that the observed behavior is meaningful and consistent with the model’s design assumptions.

---

## 1. Probability-Level Validation (Activation Consistency)

<img width="800" height="400" alt="threshold_probability" src="https://github.com/user-attachments/assets/ce090339-aca9-4f3d-a725-6ab3080652fe" />


The predicted probabilities are first examined to verify whether the model’s outputs are consistent with the expected behavior of the **sigmoid activation function**.

This step serves as a sanity check to ensure that:

- predictions are properly mapped into the [0,1] interval
- probability mass is not systematically biased or collapsed
- the activation behaves as intended under the current data and training conditions

From the probability distribution, we observe that predictions are predominantly concentrated near 0 and 1, which is consistent with the expected sigmoid behavior.

This indicates that no apparent inconsistency exists between the activation function and the model’s learned representations.

---

## 2. Logit-Level Stance Strength Analysis

<img width="800" height="400" alt="threshold_logit" src="https://github.com/user-attachments/assets/f2979565-55eb-46b8-b544-8cdc3f66d68b" />


Next, we analyze the **logit distributions** to inspect the model’s internal stance toward the **positive** and **negative** classes.

Since the model is trained under a **binary classification** setting, logits can be interpreted as a one-dimensional spectrum representing directional confidence:

<img width="1408" height="736" alt="threshold_2" src="https://github.com/user-attachments/assets/13967ada-fc62-47fd-80b1-f11aaebc84c3" />


- positive values indicate support for the positive class
- negative values indicate support for the negative class
- values near zero correspond to boundary-level uncertainty

The logit distribution reveals that, around the default threshold corresponding to logit = 0 (i.e., threshold = 0.5), the model exhibits a relatively ambiguous stance for certain positive samples.

This overlap near the decision boundary suggests the presence of potential **risk signals**, where small perturbations (e.g., data sampling or threshold choice) could lead to decision instability.

---

## 3. Threshold Scanning with Confusion Matrix Cross-Analysis

### Confusion matrix (noise = 0.2)

<img width="1064" height="70" alt="threshold_confusion_matrix" src="https://github.com/user-attachments/assets/b19cf6f1-88c8-4826-b156-45578c4637da" />


Finally, we perform a **threshold scanning experiment**, systematically varying the decision threshold and evaluating the resulting predictions using the confusion matrix.

By cross-referencing threshold values with changes in precision, recall, and error types (FP / FN), we are able to:

- identify how boundary samples are reassigned as the decision boundary shifts
- observe asymmetric risk behavior between positive and negative classes
- extract threshold ranges that offer a more stable trade-off between recall and false negatives

<img width="260" height="324" alt="threshold_scan" src="https://github.com/user-attachments/assets/d2b834cd-2c26-4304-8d3f-f2ce19cae517" />


## Conclusion

Through this process, the threshold is no longer treated as a fixed constant, but as a **decision control parameter** that reflects different risk preferences under the same learned model.

These observations describe controllable post-training decision behavior and do not imply that any specific threshold constitutes an optimal or theoretically justified risk solution.
