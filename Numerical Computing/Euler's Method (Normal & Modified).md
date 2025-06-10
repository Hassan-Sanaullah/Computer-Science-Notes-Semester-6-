# Euler’s Method

## 🔷 What is Euler’s Method?

Euler’s Method is a **first-order numerical method** used to **approximate solutions** of **initial value problems (IVPs)** of the form:

$$
\frac{dy}{dx} = f(x, y), \quad y(x_0) = y_0
$$

We use this when:

- We are **given** a differential equation (DE)  
- We **cannot** solve it analytically  
- We want to compute **approximate values** of $y$ at discrete points $x_1, x_2, \dots$

---

## 🔷 Basic Idea

From calculus, the derivative $f(x, y) = \frac{dy}{dx}$ gives the **slope** of the tangent at point $(x, y)$.

Euler’s Method uses this slope to **step forward** from a known point $(x_n, y_n)$ to the next point $(x_{n+1}, y_{n+1})$:

$$
y_{n+1} = y_n + h \cdot f(x_n, y_n)
$$

where:

- $h$ is the **step size**  
- $f(x_n, y_n)$ is the **slope** (derivative) at the current point  
- $(x_n, y_n)$ is the current point  
- $(x_{n+1}, y_{n+1})$ is the next point

This formula is repeated iteratively.

---

## 🔷 Step-by-Step Summary

1. Start with the known initial value:

   $$
   x_0, \quad y_0
   $$

2. Choose a step size $h$  
3. Compute the next value using:

   $$
   y_{n+1} = y_n + h \cdot f(x_n, y_n)
   $$

4. Update:

   $$
   x_{n+1} = x_n + h
   $$

5. Repeat for as many steps as needed.

---

##  Example: Solve an ODE using Euler’s Method

Solve the ODE:

$$
\frac{dy}{dx} = x + y, \quad y(0) = 1
$$

Estimate $y$ at $x = 0.1, 0.2, 0.3$ using step size $h = 0.1$

---

### Step 0: Initial values

$$
x_0 = 0, \quad y_0 = 1, \quad h = 0.1
$$

---

### Step 1: Compute $y_1$ at $x_1 = x_0 + h = 0.1$

$$
f(x_0, y_0) = x_0 + y_0 = 0 + 1 = 1
$$

$$
y_1 = y_0 + h \cdot f(x_0, y_0) = 1 + 0.1 \cdot 1 = 1.1
$$

---

### Step 2: Compute $y_2$ at $x_2 = x_1 + h = 0.2$

$$
f(x_1, y_1) = x_1 + y_1 = 0.1 + 1.1 = 1.2
$$

$$
y_2 = y_1 + h \cdot f(x_1, y_1) = 1.1 + 0.1 \cdot 1.2 = 1.22
$$

---

### Step 3: Compute $y_3$ at $x_3 = 0.3$

$$
f(x_2, y_2) = x_2 + y_2 = 0.2 + 1.22 = 1.42
$$

$$
y_3 = y_2 + h \cdot f(x_2, y_2) = 1.22 + 0.1 \cdot 1.42 = 1.362
$$

---

### ✅ Final Approximations

| $x$ | $y$ (Euler approx) |
|--------|------------------------|
| 0.0    | 1.000                  |
| 0.1    | 1.100                  |
| 0.2    | 1.220                  |
| 0.3    | 1.362                  |

---

## 🔷 Error and Accuracy

- Euler’s method is a **first-order method**, meaning its error per step is proportional to $h^2$, and total error over $n$ steps is $O(h)$.
- Reducing step size $h$ increases accuracy but requires more steps (and computation).
- It is not very accurate for stiff or rapidly changing solutions.

---

## 🔷 Geometric Interpretation

Euler’s Method approximates the **solution curve** using small **linear segments** (tangents). It's like drawing a curve using little straight-line steps, guided by the slope field.

---

## 🔷 Limitations

- Not accurate for large $h$  
- Can become unstable or diverge if $h$ is not small enough  
- Better alternatives: **Improved Euler (Heun’s method)** or **Runge-Kutta methods (RK4)**

---

## 🔷 Summary

| Concept       | Explanation                                     |
| ------------- | ----------------------------------------------- |
| **Used for**  | Approximating solutions of ODEs                 |
| **Equation**  | $y_{n+1} = y_n + h \cdot f(x_n, y_n)$         |
| **Given**     | $\frac{dy}{dx} = f(x, y), \quad y(x_0) = y_0$ |
| **Step size** | Smaller $h$ gives better accuracy             |
| **Accuracy**  | First-order (error $\propto h$)               |
| **Use case**  | Simple, introductory numerical solving          |

---

# Assignment Example

### 🧮 Given:

- Differential equation:  
  $$\frac{dy}{dt} = y - t^2 + 1$$

- Interval:  
  $$0 \le t \le 1$$

- Initial condition:  
  $$y(0) = 0.5$$

