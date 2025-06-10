# Jacobi Method

The **Jacobi Method** is an iterative technique used to solve a system of linear equations of the form:  
$A\vec{x} = \vec{b}$

Where:

- $A$ is an $n \times n$ square matrix  
- $\vec{x}$ is the vector of unknowns $\begin{bmatrix}x_1, x_2, \dots, x_n\end{bmatrix}^T$  
- $\vec{b}$ is the constant vector $\begin{bmatrix}b_1, b_2, \dots, b_n\end{bmatrix}^T$

---

## 🔶 Step-by-step Derivation (Mathematical Only)

### 1. System of Equations

Suppose you have the system:

```
a₁₁x₁ + a₁₂x₂ + ... + a₁ₙxₙ = b₁  
a₂₁x₁ + a₂₂x₂ + ... + a₂ₙxₙ = b₂  
...  
aₙ₁x₁ + aₙ₂x₂ + ... + aₙₙxₙ = bₙ
```

### 2. Rearranging Each Equation

In the Jacobi Method, each variable is isolated in its own equation:

From the first equation:  
$x_1 = \frac{1}{a_{11}}\left(b_1 - \sum_{j \ne 1} a_{1j} x_j \right)$

In general form:  
$x_i = \frac{1}{a_{ii}}\left(b_i - \sum_{j \ne i} a_{ij} x_j \right), \quad \text{for } i = 1, 2, \dots, n$

This is the **update rule** for Jacobi iteration.

### 3. Iterative Process

Assume an initial guess:  
$x_1^{(0)}, x_2^{(0)}, \dots, x_n^{(0)}$

Then compute the next approximation using:  
$x_i^{(k+1)} = \frac{1}{a_{ii}} \left(b_i - \sum_{j \ne i} a_{ij} x_j^{(k)} \right)$

🔁 **Note**: All $x_j^{(k)}$ values are from the **previous iteration**.  
(Jacobi performs a fully **simultaneous update**.)

Repeat until convergence:  
$\left\| \vec{x}^{(k+1)} - \vec{x}^{(k)} \right\| < \text{tolerance}$

---

## 🔶 Matrix Form

We can express the Jacobi method using matrix operations. Decompose $A$ as:  
$A = D + (L + U)$

Where:

- $D$ = diagonal part of $A$  
- $L$ = strictly lower triangular part  
- $U$ = strictly upper triangular part

Then the Jacobi iteration becomes:

$\vec{x}^{(k+1)} = D^{-1}\left( \vec{b} - (L + U) \vec{x}^{(k)} \right)$

Or:

$\vec{x}^{(k+1)} = D^{-1}\left( \vec{b} - R \vec{x}^{(k)} \right) \quad \text{where } R = L + U$

---

## 🔶 Convergence Conditions

The Jacobi method does **not always converge**. A sufficient condition for convergence is:

### 🔸 Diagonal Dominance:

A matrix $A$ is **strictly diagonally dominant** if:  
$|a_{ii}| > \sum_{j \ne i} |a_{ij}|, \quad \forall i$

If $A$ is **strictly diagonally dominant** or **symmetric positive definite**, the Jacobi method is **guaranteed to converge**.

---

## 🔶 Summary

**Update Formula (per variable):**  
$x_i^{(k+1)} = \frac{1}{a_{ii}} \left(b_i - \sum_{j \ne i} a_{ij} x_j^{(k)} \right)$

**Matrix Form:**  
$\vec{x}^{(k+1)} = D^{-1}(\vec{b} - (L+U)\vec{x}^{(k)})$

**Requirements:**

- $A$ should be **strictly diagonally dominant** or **symmetric positive definite** for guaranteed convergence  
- Initial guess can be anything, e.g., $\vec{x}^{(0)} = \vec{0}$

# Example
## Example System of Equations

We want to solve the system:


$$10x + y + z = 6   (Equation 1) $$ 
$$x + 10y + z = 6   (Equation 2) $$ 
$$x + y + 10z = 6   (Equation 3)$$


We want to find values of $x, y, z$ that satisfy all three equations.

---

## 🔷 Step 1: Solve each equation for the variable on the left

Isolate the variable in each equation:

- From Equation 1:  
  $x = \frac{1}{10}(6 - y - z)$

- From Equation 2:  
  $y = \frac{1}{10}(6 - x - z)$

- From Equation 3:  
  $z = \frac{1}{10}(6 - x - y)$

