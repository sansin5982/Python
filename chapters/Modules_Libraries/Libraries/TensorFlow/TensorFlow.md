# TensorFlow

## Introduction to TensorFlow
* TensorFlow is an open-source machine learning framework developed by Google Brain Team.
* Designed for numerical computation and large-scale machine learning.
* Useful for:
    * Neural Networks (Deep Learning)
    * Computer Vision
    * Natural Language Processing (NLP)
    * Time Series Analysis
    * Reinforcement Learning

### Why TensorFlow?
* Efficient computation graph (Graph & Eager execution modes)
* GPU & TPU acceleration
* Scalable for production (TensorFlow Serving, TFX)
* Integration with Keras (High-level API)
* Cross-platform (Desktop, Cloud, Mobile)


```python
# Download tensorflow library
# ! pip install tensorflow
```

### 1. Tensors
* Multi-dimensional arrays (like numpy arrays).
* All computations in TensorFlow use tensors.


```python
import tensorflow as tf
```


```python
# Creating a tensor
tensor = tf.constant([[1, 2], [3, 4]])
print(tensor)
```

    tf.Tensor(
    [[1 2]
     [3 4]], shape=(2, 2), dtype=int32)
    

#### Explanation:
* tf.constant: Creates an immutable tensor.
* Can create tensors of any dimension (0D scalar, 1D vector, 2D matrix, etc.)

### 2. Variables
Mutable tensors used in ML models (for weights, biases).


```python
var = tf.Variable([[5, 6], [7, 8]])
print(var)
```

    <tf.Variable 'Variable:0' shape=(2, 2) dtype=int32, numpy=
    array([[5, 6],
           [7, 8]])>
    

#### Explanation:
* Variables are used to store parameters that need to be updated during training.

### 3. Basic Operations


```python
a = tf.constant([[1, 2], [3, 4]])
b = tf.constant([[5, 6], [7, 8]])

# Addition
add = tf.add(a, b)

# Multiplication
mul = tf.multiply(a, b)

# Matrix Multiplication
matmul = tf.matmul(a, b)

print(a)
print(b)
print("Addition:\n", add)
print("Multiplication:\n", mul)
print("Matrix Multiplication:\n", matmul)
```

    tf.Tensor(
    [[1 2]
     [3 4]], shape=(2, 2), dtype=int32)
    tf.Tensor(
    [[5 6]
     [7 8]], shape=(2, 2), dtype=int32)
    Addition:
     tf.Tensor(
    [[ 6  8]
     [10 12]], shape=(2, 2), dtype=int32)
    Multiplication:
     tf.Tensor(
    [[ 5 12]
     [21 32]], shape=(2, 2), dtype=int32)
    Matrix Multiplication:
     tf.Tensor(
    [[19 22]
     [43 50]], shape=(2, 2), dtype=int32)
    

## Building Neural Network with Keras API

## 1. Sequential Model Example (FFNN)


```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

# Define model
model = Sequential([
    Dense(10, activation='relu', input_shape=(4,)),
    Dense(3, activation='softmax')
])

# Model summary
model.summary()
```

    Model: "sequential"
    _________________________________________________________________
     Layer (type)                Output Shape              Param #   
    =================================================================
     dense (Dense)               (None, 10)                50        
                                                                     
     dense_1 (Dense)             (None, 3)                 33        
                                                                     
    =================================================================
    Total params: 83
    Trainable params: 83
    Non-trainable params: 0
    _________________________________________________________________
    

#### Explanation:
* Sequential: Linear stack of layers.
* Dense: Fully connected layer.
    * 10 neurons, activation ReLU.
    * Output layer with 3 neurons, softmax activation.
* input_shape=(4,): Input vector with 4 features.
* model.summary(): Prints model architecture.

### 2. Compile Model


```python
model.compile(optimizer='adam', 
              loss='sparse_categorical_crossentropy', 
              metrics=['accuracy'])
```

#### Explanation:
* optimizer: Algorithm for weight updates (Adam optimizer).
* loss: Function to minimize (cross-entropy for classification).
* metrics: Evaluation metric during training (accuracy).

### 3. Training the Model


```python
import numpy as np

# Dummy data
X_train = np.random.random((100, 4))
y_train = np.random.randint(3, size=(100,))

# Train model
model.fit(X_train, y_train, epochs=10, batch_size=16)
```

    Epoch 1/10
    7/7 [==============================] - 1s 7ms/step - loss: 1.1444 - accuracy: 0.3100
    Epoch 2/10
    7/7 [==============================] - 0s 2ms/step - loss: 1.1397 - accuracy: 0.3200
    Epoch 3/10
    7/7 [==============================] - 0s 3ms/step - loss: 1.1365 - accuracy: 0.3100
    Epoch 4/10
    7/7 [==============================] - 0s 2ms/step - loss: 1.1333 - accuracy: 0.3100
    Epoch 5/10
    7/7 [==============================] - 0s 2ms/step - loss: 1.1310 - accuracy: 0.3100
    Epoch 6/10
    7/7 [==============================] - 0s 3ms/step - loss: 1.1284 - accuracy: 0.3000
    Epoch 7/10
    7/7 [==============================] - 0s 2ms/step - loss: 1.1254 - accuracy: 0.3000
    Epoch 8/10
    7/7 [==============================] - 0s 2ms/step - loss: 1.1229 - accuracy: 0.3000
    Epoch 9/10
    7/7 [==============================] - 0s 3ms/step - loss: 1.1209 - accuracy: 0.3000
    Epoch 10/10
    7/7 [==============================] - 0s 2ms/step - loss: 1.1191 - accuracy: 0.3000
    




    <keras.callbacks.History at 0x232cf39cee0>



