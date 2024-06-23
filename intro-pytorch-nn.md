# Intro To Pytorch and Neural Networks


### Tensors
Tensors are the fundamentals building blocks of neural networks. They are similar to numpy arrays, tensors act as storage containers for numerical data.

Pytorch Tensor
torch.tensor() - Takes two parameters, data and dtype. Data can be a list, tuple, or numpy array. Dtype is the data type of the tensor. Common data types are torch.int and torch.float.

```python
# convert a DataFrame named df to a PyTorch tensor
torch.tensor(
    df.values, 
    dtype=torch.float)
```
