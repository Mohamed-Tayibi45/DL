# Calculating the Cost Function in Linear Regression

Before updating the model parameters using **Gradient Descent**, we first need to measure how well our current model fits the training data. This measurement is called the **Cost Function**.

> **Note:** In this example, we initialize the model parameters with:
>
> - θ₀ = 0
> - θ₁ = 0
>
> These are only initial values. During training, Gradient Descent will learn the best values.

---

# Training Dataset

| x (Feature) | y (Actual Value) |
|------------:|-----------------:|
| 1 | 2 |
| 2 | 3 |
| 3 | 5 |
| 4 | 4 |
| 5 | 6 |

Number of training examples:

```text
m = 5
```

---

# Step 1: Initialize the Parameters

```text
θ₀ = 0
θ₁ = 0
```

The hypothesis function is:

```text
h(x) = θ₀ + θ₁ × x
```

Substituting the initial values:

```text
h(x) = 0
```

---

# Step 2: Calculate Predictions

| x | Actual y | Predicted h(x) |
|--:|---------:|---------------:|
| 1 | 2 | 0 |
| 2 | 3 | 0 |
| 3 | 5 | 0 |
| 4 | 4 | 0 |
| 5 | 6 | 0 |

---

# Step 3: Calculate the Absolute Error

For easier understanding, we calculate the absolute error:

```text
Absolute Error = |h(x) − y|
```

| x | y | h(x) | Absolute Error |
|--:|--:|------:|---------------:|
| 1 | 2 | 0 | 2 |
| 2 | 3 | 0 | 3 |
| 3 | 5 | 0 | 5 |
| 4 | 4 | 0 | 4 |
| 5 | 6 | 0 | 6 |

---

# Step 4: Square the Errors

| Absolute Error | Squared Error |
|---------------:|--------------:|
| 2 | 4 |
| 3 | 9 |
| 5 | 25 |
| 4 | 16 |
| 6 | 36 |

Sum of squared errors:

```text
4 + 9 + 25 + 16 + 36 = 90
```

---

# Step 5: Calculate the Cost Function

```text
                 m
J(θ₀, θ₁) = 1/(2m) × Σ (h(xᵢ) − yᵢ)²
                i=1
```

Since:

```text
m = 5
```

Substitute the values:

```text
J = 90 / (2 × 5)
```

```text
J = 90 / 10
```

```text
J = 9
```

---

# Final Result

```text
Cost = 9
```

The Cost Function is **9**, indicating that the model is still making large prediction errors.

---

# What's Next?

The next step is to use **Gradient Descent** to update **θ₀** and **θ₁**, reducing the Cost Function after every iteration until the model finds the best-fitting line.