- Step size:  
  $$h = 0.2$$

We want to approximate the values of \( y \) at \( t = 0.2, 0.4, 0.6, 0.8, 1.0 \)

---

## 🔷 Euler’s Method Formula:

$$
y_{n+1} = y_n + h \cdot f(t_n, y_n)
$$

---

## 🔢 Step-by-Step Computation

We'll define:

$$
f(t, y) = y - t^2 + 1
$$

### Step 0:

- \( t_0 = 0 \), \( y_0 = 0.5 \)

---

### Step 1: \( t_1 = 0.2 \)

\[
f(t_0, y_0) = y_0 - t_0^2 + 1 = 0.5 - 0^2 + 1 = 1.5
\]

\[
y_1 = y_0 + h \cdot f(t_0, y_0) = 0.5 + 0.2 \cdot 1.5 = 0.5 + 0.3 = 0.8
\]

---

### Step 2: \( t_2 = 0.4 \)

\[
f(t_1, y_1) = y_1 - t_1^2 + 1 = 0.8 - 0.04 + 1 = 1.76
\]

\[
y_2 = y_1 + 0.2 \cdot 1.76 = 0.8 + 0.352 = 1.152
\]

---

### Step 3: \( t_3 = 0.6 \)

\[
f(t_2, y_2) = y_2 - t_2^2 + 1 = 1.152 - 0.16 + 1 = 1.992
\]

\[
y_3 = y_2 + 0.2 \cdot 1.992 = 1.152 + 0.3984 = 1.5504
\]

---

### Step 4: \( t_4 = 0.8 \)

\[
f(t_3, y_3) = y_3 - 0.6^2 + 1 = 1.5504 - 0.36 + 1 = 2.1904
\]

\[
y_4 = y_3 + 0.2 \cdot 2.1904 = 1.5504 + 0.43808 = 1.98848
\]

---

### Step 5: \( t_5 = 1.0 \)

\[
f(t_4, y_4) = y_4 - 0.8^2 + 1 = 1.98848 - 0.64 + 1 = 2.34848
\]

\[
y_5 = y_4 + 0.2 \cdot 2.34848 = 1.98848 + 0.469696 = 2.458176
\]

---

## ✅ Final Table of Values

| \( t \) | \( y \) (Euler Approximation) |
|--------|-------------------------------|
| 0.0    | 0.500000                      |
| 0.2    | 0.800000                      |
| 0.4    | 1.152000                      |
| 0.6    | 1.550400                      |
| 0.8    | 1.988480                      |
| 1.0    | 2.458176                      |

---
# Modified Euler's Method

Sure! Let's explore the **Modified Euler’s Method** (also called the **Improved Euler Method** or **Heun’s Method**) in **full mathematical detail**, including the formula, intuition, and a step-by-step example.

---

## 🔷 1. What Is the Modified Euler’s Method?

The **Modified Euler Method** is a **second-order numerical method** for solving **first-order ordinary differential equations (ODEs)**. It improves on the basic Euler’s Method by **reducing error** through a kind of **averaging**.

We are solving:

$$
\frac{dy}{dt} = f(t, y), \quad y(t_0) = y_0
$$

Modified Euler’s method uses the slope at the **beginning and at the end** of a step to estimate the next value of $y$. So, instead of just taking the slope at the start (as in standard Euler), it uses the **average** of slopes at the **start and predicted endpoint**.

---

## 🧮 2. Modified Euler Formula

Given step size $h$, and current point $(t_n, y_n)$:

1. **Predictor Step** (like Euler’s):

   $$
   y_{n}^{\text{predict}} = y_n + h \cdot f(t_n, y_n)
   $$

2. **Corrector Step**:

   $$
   y_{n+1} = y_n + \frac{h}{2} \left[ f(t_n, y_n) + f(t_{n+1}, y_{n}^{\text{predict}}) \right]
   $$

This is like saying:

- Take the slope at the current point $f(t_n, y_n)$
- Predict the next value
- Then also evaluate the slope at that predicted point
- Average both slopes and use it to compute a more accurate $y_{n+1}$

---

## 🔎 3. Step-by-Step Example

Let’s solve:

$$
\frac{dy}{dt} = y - t^2 + 1,\quad y(0) = 0.5,\quad h = 0.2
$$

We want to compute $y$ at $t = 0.2$

---

### 🔹 Step 1: Initial values

$$
t_0 = 0,\quad y_0 = 0.5
$$

$$
f(t_0, y_0) = 0.5 - 0^2 + 1 = 1.5
$$

---

### 🔹 Step 2: Predictor Step

$$
y_{\text{predict}} = y_0 + h \cdot f(t_0, y_0) = 0.5 + 0.2 \cdot 1.5 = 0.8
$$

This is the standard Euler step.

---

### 🔹 Step 3: Corrector Step

We now compute:

- $t_1 = 0.2$
- $f(t_1, y_{\text{predict}}) = 0.8 - 0.2^2 + 1 = 0.8 - 0.04 + 1 = 1.76$

Now average the two slopes:

$$
\text{average slope} = \frac{1}{2} \left(1.5 + 1.76\right) = \frac{3.26}{2} = 1.63
$$

So:

$$
y_1 = y_0 + h \cdot \text{average slope} = 0.5 + 0.2 \cdot 1.63 = 0.5 + 0.326 = 0.826
$$

---

### ✅ Final Result:

Using **Modified Euler’s Method**,

$$
y(0.2) \approx 0.826
$$

Compare this to:

- Euler’s method: $y(0.2) = 0.8$
- Exact solution: $y(0.2) \approx 0.8293$

So modified Euler is more accurate than standard Euler.

---

## 🔁 Repeat Process for More Steps

To compute $y_2$ at $t = 0.4$, use:

- $t_1 = 0.2$, $y_1 = 0.826$
- $f(t_1, y_1) = y_1 - t_1^2 + 1 = 0.826 - 0.04 + 1 = 1.786$
- Predictor:

  $$
  y_{\text{predict}} = y_1 + 0.2 \cdot 1.786 = 0.826 + 0.3572 = 1.1832
  $$

- $f(t_2, y_{\text{predict}}) = 1.1832 - 0.16 + 1 = 2.0232$
- Corrector:

  $$
  y_2 = y_1 + 0.2 \cdot \frac{1.786 + 2.0232}{2} = 0.826 + 0.2 \cdot 1.9046 = 0.826 + 0.38092 = 1.20692
  $$

---

## 📌 Summary Table of First Few Steps

| Step | $t$ | $y$ (Modified Euler) |
|------|-----|-----------------------|
| 0    | 0.0 | 0.5000                |
| 1    | 0.2 | 0.8260                |
| 2    | 0.4 | 1.2069                |
| ...  | ... | ...                   |

---

## 📚 Summary: Modified Euler Method

| Feature       | Euler       | Modified Euler        |
|---------------|-------------|------------------------|
| Accuracy      | First-order | Second-order           |
| Uses slope at | Start only  | Start + End (average)  |
| Error         | Higher      | Lower                  |

---

# Assignment Example

## 🔷 Problem

We are given:

$$
\frac{dy}{dt} = \frac{2 - 2ty}{t^2 + 1}, \quad y(0) = 1, \quad 0 \leq t \leq 1, \quad h = 0.2
$$

We will compute approximate values of $y$ at:

$$
t = 0,\ 0.2,\ 0.4,\ 0.6,\ 0.8,\ 1.0
$$

---

## 🔧 Step-by-Step: Modified Euler’s Method

### Formula Recap

1. Predictor step:

   $$
   y_{\text{predict}} = y_n + h \cdot f(t_n, y_n)
   $$

2. Corrector step:

   $$
   y_{n+1} = y_n + \frac{h}{2} \cdot \left[ f(t_n, y_n) + f(t_{n+1}, y_{\text{predict}}) \right]
   $$

---

## ✅ Step 1: Initial values

$$
t_0 = 0,\quad y_0 = 1
$$

We’ll compute $y_1 \approx y(0.2)$

---

### 🔹 Step 2: Compute $f(t_0, y_0)$

The function is:

$$
f(t, y) = \frac{2 - 2ty}{t^2 + 1}
$$

So at $t = 0$, $y = 1$:

$$
f(0, 1) = \frac{2 - 2(0)(1)}{0^2 + 1} = \frac{2}{1} = 2
$$

---

### 🔹 Step 3: Predictor step

$$
y_{\text{predict}} = y_0 + h \cdot f(t_0, y_0) = 1 + 0.2 \cdot 2 = 1 + 0.4 = 1.4
$$

---

### 🔹 Step 4: Compute $f(t_1, y_{\text{predict}})$

* $t_1 = 0.2$
* $y_{\text{predict}} = 1.4$

$$
f(0.2, 1.4) = \frac{2 - 2(0.2)(1.4)}{0.2^2 + 1} = \frac{2 - 0.56}{0.04 + 1} = \frac{1.44}{1.04} \approx 1.3846
$$

---

### 🔹 Step 5: Corrector step

Now correct the value of $y_1$:

$$
y_1 = y_0 + \frac{h}{2} \cdot \left[ f(t_0, y_0) + f(t_1, y_{\text{predict}}) \right]
$$

$$
y_1 = 1 + 0.1 \cdot (2 + 1.3846) = 1 + 0.1 \cdot 3.3846 = 1 + 0.33846 = \boxed{1.3385}
$$

---

## ✅ Summary so far

| Step | $t$ | $y$ (Modified Euler) |
| ---- | --- | -------------------- |
| 0    | 0.0 | 1.0000               |
| 1    | 0.2 | 1.3385               |

---
