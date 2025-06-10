# 🔷 Power Method: Find Dominant Eigenvalue and Eigenvector

The **Power Method** is one of the simplest and most useful iterative methods in numerical linear algebra. It helps compute the **dominant eigenvalue** (the one with the largest absolute value) and its corresponding **eigenvector** of a matrix.

---

## 🔷 Overview

Given a **square matrix** $A \in \mathbb{R}^{n \times n}$, the **Power Method**:

- Estimates the **dominant eigenvalue** $\lambda_1$, i.e., the eigenvalue with the largest magnitude $|\lambda_1|$
- Finds a corresponding **eigenvector** $\vec{v}_1$

This is very useful when the matrix is large, and you only need the largest eigenvalue/vector pair.

---

## 🔷 Background: What are Eigenvalues and Eigenvectors?

For a square matrix $A$, a scalar $\lambda$ and a non-zero vector $\vec{x}$ are said to be an **eigenvalue** and **eigenvector** of $A$ if:

$$
A \vec{x} = \lambda \vec{x}
$$

In words:

- $\vec{x}$ is scaled (not rotated) by the transformation $A$
- $\lambda$ is the scaling factor

---

## 🔷 Power Method Algorithm (Step-by-step)

Suppose $A$ has $n$ linearly independent eigenvectors and eigenvalues $\lambda_1, \lambda_2, \dots, \lambda_n$, with:

$$
|\lambda_1| > |\lambda_2| \geq |\lambda_3| \geq \dots \geq |\lambda_n|
$$

We want to find $\lambda_1$ and its eigenvector $\vec{v}_1$.

---

### 🧮 Step 1: Choose an initial vector

Pick any non-zero vector $\vec{x}^{(0)}$.  
Usually, a random vector or even $\vec{x}^{(0)} = [1, 1, 1, \dots]^T$ is fine.

---

### 🧮 Step 2: Iterative multiplication

We compute the next vector:

$$
\vec{x}^{(k+1)} = A \vec{x}^{(k)}
$$

Then normalize it to prevent it from growing too large:

$$
\vec{x}^{(k+1)} = \frac{A \vec{x}^{(k)}}{\| A \vec{x}^{(k)} \|}
$$

Repeat this process until the vector converges (i.e., its direction stabilizes).

---

### 🧮 Step 3: Estimate the eigenvalue

Once you have a good approximation $\vec{x}^{(k)}$, compute the **Rayleigh Quotient** to estimate the eigenvalue:

$$
\lambda^{(k)} = \frac{ \vec{x}^{(k)^T} A \vec{x}^{(k)} }{ \vec{x}^{(k)^T} \vec{x}^{(k)} }
$$

This gives you the approximate **dominant eigenvalue** $\lambda_1$.

---

## 🔷 Why Does This Work?

Suppose your initial vector $\vec{x}^{(0)}$ can be written as a linear combination of eigenvectors:

$$
\vec{x}^{(0)} = c_1 \vec{v}_1 + c_2 \vec{v}_2 + \dots + c_n \vec{v}_n
$$

Then:

$$
A^k \vec{x}^{(0)} = c_1 \lambda_1^k \vec{v}_1 + c_2 \lambda_2^k \vec{v}_2 + \dots + c_n \lambda_n^k \vec{v}_n
$$

As $k \to \infty$, the term with $\lambda_1^k \vec{v}_1$ dominates (since $|\lambda_1| > |\lambda_i|$ for $i > 1$). So:

$$
\vec{x}^{(k)} \to \vec{v}_1
$$

And the direction of $\vec{x}^{(k)}$ becomes that of the dominant eigenvector.

---

## 🔷 Example

Let’s consider the matrix:

$$
A =
\begin{bmatrix}
2 & 1 \\
1 & 3
\end{bmatrix}
$$

We want to use the Power Method to find the dominant eigenvalue and eigenvector.

---

### Step 1: Choose initial vector

Let:

$$
\vec{x}^{(0)} = \begin{bmatrix} 1 \\ 1 \end{bmatrix}
$$

---

### Step 2: First iteration

$$
\vec{x}^{(1)} = A \vec{x}^{(0)} =
\begin{bmatrix}
2 & 1 \\
1 & 3
\end{bmatrix}
\begin{bmatrix}
1 \\
1
\end{bmatrix}
=
\begin{bmatrix}
3 \\
4
\end{bmatrix}
$$

Normalize it (e.g., divide by max entry):

$$
\vec{x}^{(1)} = \frac{1}{4} \begin{bmatrix} 3 \\ 4 \end{bmatrix} = \begin{bmatrix} 0.75 \\ 1 \end{bmatrix}
$$

---

### Step 3: Second iteration

$$
\vec{x}^{(2)} = A \vec{x}^{(1)} =
\begin{bmatrix}
2 & 1 \\
1 & 3
\end{bmatrix}
\begin{bmatrix}
0.75 \\
1
\end{bmatrix}
=
\begin{bmatrix}
2.5 \\
3.75
\end{bmatrix}
$$

Normalize:

$$
\vec{x}^{(2)} = \frac{1}{3.75} \begin{bmatrix} 2.5 \\ 3.75 \end{bmatrix} = \begin{bmatrix} 0.6667 \\ 1 \end{bmatrix}
$$

---

### Step 4: Third iteration

$$
\vec{x}^{(3)} = A \vec{x}^{(2)} =
\begin{bmatrix}
2 & 1 \\
1 & 3
\end{bmatrix}
\begin{bmatrix}
0.6667 \\
1
\end{bmatrix}
=
\begin{bmatrix}
2.3333 \\
3.6667
\end{bmatrix}
$$

Normalize:

