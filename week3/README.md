# week-3-AI-NN
# Neural Network Training with Streamlit

This repository contains an implementation of a simple neural network using Streamlit for interactive visualization. The neural network is trained using backpropagation on a small dataset.

## Algorithm

The neural network consists of:
- An input layer with 2 neurons.
- A hidden layer with 2 neurons.
- An output layer with 1 neuron.

### Key Components:
1. **Feedforward**: Computes the output of the neural network.
2. **Sigmoid Activation Function**: Used for both the hidden and output layers.
3. **Backpropagation**: Adjusts the weights to minimize the error between the predicted and actual outputs.

### Sigmoid Function:
\[
\sigma(x) = \frac{1}{1 + e^{-x}}
\]

### Backpropagation:
- **Output Error**: \( \text{error} = y - \text{output} \)
- **Output Delta**: \( \text{delta} = \text{error} \times \sigma'(\text{output}) \)
- **Hidden Error**: Propagates the output error back to the hidden layer.
- **Hidden Delta**: \( \text{hidden\_delta} = \text{hidden\_error} \times \sigma'(\text{hidden\_output}) \)

## Code Overview

### `NeuralNetwork` Class
Implements a simple neural network with methods for feedforward, backpropagation, and training:
- `__init__`: Initializes weights and learning rate.
- `sigmoid` and `sigmoid_derivative`: Activation function and its derivative.
- `feedforward`: Computes the network's output.
- `backpropagate`: Updates the weights based on the error.
- `train`: Trains the neural network using the provided dataset.

### Streamlit Application
- **Training Data**: Predefined XOR dataset.
- **Train Neural Network**: Button to start the training process.
- **Test Neural Network**: Input fields to test the neural network with new data.

## Running the Application

1. **Install the Required Packages:**
   Ensure you have the necessary packages installed by running:
   ```bash
   pip install -r requirements.txt
