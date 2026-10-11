# Deep Learning

[Youtube Playlist](https://www.youtube.com/watch?v=YFNKnUhm_-s&list=PLZoTAELRMXVPGU70ZGsckrMdr0FteeRUi&index=1)

- Back-propagation and Chain Rule ([Video](https://www.youtube.com/watch?v=Ilg3gGewQ5U), [Video](https://www.youtube.com/watch?v=kbGu60QBx2o))
    - Partial computations of the gradient from one layer are reused in the computation of the gradient for the previous layer

- Activation Functions
    - **Sigmoid: $\frac{1}{1+e^{-x}}$**
    - **tanh:** No need to remember exact formula
    - **Relu: $max(x,0)$**
    - **Leaky Relu:** $max(x, 0.01x)$
    - **ELU (Exponential Linear unit):**
    - **PRelu (Parametric Relu):** $max(x, \alpha x)$
    - **Swish (Self-Gated):** $x \times sigmoid(x)$
    - **Softplus: $ln(1+e^{x})$**
    - **Softmax: $\frac{e^{x_i}}{\sum e^{x_i}}$**
    
- Optimisers
    - Gradient Descent
    - Stochastic Gradient Descent
    - Mini-batch SGD
    - SGD with momentum
    - Adagrad (Adaptive Gradient Descent)
        - Adjusting learning rate based on past gradients
    - Adadelta and RMSProp
    - Adam
        - Smoothening with momentum
        - Adaptive gradient with RMSProp

- Loss Functions
    - Regression
        - Mean Squared Error
        - Mean Absolute Error
        - Huber loss
    - Classification
        - Binary Cross Entropy
        - Categorical (multi-class) Cross Entropy

- Weight Initialization Techniques
    - Random Initialization
    - He Initialization (works well with ReLU)
    - Xavier Initialization (works well with sigmoid and tanh activations)

- Regularization Techniques
    - L1 Regularization (Lasso)
    - L2 Regularization (Ridge)
    - Dropout
    - Early Stopping
    - Batch Normalization
    - Data Augmentation

### **Vanishing gradient problem**

1. **Deep Networks, Small Gradients:**
    - Happens in deep neural networks with many layers
    - Gradients (derivatives) become very small during training
2. **Chain rule and backpropagation**
    - During backpropagation, gradients are multiplied as they move backward through the layers
    - When these gradients are tiny (close to zero), the multiplication makes them even smaller
3. **Culprit 1: Activation Functions**
    - Common activation functions like sigmoid and tanh "squash" input values into a limited range
    - As the input values get extreme, these functions saturate, causing gradients to approach zero
4. **Culprit 2: Weight Initialization**
    - Inappropriate weight initialization can worsen the problem
    - Starting with very small weights may lead to early saturation of activation functions
5. **Consequences for Learning**
    - Extremely small gradients mean the model learns very slowly or may stop learning altogether
    - Layers closer to the input are more affected.
6. **Mitigations and Solutions:**
    - Use activation functions like ReLU that don't saturate for positive inputs.
    - Apply techniques like batch normalization to stabilize and normalize inputs.

[What is a Two-Tower Embedding Model? - Hopsworks](https://www.hopsworks.ai/dictionary/two-tower-embedding-model)