$$
\vec{x}^{(3)} = \frac{1}{3.6667} \begin{bmatrix} 2.3333 \\ 3.6667 \end{bmatrix} = \begin{bmatrix} 0.636 \\ 1 \end{bmatrix}
$$

We see the vector is stabilizing around $\vec{v}_1 \approx [0.618, 1]$.

---

### Step 5: Estimate dominant eigenvalue (Rayleigh Quotient)

Compute:

$$
\lambda^{(3)} = \frac{ \vec{x}^{(3)^T} A \vec{x}^{(3)} }{ \vec{x}^{(3)^T} \vec{x}^{(3)} }
$$

Using $\vec{x}^{(3)} \approx \begin{bmatrix} 0.636 \\ 1 \end{bmatrix}$:

- $A\vec{x}^{(3)} \approx \begin{bmatrix} 2.272 \\ 3.636 \end{bmatrix}$
- $\vec{x}^{(3)^T} A \vec{x}^{(3)} \approx 0.636 \cdot 2.272 + 1 \cdot 3.636 \approx 5.08$
- $\vec{x}^{(3)^T} \vec{x}^{(3)} = 0.636^2 + 1^2 \approx 1.405$

So:

$$
\lambda \approx \frac{5.08}{1.405} \approx 3.615
$$

Which is close to the **actual dominant eigenvalue** $\lambda_1 = 3.618$.

---

## 🔷 What is the Rayleigh Quotient?

The **Rayleigh Quotient** is a formula used to estimate the eigenvalue associated with a given vector $\vec{x}$:

$$
R(\vec{x}) = \frac{ \vec{x}^T A \vec{x} }{ \vec{x}^T \vec{x} }
$$

If $\vec{x}$ is an exact eigenvector of $A$, then:

$$
R(\vec{x}) = \lambda
$$

If $\vec{x}$ is an **approximate** eigenvector, $R(\vec{x})$ gives a very **good estimate** of the corresponding eigenvalue.

---

## 🔷 When Does the Power Method Work?

✅ It works when:

- The matrix has a **dominant eigenvalue** $|\lambda_1| > |\lambda_2|$
- The initial guess has a component in the direction of $\vec{v}_1$ (almost always the case)

❌ It fails or converges slowly if:

- $|\lambda_1| \approx |\lambda_2|$
- The dominant eigenvalue is **complex**

---

## 🔷 Summary Table

| Concept                 | Description                                                                                   |
|------------------------|-----------------------------------------------------------------------------------------------|
| **Power Method**        | Iteratively multiplies a matrix by a vector to converge to the dominant eigenvector          |
| **Rayleigh Quotient**   | $\frac{\vec{x}^T A \vec{x}}{\vec{x}^T \vec{x}}$ — used to estimate the eigenvalue from a vector |
| **Dominant Eigenvalue** | The eigenvalue with the largest absolute value                                               |
| **Convergence**         | Rapid if $|\lambda_1| \gg |\lambda_2|$                                                       |

---

# Rayleigh Quotient in detail

### 🔁 Recap of Where We Left Off

We were using the Power Method on the matrix:

$$
A =
\begin{bmatrix}
2 & 1 \\
1 & 3 \\
\end{bmatrix}
$$

And after a few iterations, we had an approximate eigenvector:

$$
\vec{x}^{(3)} =
\begin{bmatrix}
0.636 \\
1 \\
\end{bmatrix}
$$

We want to compute the **Rayleigh Quotient**:

$$
\lambda \approx \frac{\vec{x}^T A \vec{x}}{\vec{x}^T \vec{x}}
$$

---

## 🔷 Step-by-Step Calculation

### Step 1: Multiply $A \vec{x}$

We compute:

$$
A \vec{x} =
\begin{bmatrix}
2 & 1 \\
1 & 3 \\
\end{bmatrix}
\begin{bmatrix}
0.636 \\
1 \\
\end{bmatrix}
=
\begin{bmatrix}
2 \cdot 0.636 + 1 \cdot 1 \\
1 \cdot 0.636 + 3 \cdot 1 \\
\end{bmatrix}
=
\begin{bmatrix}
1.272 + 1 \\
0.636 + 3 \\
\end{bmatrix}
=
\begin{bmatrix}
2.272 \\
3.636 \\
\end{bmatrix}
$$

---

### Step 2: Compute numerator $\vec{x}^T A \vec{x}$

This is the **dot product** of $\vec{x}$ and $A \vec{x}$:

$$
\vec{x}^T A \vec{x} = 0.636 \cdot 2.272 + 1 \cdot 3.636
$$

Calculate each term:

- $0.636 \cdot 2.272 \approx 1.445$
- $1 \cdot 3.636 = 3.636$

So:

$$
\vec{x}^T A \vec{x} \approx 1.445 + 3.636 = 5.081
$$

---

### Step 3: Compute denominator $\vec{x}^T \vec{x}$

This is the **norm squared** (dot product of the vector with itself):

$$
\vec{x}^T \vec{x} = 0.636^2 + 1^2 = 0.4045 + 1 = 1.4045
$$

---

### Step 4: Final Rayleigh Quotient

Now compute:

$$
\lambda \approx \frac{5.081}{1.4045} \approx 3.616
$$

✅ This is a **very good approximation** of the true dominant eigenvalue, which (for this matrix) is exactly:

$$
\lambda_1 = \frac{5 + \sqrt{5}}{2} \approx 3.618
$$

---

## ✅ Final Result

- **Approximate eigenvalue** (via Rayleigh Quotient): $\lambda \approx 3.616$
- **Approximate eigenvector**: $\vec{v} \approx [0.636, 1]$
