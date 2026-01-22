# 5.Confusion Matrix Analysis of Class-wise Error Distribution Under Label Imbalance

## Experiment Goal

This experiment investigates how **class imbalance in label `y`** affects:

- model training dynamics
- decision boundary behavior
- generalization under different class ratios

The objective is **not** to optimize accuracy, but to **analyze how errors are redistributed across classes under biased training conditions**.

To this end, **confusion matrix analysis is used as the primary observational tool** to examine whether prediction errors exhibit **systematic, class-dependent bias**, rather than random misclassification.


## Confusion Matrix as a Tool for Risk Interpretation

In this experiment, the **confusion matrix** is used not merely to report performance, how risk is distributed across classes under class imbalance.

By examining **precision**, **recall**, and the corresponding confusion matrix entries, we observe **which types of errors the model chooses to tolerate**, and how these choices reflect its inductive bias rather than raw accuracy.


## Class Imbalance and Geometric Consistency

Using a geometrically well-defined dataset (moons), label imbalance is introduced as a **controlled perturbation** to the risk structure.

The goal is not to correct imbalance, but to observe whether the model can still **recover the correct data geometry**, and how the decision boundary deforms when the cost of different errors becomes asymmetric.

When the resulting confusion matrix remains interpretable and geometrically consistent, it suggests that the **data structure and the model’s inductive bias are compatible**.


## Early Epochs and Initialization Effects

### lucky initialization

<img width="1184" height="348" alt="Imbalance_confusion_matrix" src="https://github.com/user-attachments/assets/acc5f294-16b3-447d-9219-8363dc71db9b" />

<img width="891" height="328" alt="Imbalance_confusion_matrix_val_loss" src="https://github.com/user-attachments/assets/822036f7-17ab-4d48-96be-b8fc863b4fd8" />


Confusion matrices at **epoch = 0** reveal whether the model starts from a configuration resembling **lucky initialization**, This observation is descriptive and does not imply that early alignment guarantees optimal or stable convergence.

These early conditions often influence the final solution, even after prolonged training, indicating that **early training dynamics can constrain long-term model behavior**.


## Random Seed as Exploration

### Change the seed

<img width="1182" height="346" alt="Imbalance_confusion_matrix_42" src="https://github.com/user-attachments/assets/5cc0d961-807c-471c-adfa-0623a062da7a" />

<img width="891" height="328" alt="Imbalance_confusion_matrix_val_loss_42" src="https://github.com/user-attachments/assets/7fc9b40d-8010-431d-9721-4077b984bb1e" />


Across experiments, different random seeds lead to qualitatively different outcomes.

In this context, **SEED functions as an exploration mechanism rather than a mere reproducibility setting**, exposing multiple inductive biases available to the same model under identical data conditions.

---

## Takeaway

This study highlights that under class imbalance:

- confusion matrices expose **model risk preferences**,
- early training dynamics shape final outcomes,
- and random initialization meaningfully affects which inductive bias is realized.

The focus is therefore on **model behavior and interpretability**, rather than metric optimization alone.