These are the **update formulas** for the Jacobi iteration.

---

## 🔷 Step 2: Initial Guess

Start with an initial guess for all variables:

$$
x^{(0)} = 0, \quad y^{(0)} = 0, \quad z^{(0)} = 0
$$

This is called the **initial approximation** or **initial iteration**.

---

## 🔷 Step 3: Iteration 1 ($k=0 \to 1$)

Use the update formulas, plugging in values from the previous iteration ($x=0, y=0, z=0$):

- Compute $x^{(1)}$:  
  $x^{(1)} = \frac{1}{10}(6 - y^{(0)} - z^{(0)}) = \frac{1}{10}(6 - 0 - 0) = 0.6$

- Compute $y^{(1)}$:  
  $y^{(1)} = \frac{1}{10}(6 - x^{(0)} - z^{(0)}) = \frac{1}{10}(6 - 0 - 0) = 0.6$

- Compute $z^{(1)}$:  
  $z^{(1)} = \frac{1}{10}(6 - x^{(0)} - y^{(0)}) = \frac{1}{10}(6 - 0 - 0) = 0.6$

After Iteration 1:  
$$
x = 0.6, \quad y = 0.6, \quad z = 0.6
$$

---

## 🔷 Step 4: Iteration 2 ($k=1 \to 2$)

Plug in $x^{(1)}=y^{(1)}=z^{(1)}=0.6$ into update formulas:

- $x^{(2)} = \frac{1}{10}(6 - 0.6 - 0.6) = \frac{1}{10}(4.8) = 0.48$  
- $y^{(2)} = \frac{1}{10}(6 - 0.6 - 0.6) = 0.48$  
- $z^{(2)} = \frac{1}{10}(6 - 0.6 - 0.6) = 0.48$

Now:  
$$
x = 0.48, \quad y = 0.48, \quad z = 0.48
$$

---

## 🔷 Step 5: Iteration 3 ($k=2 \to 3$)

Use $x^{(2)}=y^{(2)}=z^{(2)}=0.48$:

- $x^{(3)} = \frac{1}{10}(6 - 0.48 - 0.48) = \frac{1}{10}(5.04) = 0.504$  
- $y^{(3)} = 0.504$  
- $z^{(3)} = 0.504$

Now:  
$$
x = y = z = 0.504
$$

---

## 🔷 Step 6: Repeat Until Convergence

Keep repeating the update process. The values approach the true solution with each iteration.

Example values after further iterations:

- Iteration 4: $x = y = z \approx 0.4992$  
- Iteration 5: $x = y = z \approx 0.50016$  
- Iteration 6: $x = y = z \approx 0.49992$  
- ...  
- Final: $x = y = z \to 0.5$

---

## 🔷 Final Solution

The exact solution to the system is:  
$$
x = y = z = 0.5
$$

---

## 🔷 Recap of the Process

1. Isolate each variable in its own equation.  
2. Choose initial guesses for $x, y, z$.  
3. Update each variable using values from the previous iteration.  
4. Repeat until values converge (stop changing significantly).

---

# Gauss-Seidal Method
Great! Now let’s learn the **Gauss-Seidel Method**, which is another **iterative method** to solve a system of linear equations like:

$$
A \vec{x} = \vec{b}
$$

It is **similar to the Jacobi method**, but with one **key difference**:

> **Gauss-Seidel uses the most recently updated values immediately** during each iteration, instead of waiting for the full iteration to finish like Jacobi.

Let’s go step-by-step using the **same example** we used for Jacobi so you can clearly see the difference.

---

## 🔷 Step-by-step Explanation Using an Example

We’ll solve:

$$
\begin{aligned}
10x + y + z &= 6 \quad \text{(Equation 1)} \\
x + 10y + z &= 6 \quad \text{(Equation 2)} \\
x + y + 10z &= 6 \quad \text{(Equation 3)} \\
\end{aligned}
$$

---

## 🔷 Step 1: Rearranging (same as Jacobi)

We isolate the main variable in each equation:

$$
\begin{aligned}
x &= \frac{1}{10}(6 - y - z) \\
y &= \frac{1}{10}(6 - x - z) \\
z &= \frac{1}{10}(6 - x - y) \\
\end{aligned}
$$

These are the update formulas.

---

## 🔷 Step 2: Initial Guess

Let:

$$
x^{(0)} = 0, \quad y^{(0)} = 0, \quad z^{(0)} = 0
$$

