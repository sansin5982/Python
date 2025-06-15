# 🧠 PyTorch 
This notebook covers the essentials of PyTorch with practical examples.

## 📌 1. Installing PyTorch
Install via pip if not already installed:


```python
#!pip install torch torchvision torchaudio
```

## 📌 2. PyTorch Tensors


```python
import torch

# Scalar
a = torch.tensor(3.14)

# 1D Tensor
b = torch.tensor([1, 2, 3])

# 2D Tensor
c = torch.tensor([[1, 2], [3, 4]])

# Random Tensor
d = torch.rand(3, 3)

a, b, c, d
```




    (tensor(3.1400),
     tensor([1, 2, 3]),
     tensor([[1, 2],
             [3, 4]]),
     tensor([[0.0721, 0.6970, 0.2052],
             [0.2283, 0.8324, 0.0977],
             [0.8353, 0.9661, 0.9009]]))



## 📌 3. Tensor Operations


```python
x = torch.tensor([1.0, 2.0])
y = torch.tensor([3.0, 4.0])

print("Addition:", x + y)
print("Multiplication:", x * y)
print("Dot Product:", torch.dot(x, y))
```

    Addition: tensor([4., 6.])
    Multiplication: tensor([3., 8.])
    Dot Product: tensor(11.)
    


```python
a = torch.rand(4, 1)
b = torch.rand(1, 4)
print("Broadcasted Addition Shape:", (a + b).shape)

# Reshape
a = torch.rand(4, 2)
a_reshaped = a.view(2, 4)
a_reshaped
```

    Broadcasted Addition Shape: torch.Size([4, 4])
    




    tensor([[0.0109, 0.1784, 0.0872, 0.1617],
            [0.8003, 0.5657, 0.5916, 0.4293]])



## 📌 4. GPU Support


```python
device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
x = torch.rand(3, 3).to(device)
x
```




    tensor([[0.5661, 0.9788, 0.4948],
            [0.8720, 0.1066, 0.0324],
            [0.3777, 0.4082, 0.7264]])



## 📌 5. Automatic Differentiation


```python
x = torch.tensor(2.0, requires_grad=True)
y = x**2 + 3*x + 1
y.backward()
x.grad
```




    tensor(7.)



## 📌 6. Building a Simple Neural Network


```python
import torch.nn as nn
import torch.nn.functional as F

class SimpleNN(nn.Module):
    def __init__(self):
        super(SimpleNN, self).__init__()
        self.fc1 = nn.Linear(2, 4)
        self.fc2 = nn.Linear(4, 1)

    def forward(self, x):
        x = F.relu(self.fc1(x))
        return torch.sigmoid(self.fc2(x))
```

## 📌 7. Training the Network


```python
model = SimpleNN()
criterion = nn.BCELoss()
optimizer = torch.optim.Adam(model.parameters(), lr=0.01)

X = torch.tensor([[0., 0.], [0., 1.], [1., 0.], [1., 1.]])
y = torch.tensor([[0.], [1.], [1.], [0.]])

for epoch in range(1000):
    optimizer.zero_grad()
    outputs = model(X)
    loss = criterion(outputs, y)
    loss.backward()
    optimizer.step()

    if epoch % 200 == 0:
        print(f'Epoch {epoch}, Loss: {loss.item()}')
```

    Epoch 0, Loss: 0.6987389326095581
    Epoch 200, Loss: 0.15495747327804565
    Epoch 400, Loss: 0.028060603886842728
    Epoch 600, Loss: 0.01099860854446888
    Epoch 800, Loss: 0.005848010536283255
    

## 📌 8. Saving and Loading Models


```python
torch.save(model.state_dict(), 'model.pth')

model2 = SimpleNN()
model2.load_state_dict(torch.load('model.pth'))
model2.eval()
```




    SimpleNN(
      (fc1): Linear(in_features=2, out_features=4, bias=True)
      (fc2): Linear(in_features=4, out_features=1, bias=True)
    )



#### 📌 10. Applications in GenAI & NLP
🔹 Use Cases:
    * Text Classification
    * Language Modeling (e.g., GPT)
    * Machine Translation
    * Transformer Architectures
🔹 Libraries:
    * torchtext – text preprocessing
    * transformers (by Hugging Face) – LLMs (GPT, BERT, etc.)

#### 🧪 11. Example: Text Classification with LSTM (Coming up...)
We can build an LSTM model or transformer block using PyTorch's modules like nn.Embedding, nn.LSTM, and nn.Linear. We’ll go step-by-step in the next session.

#### 📘 12. Summary
| Concept               | Tool/Method              |
| --------------------- | ------------------------ |
| Tensor Creation       | `torch.tensor`, `rand()` |
| Neural Network Layers | `nn.Linear`, `nn.ReLU`   |
| Loss Functions        | `nn.CrossEntropyLoss`    |
| Optimization          | `torch.optim.Adam`       |
| Autograd              | `backward()`, `.grad`    |
| GPU Usage             | `.to(device)`            |

