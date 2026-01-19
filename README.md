# Control the noise level to observe how noise affects the decision boundary during training.

- Neurons flow through the activation function to introduce nonlinearity into the model.

- We keep the logits, as they help reduce prediction errors, then pass the data into the training function and return the model output.

- Compute the validation loss at this step to compare it with the training loss, and show the decision boundary.


# -- Experiment Setup

- Dataset: 'make_moons'
- Number of samples: 1200
- Noise levels: '[0.05, 0.20, 0.40]'
- Train / Validation split: 75% /25%
- Feature scaling: StandardScaler (fit on full dataset)
- Model: MLP with 2 hidden layers
  - Architecture: 2 -> 32 -> 32 -> 1
  - Actavition: ReLU
- Loss: BCEwithLogitsLoss
- Optimizer: Adam
- Learning rate: 1e-2
- Epochs: 1500
- Evaluation: Decision Boundary

### -- Observations

#### Noise = 0.05 (Low noise)

- The decision boundary is smooth and well-aligned with the true data geometry.
- The two moon-shaped clusters are clearly separable.
- Training converges quickly and stably.
- The learned boundary closely matches intuitive expectations.

#### Noise = 0.20 (Moderate noise)

- The decision boundary becomes less smooth.
- Local fluctuations appear near overlapping regions.
- The global structure is still preserved, but uncertainty increases.
- Validation accuracy remains reasonable, but loss oscillation increases.

#### Noise = 0.40 (High noise)

- The decision boundary becomes irregular and fragmented.
- The model struggles to identify a consistent global structure.
- Many samples lie near or across the boundary.
- The learned boundary reflects noise rather than underlying geometry.