---

## 🔷 Step 3: Iteration 1 (k = 0 → 1)

Here's where **Gauss-Seidel differs from Jacobi**:

* In Jacobi, we computed **x₁, y₁, z₁** using only **x₀, y₀, z₀**
* In Gauss-Seidel, we **immediately** use newly computed values

---

### Step-by-step:

1. Compute $x^{(1)}$ using $y^{(0)}$, $z^{(0)}$:

$$
x^{(1)} = \frac{1}{10}(6 - 0 - 0) = 0.6
$$

2. Compute $y^{(1)}$ using **new $x^{(1)}$** and $z^{(0)}$:

$$
y^{(1)} = \frac{1}{10}(6 - 0.6 - 0) = \frac{5.4}{10} = 0.54
$$

3. Compute $z^{(1)}$ using **new $x^{(1)}$, new $y^{(1)}$**:

$$
z^{(1)} = \frac{1}{10}(6 - 0.6 - 0.54) = \frac{4.86}{10} = 0.486
$$

---

### Result after Iteration 1:

$$
x = 0.6, \quad y = 0.54, \quad z = 0.486
$$

Note: Unlike Jacobi, we used **updated values immediately** — that’s the power of Gauss-Seidel.

---

## 🔷 Step 4: Iteration 2 (k = 1 → 2)

Now use the latest values in this order: $x \to y \to z$

1. Compute:

$$
x^{(2)} = \frac{1}{10}(6 - y^{(1)} - z^{(1)}) = \frac{1}{10}(6 - 0.54 - 0.486) = \frac{4.974}{10} = 0.4974
$$

2. Compute:

$$
y^{(2)} = \frac{1}{10}(6 - x^{(2)} - z^{(1)}) = \frac{1}{10}(6 - 0.4974 - 0.486) = \frac{5.0166}{10} = 0.50166
$$

3. Compute:

$$
z^{(2)} = \frac{1}{10}(6 - x^{(2)} - y^{(2)}) = \frac{1}{10}(6 - 0.4974 - 0.50166) = \frac{5.00094}{10} = 0.500094
$$

---

### After Iteration 2:

$$
x = 0.4974, \quad y = 0.50166, \quad z = 0.500094
$$

Much closer to the true value $0.5$ than Jacobi after 2 iterations.

---

## 🔷 Step 5: Iteration 3

Use updated values from Iteration 2:

1. 

$$
x^{(3)} = \frac{1}{10}(6 - y^{(2)} - z^{(2)}) = \frac{1}{10}(6 - 0.50166 - 0.500094) = 0.499025
$$

2.

$$
y^{(3)} = \frac{1}{10}(6 - x^{(3)} - z^{(2)}) = \frac{1}{10}(6 - 0.499025 - 0.500094) = 0.500088
$$

3.

$$
z^{(3)} = \frac{1}{10}(6 - x^{(3)} - y^{(3)}) = \frac{1}{10}(6 - 0.499025 - 0.500088) = 0.5000887
$$

---

### After Iteration 3:

$$
x = 0.499025, \quad y = 0.500088, \quad z = 0.5000887
$$

Converging very quickly.

---

## 🔷 Final Result (after a few more iterations)

You’ll eventually reach:

$$
x = y = z = 0.5
$$

Which is the exact solution of the system.

---

## 🔷 Summary: Jacobi vs Gauss-Seidel

| Feature                | Jacobi                                                                   | Gauss-Seidel                                                                                             |
| ---------------------- | ------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------- |
| Uses old values only   | ✅ Yes                                                                    | ❌ No (uses new values immediately)                                                                       |
| Faster convergence     | ❌ Usually slower                                                         | ✅ Usually faster                                                                                         |
| Can parallelize easily | ✅ Yes                                                                    | ❌ No (has sequential dependency)                                                                         |
| Formula                | $x_i^{(k+1)} = \frac{1}{a_{ii}} (b_i - \sum_{j \ne i} a_{ij} x_j^{(k)})$ | $x_i^{(k+1)} = \frac{1}{a_{ii}} (b_i - \sum_{j < i} a_{ij} x_j^{(k+1)} - \sum_{j > i} a_{ij} x_j^{(k)})$ |

---

## 🔷 When Does Gauss-Seidel Converge?

Just like Jacobi, it converges if:

* The matrix $A$ is **strictly diagonally dominant**, or  
* $A$ is **symmetric positive definite**
