# Calculating the Cost Function in Linear Regression

Before updating the model parameters using **Gradient Descent**, we first need to measure how well our current model fits the training data. This is done using the **Cost Function**.

---

## Training Dataset

Suppose we have the following dataset:

| x (Feature) | y (Actual Value) |
|------------:|-----------------:|
| 1 | 2 |
| 2 | 3 |
| 3 | 5 |
| 4 | 4 |
| 5 | 6 |

---

# Step 1: Initialize the Parameters

Assume the initial parameters are:

- θ₀ = 0
- θ₁ = 1

The hypothesis function is:

\[
h(x)=\theta_0+\theta_1x
\]

Substituting the initial values:

\[
h(x)=x
\]

---

# Step 2: Calculate Predictions

Using the hypothesis, we predict the output for each training example.

| x | Actual y | Predicted h(x) |
|--:|---------:|---------------:|
| 1 | 2 | 1 |
| 2 | 3 | 2 |
| 3 | 5 | 3 |
| 4 | 4 | 4 |
| 5 | 6 | 5 |

---

# Step 3: Calculate the Error

The error for each example is:

\[
Error = h(x)-y
\]

| x | y | h(x) | Error |
|--:|--:|------:|------:|
| 1 | 2 | 1 | -1 |
| 2 | 3 | 2 | -1 |
| 3 | 5 | 3 | -2 |
| 4 | 4 | 4 | 0 |
| 5 | 6 | 5 | -1 |

---

# Step 4: Square the Errors

We square each error because:

- Negative and positive errors should not cancel each other.
- Larger errors receive a larger penalty.

| Error | Error² |
|------:|-------:|
| -1 | 1 |
| -1 | 1 |
| -2 | 4 |
| 0 | 0 |
| -1 | 1 |

Sum of squared errors:

\[
1+1+4+0+1=7
\]

---

# Step 5: Calculate the Cost Function

The Cost Function for Linear Regression is:

\[
J(\theta_0,\theta_1)=
\frac{1}{2m}
\sum_{i=1}^{m}
(h(x^{(i)})-y^{(i)})^2
\]

Where:

- **m** = number of training examples
- Here:

\[
m=5
\]

Substitute the values:

\[
J=\frac{7}{2\times5}
\]

\[
J=\frac{7}{10}
\]

\[
J=0.7
\]

---

# Final Result

The **Cost Function** is:

> **J(θ₀, θ₁) = 0.7**

This value tells us how far our predictions are from the actual values.

---

# What Happens Next?

If the Cost is large, **Gradient Descent** updates the parameters **θ₀** and **θ₁** to reduce the error.

For example:

| Iteration | θ₀ | θ₁ | Cost |
|----------:|---:|---:|-----:|
| 1 | 0.00 | 1.00 | 0.70 |
| 2 | 0.30 | 1.15 | 0.42 |
| 3 | 0.45 | 1.25 | 0.19 |
| 4 | 0.55 | 1.32 | 0.06 |
| 5 | 0.60 | 1.35 | 0.01 |

Notice that the **Cost** decreases after each iteration as the model learns a better relationship between the input and output data.

---

# Summary

The training process follows these steps:

1. Initialize **θ₀** and **θ₁**.
2. Compute predictions using the hypothesis function.
3. Calculate the error for every training example.
4. Square each error.
5. Sum all squared errors.
6. Compute the Cost Function.
7. Use **Gradient Descent** to update **θ₀** and **θ₁**.
8. Repeat until the Cost converges to a very small value.

This is the fundamental idea behind training a **Linear Regression** model from scratch.


------------------------------------------------------------------




# First Gradient Descent Iteration (Manual Calculation)

One important point to understand is that **θ₀** and **θ₁** are **not given in the dataset**.

They are **learned from the training data** using optimization algorithms such as **Gradient Descent** (or calculated directly using the **Normal Equation**).

Let's manually perform the **first Gradient Descent iteration**.

---

## Training Dataset

| x | y |
|--:|--:|
| 1 | 2 |
| 2 | 3 |
| 3 | 5 |
| 4 | 4 |
| 5 | 6 |

Number of training examples:

\[
m = 5
\]

---

# Step 1: Initialize the Parameters

We start with:

\[
\theta_0 = 0
\]

\[
\theta_1 = 0
\]

Learning rate:

\[
\alpha = 0.1
\]

The hypothesis function is:

\[
h(x)=\theta_0+\theta_1x
\]

Since both parameters are zero:

\[
h(x)=0
\]

This means the model predicts **0** for every input.

---

# Step 2: Compute Predictions and Errors

| x | y | h(x) | Error = h(x) − y |
|--:|--:|------:|----------------:|
| 1 | 2 | 0 | -2 |
| 2 | 3 | 0 | -3 |
| 3 | 5 | 0 | -5 |
| 4 | 4 | 0 | -4 |
| 5 | 6 | 0 | -6 |

---

# Step 3: Update θ₀

The Gradient Descent update rule is:

\[
\theta_0 :=
\theta_0
-
\alpha
\left(
\frac{1}{m}
\sum_{i=1}^{m}
(h(x^{(i)})-y^{(i)})
\right)
\]

### Sum of errors

\[
-2-3-5-4-6=-20
\]

Substitute the values:

\[
\theta_0
=
0
-
0.1
\left(
\frac{-20}{5}
\right)
\]

\[
=
0
-
0.1(-4)
\]

\[
=
0.4
\]

Therefore,

\[
\boxed{\theta_0=0.4}
\]

---

# Step 4: Update θ₁

The update rule for θ₁ is:

\[
\theta_1 :=
\theta_1
-
\alpha
\left(
\frac{1}{m}
\sum_{i=1}^{m}
(h(x^{(i)})-y^{(i)})x^{(i)}
\right)
\]

Compute the product of each error and its corresponding x value.

| Error | x | Error × x |
|------:|--:|----------:|
| -2 | 1 | -2 |
| -3 | 2 | -6 |
| -5 | 3 | -15 |
| -4 | 4 | -16 |
| -6 | 5 | -30 |

Sum:

\[
-2-6-15-16-30=-69
\]

Substitute into the equation:

\[
\theta_1
=
0
-
0.1
\left(
\frac{-69}{5}
\right)
\]

\[
=
0
+
1.38
\]

\[
=
1.38
\]

Therefore,

\[
\boxed{\theta_1=1.38}
\]

---

# Parameters After the First Iteration

| Parameter | Value |
|----------:|------:|
| θ₀ | **0.40** |
| θ₁ | **1.38** |

These are **not** the final values.

Gradient Descent will continue updating the parameters over many iterations until the Cost Function reaches its minimum.

---

# What Happens Next?

The next iteration uses the updated parameters:

\[
\theta_0=0.4
\]

\[
\theta_1=1.38
\]

The algorithm then repeats the same process:

1. Compute new predictions.
2. Compute new errors.
3. Update **θ₀**.
4. Update **θ₁**.
5. Repeat until the Cost Function converges.

Over time, the parameters move closer to the optimal values that best fit the training data.

---

# Key Takeaway

A common misconception is that **θ₀** and **θ₁** already exist in the dataset.

They do **not**.

The dataset only contains **features (x)** and **target values (y)**.

The purpose of training is to **learn** the values of **θ₀** and **θ₁** that minimize the Cost Function using **Gradient Descent** (or compute them directly using the **Normal Equation**).