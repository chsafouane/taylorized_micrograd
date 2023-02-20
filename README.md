# Taylorized micrograd

"Stupid is as stupid does"

## Table of Contents

- [About](#about)
- [Getting Started](#getting_started)
- [Usage](#usage)

## About <a name = "about"></a>

This project implements backpropagation over a dynamically built DAG. It's 100% inspired from [Andrej Karpathy's project](https://github.com/karpathy/micrograd). Most of the code is copied verbatim (well, developped along with Andrej's lecture).

The only difference is that instead of implementing activation functions such as `tanh` and `sigmoid`, we only implement a Taylor expansion of the exponential function.
The activation functions will use the Taylor expansion of the exponential function as a building block.

While this project was created just for fun and seems to me like a stupid idea, but the thing is one can use a different order of expansion for the exponential in each tanh/sigmoid/etc that is used.

While using low-order expansions might seem like (over) regularizing the model, using a different order of expansion might be thought of as dropout.

I'm quite sure everyone thought of dropout as being a stupid idea when it was created (but I admit there was empirical evidence/benchmarks to support the claims, none will be given in this context).

## Getting Started <a name = "getting_started"></a>



### Prerequisites

No specific package is required

### Installing

Documentation and Installation are WIP

## Usage <a name = "usage"></a>

If you'd like to use the 3rd order Taylor expansion for the exponential function, you can do as follows:

```python
# The input is 2
a = Value(2.0, label="a")

# We use a 3rd-order Taylor expansion of the exponential
b = a.exp(3); b.label = "b"

# Backward propagation
b.backward()
```

The same applies for `tanh`

```python
# The input is 2
a = Value(2.0, label="a")

# We use a 10th-order Taylor expansion of the exponential
b = a.tanh(10); b.label = "b"

# Backward propagation
b.backward()
```

You can add other activation functions in case you'd like to experiment with them. Adding other activation functions is a WIP.
