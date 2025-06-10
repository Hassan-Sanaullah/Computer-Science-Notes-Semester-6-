# Runge-Kutta 4th Order Method (RK4)

Let's go step by step and **learn the Runge-Kutta 4th Order Method (RK4)** in full detail — no shortcuts or rushing. This is one of the most accurate single-step methods used to numerically solve first-order ordinary differential equations (ODEs) of the form:

$$
\frac{dy}{dt} = f(t, y), \quad y(t_0) = y_0
$$

---

## 🔷 Objective

Estimate the value of $y$ at $t_{n+1} = t_n + h$, given:

* The differential equation $\frac{dy}{dt} = f(t, y)$
* The initial condition $y(t_0) = y_0$
* A step size $h$

---

## 🔶 RK4 Formula

RK4 uses **four evaluations of the function $f(t, y)$** at each step:

$$
\begin{align*}
k_1 &= f(t_n, y_n) \\
k_2 &= f\left(t_n + \frac{h}{2},\ y_n + \frac{h}{2}k_1\right) \\
k_3 &= f\left(t_n + \frac{h}{2},\ y_n + \frac{h}{2}k_2\right) \\
k_4 &= f(t_n + h,\ y_n + hk_3) \\
\end{align*}
$$

Then compute:

$$
y_{n+1} = y_n + \frac{h}{6} (k_1 + 2k_2 + 2k_3 + k_4)
$$

---

## 🔍 Why Four Slopes?

* $k_1$: slope at the beginning of the interval  
* $k_2$: slope at the midpoint using $k_1$  
* $k_3$: slope at the midpoint using $k_2$  
* $k_4$: slope at the end using $k_3$  

Then we average them, giving double weight to the midpoint values $k_2$ and $k_3$, since they better represent the actual behavior of the function.

---

## 🧮 Step-by-Step Example

Let’s solve the same example we did for earlier methods, so you can compare them:

### Problem:

$$
\frac{dy}{dt} = y - t^2 + 1,\quad y(0) = 0.5,\quad h = 0.2
$$

We want to compute $y(0.2)$.

---

### ✅ Step 1: Identify values

* $t_0 = 0$  
* $y_0 = 0.5$  
* $h = 0.2$  
* $f(t, y) = y - t^2 + 1$

---

### ✅ Step 2: Compute $k_1$

$$
k_1 = f(t_0, y_0) = f(0, 0.5) = 0.5 - 0^2 + 1 = 0.5 + 1 = \boxed{1.5}
$$

---

### ✅ Step 3: Compute $k_2$

$$
k_2 = f\left(t_0 + \frac{h}{2},\ y_0 + \frac{h}{2}k_1\right) = f(0.1,\ 0.5 + 0.1 \cdot 1.5) = f(0.1, 0.65)
$$

Now compute:

$$
f(0.1, 0.65) = 0.65 - (0.1)^2 + 1 = 0.65 - 0.01 + 1 = \boxed{1.64}
$$

---

### ✅ Step 4: Compute $k_3$

$$
k_3 = f\left(0.1,\ 0.5 + 0.1 \cdot 1.64\right) = f(0.1, 0.664)
$$

$$
f(0.1, 0.664) = 0.664 - 0.01 + 1 = \boxed{1.654}
$$

---

### ✅ Step 5: Compute $k_4$

$$
k_4 = f(t_0 + h,\ y_0 + h \cdot k_3) = f(0.2,\ 0.5 + 0.2 \cdot 1.654) = f(0.2,\ 0.5 + 0.3308) = f(0.2, 0.8308)
$$

$$
f(0.2, 0.8308) = 0.8308 - 0.04 + 1 = \boxed{1.7908}
$$

---

### ✅ Step 6: Compute $y_1$

$$
y_1 = y_0 + \frac{h}{6} (k_1 + 2k_2 + 2k_3 + k_4)
$$

Plug in the values:

$$
y_1 = 0.5 + \frac{0.2}{6} (1.5 + 2 \cdot 1.64 + 2 \cdot 1.654 + 1.7908)
$$

Compute the sum:

$$
= 0.5 + \frac{0.2}{6} (1.5 + 3.28 + 3.308 + 1.7908) = 0.5 + \frac{0.2}{6} \cdot 9.8788
$$

$$
= 0.5 + 0.03333 \cdot 9.8788 = 0.5 + 0.3293 \approx \boxed{0.8293}
$$

---

## ✅ Final Answer

Using RK4 method with $h = 0.2$:

$$
y(0.2) \approx \boxed{0.8293}
$$

---

 🔄 You can continue this same process to compute $y(0.4),\ y(0.6),\ \ldots$ etc. Just repeat steps using the newly computed $t$ and $y$ values.

---


# Example 2

Let's solve a **first-order ODE with trigonometric functions** using the **Runge-Kutta 4th Order (RK4) Method** step-by-step.

---

## ✅ Example:

$$
\frac{dy}{dt} = \cos(t) - y, \quad y(0) = 1, \quad h = 0.1
$$

We want to estimate the value of $y(0.1)$.

---

## 🧾 Step-by-Step Using RK4

Given:

* $f(t, y) = \cos(t) - y$
* $t_0 = 0$
* $y_0 = 1$
* $h = 0.1$

---

### 🔹 Step 1: Compute $k_1$

$$
k_1 = f(t_0, y_0) = \cos(0) - 1 = 1 - 1 = \boxed{0}
$$

---

### 🔹 Step 2: Compute $k_2$

$$
k_2 = f\left(t_0 + \frac{h}{2},\ y_0 + \frac{h}{2}k_1\right) = f(0.05,\ 1 + 0.05 \cdot 0) = f(0.05,\ 1)
$$

$$
k_2 = \cos(0.05) - 1 \approx 0.99875 - 1 = \boxed{-0.00125}
$$

---

### 🔹 Step 3: Compute $k_3$

$$
k_3 = f\left(0.05,\ 1 + 0.05 \cdot (-0.00125)\right) = f(0.05,\ 0.9999375)
$$

$$
k_3 = \cos(0.05) - 0.9999375 \approx 0.99875 - 0.9999375 = \boxed{-0.00119}
$$

---

### 🔹 Step 4: Compute $k_4$

$$
k_4 = f(t_0 + h,\ y_0 + h \cdot k_3) = f(0.1,\ 1 + 0.1 \cdot (-0.00119)) = f(0.1,\ 0.999881)
$$

$$
k_4 = \cos(0.1) - 0.999881 \approx 0.99500 - 0.999881 = \boxed{-0.004881}
$$

---

### 🔹 Step 5: Combine for Final $y_1$

$$
y_1 = y_0 + \frac{h}{6}(k_1 + 2k_2 + 2k_3 + k_4)
$$

$$
y_1 = 1 + \frac{0.1}{6}(0 + 2(-0.00125) + 2(-0.00119) + (-0.004881))
$$

$$
= 1 + \frac{0.1}{6}(-0.0025 - 0.00238 - 0.004881) = 1 + \frac{0.1}{6}(-0.009761)
$$

$$
= 1 - 0.1 \cdot 0.001627 = 1 - 0.0001627 \approx \boxed{0.99984}
$$

---

## ✅ Final Answer:

$$
y(0.1) \approx \boxed{0.99984}
$$

---