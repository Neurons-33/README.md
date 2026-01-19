# Control the noise level to observe how noise affects the decision boundary during training.

- Neurons flow through the activation function to introduce nonlinearity into the model.

- We keep the logits, as they help reduce prediction errors, then pass the data into the training function and return the model output.

- Compute the validation loss at this step to compare it with the training loss, and show the decision boundary.


# -- Experiment Setup
- Dataset: Moons
- Model: MLP
- Actavition: ReLU
- Optimizer: Adam
- Evaluation: Decision Boundary
