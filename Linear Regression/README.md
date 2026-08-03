# Calculating the Cost Function in Linear Regression

Before updating the model parameters using **Gradient Descent**, we first need to measure how well our current model fits the training data. This measurement is called the **Cost Function**.

> **Note:** The parameters **θ₀** and **θ₁** are **not** part of the dataset. They are learned during training. In this example, we initialize them with **0** only to demonstrate how Gradient Descent works.

---

# Training Dataset

Suppose we have the following dataset:

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

We start with the following initial values:

```text
θ₀ = 0
θ₁ = 0
```

The hypothesis (prediction) function is:

```text
h(x) = θ₀ + θ₁ × x
```

Substituting the initial values:

```text
h(x) = 0
```

Since both parameters are zero, the model predicts **0** for every input.

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

# Step 3: Calculate the Error

The error for each training example is:

```text
Error = h(x) − y
```

| x | y | h(x) | Error |
|--:|--:|------:|------:|
| 1 | 2 | 0 | -2 |
| 2 | 3 | 0 | -3 |
| 3 | 5 | 0 | -5 |
| 4 | 4 | 0 | -4 |
| 5 | 6 | 0 | -6 |

---

# Step 4: Square the Errors

We square each error because:

- Negative and positive errors should not cancel each other.
- Larger errors receive a larger penalty.

| Error | Error² |
|------:|-------:|
| -2 | 4 |
| -3 | 9 |
| -5 | 25 |
| -4 | 16 |
| -6 | 36 |

Sum of squared errors:

```text
4 + 9 + 25 + 16 + 36 = 90
```

---

# Step 5: Calculate the Cost Function

The Cost Function for Linear Regression is:

```text
                 m
J(θ₀, θ₁) = 1/(2m) × Σ (h(xᵢ) − yᵢ)²
                i=1
```

Where:

- **m** = number of training examples

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

The Cost Function is:

```text
J(θ₀, θ₁) = 9
```

A Cost of **9** means the model's predictions are still far from the actual values because the parameters have not yet been optimized.

---

# What Happens Next?

Now Gradient Descent updates the parameters **θ₀** and **θ₁** to reduce the Cost.

The goal is to minimize the Cost Function after each iteration until the model finds the best-fitting line.

---

# First Gradient Descent Iteration (Manual Calculation)

Remember that **θ₀** and **θ₁** are **learned from the data**.

They are **not** stored in the dataset.

We continue using:

```text
θ₀ = 0
θ₁ = 0
α = 0.1
```

where **α** is the learning rate.

---

# Step 1: Compute Predictions

The hypothesis function is:

```text
h(x) = θ₀ + θ₁ × x
```

Since:

```text
θ₀ = 0
θ₁ = 0
```

the prediction becomes:

```text
h(x) = 0
```

for every training example.

---

# Step 2: Compute Errors

| x | y | h(x) | Error |
|--:|--:|------:|------:|
| 1 | 2 | 0 | -2 |
| 2 | 3 | 0 | -3 |
| 3 | 5 | 0 | -5 |
| 4 | 4 | 0 | -4 |
| 5 | 6 | 0 | -6 |

---

# Step 3: Update θ₀

Gradient Descent updates θ₀ using:

```text
θ₀ := θ₀ − α × (1/m) × Σ(h(xᵢ) − yᵢ)
```

Sum of errors:

```text
-2 + (-3) + (-5) + (-4) + (-6) = -20
```

Substitute the values:

```text
θ₀ = 0 − 0.1 × (-20 / 5)
```

```text
θ₀ = 0 − 0.1 × (-4)
```

```text
θ₀ = 0.4
```

---

# Step 4: Update θ₁

Gradient Descent updates θ₁ using:

```text
θ₁ := θ₁ − α × (1/m) × Σ((h(xᵢ) − yᵢ) × xᵢ)
```

Compute the products:

| Error | x | Error × x |
|------:|--:|----------:|
| -2 | 1 | -2 |
| -3 | 2 | -6 |
| -5 | 3 | -15 |
| -4 | 4 | -16 |
| -6 | 5 | -30 |

Sum:

```text
-2 + (-6) + (-15) + (-16) + (-30) = -69
```

Substitute the values:

```text
θ₁ = 0 − 0.1 × (-69 / 5)
```

```text
θ₁ = 0 + 1.38
```

```text
θ₁ = 1.38
```

---

# Parameters After the First Iteration

| Parameter | Value |
|----------:|------:|
| θ₀ | 0.40 |
| θ₁ | 1.38 |

These are **not** the final values.

Gradient Descent will repeat the same calculations many times.

After every iteration:

1. Compute new predictions.
2. Compute the new Cost.
3. Update θ₀.
4. Update θ₁.
5. Repeat until the Cost reaches its minimum.

---

# Key Takeaway

The training dataset contains only:

- Input features (**x**)
- Target values (**y**)

The parameters **θ₀** and **θ₁** are **unknown** at the beginning.

The purpose of **Gradient Descent** is to learn the values of **θ₀** and **θ₁** that minimize the **Cost Function**, allowing the Linear Regression model to make accurate predictions.