#### Explanation:
* X_train: 100 samples, 4 features.
* y_train: 100 target labels (3 classes).
* epochs: Number of training cycles.
* batch_size: Number of samples per gradient update.

### 4. Evaluation & Prediction


```python
# Evaluation
loss, accuracy = model.evaluate(X_train, y_train)
print(f"Loss: {loss}, Accuracy: {accuracy}")

# Prediction
preds = model.predict(X_train[:5])
print(preds)
```

    4/4 [==============================] - 0s 4ms/step - loss: 1.1178 - accuracy: 0.2900
    Loss: 1.1178007125854492, Accuracy: 0.28999999165534973
    1/1 [==============================] - 0s 68ms/step
    [[0.3079478  0.3539794  0.33807284]
     [0.30222064 0.38728613 0.3104933 ]
     [0.32231408 0.34936124 0.32832468]
     [0.30219293 0.40334246 0.29446468]
     [0.18266308 0.48452815 0.33280867]]
    

#### Explanation:
* evaluate: Checks performance on given data.
* predict: Predicts class probabilities for given samples.

## Custom Training with GradientTape


```python
# Variables
W = tf.Variable(tf.random.normal([2, 1]))
b = tf.Variable(tf.random.normal([1]))

# Input
X = tf.constant([[1.0, 2.0], [3.0, 4.0]])
y_true = tf.constant([[1.0], [2.0]])

# Forward & Backward Pass
with tf.GradientTape() as tape:
    y_pred = tf.matmul(X, W) + b
    loss = tf.reduce_mean(tf.square(y_pred - y_true))

# Gradients
grads = tape.gradient(loss, [W, b])
print("Gradients:\n", grads)
```

    Gradients:
     [<tf.Tensor: shape=(2, 1), dtype=float32, numpy=
    array([[2.6718721],
           [3.8426585]], dtype=float32)>, <tf.Tensor: shape=(1,), dtype=float32, numpy=array([1.1707864], dtype=float32)>]
    

#### Explanation:
* GradientTape: Records operations for automatic differentiation.
* Computes gradients of loss w.r.t variables.
* Updates weights manually if required (Custom training loop).

## TensorFlow Dataset API


```python
# Dummy dataset
data = tf.data.Dataset.from_tensor_slices((X_train, y_train))

# Batching and shuffling
data = data.shuffle(buffer_size=100).batch(16)

# Iterating dataset
for batch_X, batch_y in data.take(1):
    print(batch_X.shape, batch_y.shape)
```

    (16, 4) (16,)
    

#### Explanation:
* Dataset API: Efficient data input pipeline.
* .shuffle(): Randomizes data order.
* .batch(): Splits data into batches.
* .take(): Limits number of batches to iterate.

## TensorFlow Serving & Model Export



```python
# Save model
model.save('my_model')

# Load model
new_model = tf.keras.models.load_model('my_model')

# Predict using loaded model
new_preds = new_model.predict(X_train[:5])
print(new_preds)
```

    WARNING:absl:Found untraced functions such as _update_step_xla while saving (showing 1 of 1). These functions will not be directly callable after loading.
    

    INFO:tensorflow:Assets written to: my_model\assets
    

    INFO:tensorflow:Assets written to: my_model\assets
    

    1/1 [==============================] - 0s 40ms/step
    [[0.3079478  0.3539794  0.33807284]
     [0.30222064 0.38728613 0.3104933 ]
     [0.32231408 0.34936124 0.32832468]
     [0.30219293 0.40334246 0.29446468]
     [0.18266308 0.48452815 0.33280867]]
    

#### Explanation:
* Saves model in SavedModel format.
* Reloads it for inference or deployment.

## TensorFlow Key Functionalities Recap
| Feature             | Purpose                               |
|---------------------|---------------------------------------|
| Tensors             | Multi-dimensional array operations    |
| Variables           | Mutable tensors for ML models         |
| Layers (Dense, Conv)| Building neural network architectures |
| Optimizers          | Gradient Descent methods              |
| Loss Functions      | Error computation & minimization      |
| GradientTape        | Automatic differentiation             |
| Dataset API         | Data pipelines for large datasets     |
| Model Saving/Serving| Exporting models for deployment       |

### Summary
TensorFlow is essential for deep learning workflows.
It offers both high-level (Keras) & low-level APIs.
Optimized for both research & production use.
Integrated with GPU/TPU for scalable training.


```python

```
