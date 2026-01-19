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
