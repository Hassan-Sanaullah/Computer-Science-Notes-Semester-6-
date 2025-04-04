# Bisection Method

The **Bisection Method** is a simple and effective root-finding technique for solving equations of the form:  
$$f(x) = 0$$

It is a **bracketing method**, which means it requires an interval $[a, b]$ where the function has opposite signs at the endpoints, i.e.,  
$$f(a) \times f(b) < 0$$

This condition guarantees that there is at least one root between $a$ and $b$ (according to the **Intermediate Value Theorem**). The method then proceeds by repeatedly bisecting the interval and narrowing down the location of the root.

## Step-by-Step Procedure:

1. **Choose an initial interval $[a, b]$:**

   - You need to select two initial points $a$ and $b$ such that:
     - $f(a) \times f(b) < 0$, meaning the function takes opposite signs at $a$ and $b$.

2. **Calculate the midpoint:**

   - Find the midpoint $m$ of the interval $[a, b]$ as:  
     $$m = \frac{(a + b)}{2}$$

3. **Evaluate the function at the midpoint:**

   - Calculate $f(m)$

3. **Check the sign of $f(m)$:**

   - If $f(m) = 0$, then $m$ is the root, and the method stops.
   - If $f(m)$ and $f(a)$ have opposite signs, then the root lies between $a$ and $m$. Set $b = m$.
   - If $f(m)$ and $f(b)$ have opposite signs, then the root lies between $m$ and $b$. Set $a = m$.

 **When to Replace Values in the Bisection Method**

- If $f(m) = 0$:  
  You’ve found the exact root. You can stop here.

- If $f(a) \cdot f(m) < 0$:  
  ➤ The root lies between $a$ and $m$, so you replace $b$ with $m$:  
$$
  b = m
 $$

- If $f(m) \cdot f(b) < 0$:  
  ➤ The root lies between $m$ and $b$, so you replace $a$ with $m$:  
$$
  a = m
 $$


5. **Repeat the process:**

   - Repeat the steps until the interval $[a, b]$ is sufficiently small, i.e., $|b - a|$ is smaller than a given tolerance $ε$, or the value of $f(m)$ is close enough to 0.

6. **Final Approximation:**

   - The midpoint $m$ is the best approximation of the root after the specified number of iterations or once the stopping criteria are met.
## Example:
### Solving $f(x) = x^3 - x - 2 = 0$ using the Bisection Method (3 Iterations)

---

### Step 1: Choose the interval $[a, b]$

We need to find $a$ and $b$ such that:

$$
f(a) \times f(b) < 0
$$

Try $a = 1$, $b = 2$:

$$
f(1) = 1^3 - 1 - 2 = -2 
$$
$$
f(2) = 2^3 - 2 - 2 = 4
$$

Since $f(1) \times f(2) = -2 \times 4 = -8 < 0$, the interval is valid.

✅ Initial interval: $[1, 2]$

---

### Iteration 1:

$$
a = 1, \quad b = 2
$$

Midpoint:

$$
m_1 = \frac{1 + 2}{2} = 1.5
$$

Evaluate:

$$
f(1.5) = (1.5)^3 - 1.5 - 2 = 3.375 - 1.5 - 2 = -0.125
$$

Since $f(1) < 0$ and $f(1.5) < 0$, both are negative.

New interval:

$$
[1.5, 2]
$$

---

### Iteration 2:

$$
a = 1.5, \quad b = 2
$$

Midpoint:

$$
m_2 = \frac{1.5 + 2}{2} = 1.75
$$

Evaluate:

$$
f(1.75) = (1.75)^3 - 1.75 - 2 = 5.359375 - 1.75 - 2 = 1.609375
$$

Now $f(1.5) = -0.125$, $f(1.75) = 1.609375$, so signs are opposite.

New interval:

$$
[1.5, 1.75]
$$

---

### Iteration 3:

$$
a = 1.5, \quad b = 1.75
$$

Midpoint:

$$
m_3 = \frac{1.5 + 1.75}{2} = 1.625
$$

Evaluate:

$$
f(1.625) = (1.625)^3 - 1.625 - 2 = 4.29 - 1.625 - 2 = 0.640625
$$

Now $f(1.5) = -0.125$, $f(1.625) = 0.640625$, signs are opposite.

New interval:

$$
[1.5, 1.625]
$$

---

### Final Result after 3 Iterations:

The root lies in the interval:

$$
[1.5, 1.625]
$$

The approximate root after 3 iterations is:

$$
\boxed{1.625}
$$
# Fixed Point Iteration Method

### Goal

To solve a nonlinear equation of the form:  
$$f(x) = 0$$

We rearrange it into:  
$$x = g(x)$$

Then, we apply iteration to get successively better approximations of the root.  
We're trying to find a value $x$ where:  
$$x = g(x)$$

This value is called the **fixed point**, and it's also a solution to the original equation.

---

### Why Are There Many $g(x)$ Forms?

Because there are many ways to algebraically rearrange $f(x) = 0$ into $x = g(x)$.

---

### Example:

Suppose you are solving:  
$$f(x) = x^3 + x - 1 = 0$$

Here are some different ways to rearrange this into $x = g(x)$:

1. $$x = 1 - x^3 \Rightarrow g(x) = 1 - x^3$$  
2. $$x = \sqrt[3]{1 - x} \Rightarrow g(x) = \sqrt[3]{1 - x}$$ 
3. $$x = \frac{1}{1 + x^2} \Rightarrow g(x) = \frac{1}{1 + x^2}$$

All of these are valid rearrangements — but **not all will converge** when used in iteration.

---

### How to Choose the Right $g(x)$

The convergence depends on the **derivative** of $g(x)$. Specifically:

### Convergence Condition:

$|g'(x)| < 1$ near the root

If this condition is satisfied, then the fixed-point iteration will converge.  
If $|g'(x)| > 1$, the iterations will diverge.

---

## Step-by-Step Procedure

### Step 1: Rearrange $f(x) = 0$ into $x = g(x)$

Choose a form of $g(x)$ such that $|g'(x)| < 1$ near the expected root.

---

### Step 2: Choose Initial Guess $x_0$

Select a value close to where you think the root is (based on a graph, table, or context).

---

### Step 3: Apply the Iteration Rule

$$x_{n+1} = g(x_n)$$

Repeat the process:  
$$x_1 = g(x_0)$$  
$$x_2 = g(x_1)$$  
$$x_3 = g(x_2)$$  
$$\vdots$$
## Example: Fixed Point Iteration Method with Multiple $g(x)$ Forms

### Given Equation:

Solve the equation:  
$f(x) = x^3 - 4x - 9 = 0$

We will explore different rearrangements of this equation and apply the Fixed Point Iteration Method to each one. The goal is to identify the correct form for convergence.

---

### **Step 1: Rearrange $f(x) = 0$ into Multiple Forms of $g(x)$**

#### Rearrangement 1:

$$
x = \frac{4x + 9}{x^2}
$$

So, the first $g(x)$ is:  
$$
g_1(x) = \frac{4x + 9}{x^2}
$$

#### Rearrangement 2:

$$
x = \frac{x^3 - 9}{4}
$$

So, the second $g(x)$ is:  
$$
g_2(x) = \frac{x^3 - 9}{4}
$$

#### Rearrangement 3:

$$
x = \frac{9 + 4x}{x^2}
$$

So, the third $g(x)$ is:  
$$
g_3(x) = \frac{9 + 4x}{x^2}
$$

---

### **Step 2: Choose an Initial Guess $x_0$**

Let’s start with an initial guess $x_0 = 3$ for all three cases, which is close to the expected root.

---

### **Step 3: Check the Convergence Condition**

To choose the correct form of $g(x)$, we need to check if $|g'(x)| < 1$ near the root. This ensures that the iteration will converge.

#### **For $g_1(x) = \frac{4x + 9}{x^2}$:**

Find the derivative $g_1'(x)$:

$$
g_1'(x) = \frac{d}{dx} \left( \frac{4x + 9}{x^2} \right) = \frac{2x(4x + 9) - (4x + 9)2x}{x^4} = \frac{-2x^2 + 9}{x^4}
$$

Check the magnitude of $g_1'(x)$ near the expected root $x \approx 3$:

$$
g_1'(3) = \frac{-2(3)^2 + 9}{(3)^4} = \frac{-18 + 9}{81} = \frac{-9}{81} = -\frac{1}{9} \approx -0.1111
$$

Since $|g_1'(3)| = 0.1111 < 1$, this form satisfies the convergence condition.

#### **For $g_2(x) = \frac{x^3 - 9}{4}$:**

Find the derivative $g_2'(x)$:

$$
g_2'(x) = \frac{d}{dx} \left( \frac{x^3 - 9}{4} \right) = \frac{3x^2}{4}
$$

Check the magnitude of $g_2'(x)$ near $x = 3$:

$$
g_2'(3) = \frac{3(3)^2}{4} = \frac{3 \times 9}{4} = \frac{27}{4} = 6.75
$$

Since $|g_2'(3)| = 6.75 > 1$, this form **does not** satisfy the convergence condition. Therefore, **do not use this $g(x)$**.

#### **For $g_3(x) = \frac{9 + 4x}{x^2}$:**

Find the derivative $g_3'(x)$:

$$
g_3'(x) = \frac{d}{dx} \left( \frac{9 + 4x}{x^2} \right) = \frac{x^2(4) - (9 + 4x)(2x)}{x^4}
$$

Simplifying:

$$
g_3'(x) = \frac{4x^2 - 2x(9 + 4x)}{x^4} = \frac{4x^2 - 18x - 8x^2}{x^4} = \frac{-4x^2 - 18x}{x^4} = \frac{-2x^2 - 9x}{x^3}
$$

Check the magnitude of $g_3'(x)$ near $x = 3$:

$$
g_3'(3) = \frac{-2(3)^2 - 9(3)}{(3)^3} = \frac{-18 - 27}{27} = \frac{-45}{27} = -\frac{5}{3} \approx -1.6667
$$

Since $|g_3'(3)| = 1.6667 > 1$, this form **does not** satisfy the convergence condition. Therefore, **do not use this $g(x)$** either.

---

### **Step 4: Apply Fixed Point Iteration using $g_1(x)$**

Since $g_1(x)$ is the only form that satisfies the convergence condition, we will proceed with it.

We’ll use the iteration formula:

$$
x_{n+1} = g_1(x_n) = \frac{4x_n + 9}{x_n^2}
$$

Starting with $x_0 = 3$:

---

### **Iteration 1:**

$$
x_1 = g_1(x_0) = \frac{4(3) + 9}{(3)^2} = \frac{12 + 9}{9} = \frac{21}{9} = 2.3333
$$

---

### **Iteration 2:**

$$
x_2 = g_1(x_1) = \frac{4(2.3333) + 9}{(2.3333)^2} = \frac{9.3332 + 9}{5.4444} \approx \frac{18.3332}{5.4444} \approx 3.368
$$

---

### **Iteration 3:**

$$
x_3 = g_1(x_2) = \frac{4(3.368) + 9}{(3.368)^2} = \frac{13.472 + 9}{11.33} = \frac{22.472}{11.33} \approx 1.981
$$

---

### **Summary of Iterations:**

- Initial guess: $x_0 = 3$
- After 1st iteration: $x_1 \approx 2.3333$
- After 2nd iteration: $x_2 \approx 3.368$
- After 3rd iteration: $x_3 \approx 1.981$

---

### **Conclusion:**

- We have successfully chosen the form $g_1(x) = \frac{4x + 9}{x^2}$ for the **Fixed Point Iteration Method** since it satisfies the convergence condition.
- After 3 iterations, the method is bringing us closer to the root, but we need more iterations for better accuracy.

---

Would you like me to continue iterating or analyze further?
### In **fixed-point iteration**, you **always replace $x$** with the result from the **previous iteration**

# Secant Method

### Goal:

To find the root of a nonlinear equation:

$$f(x) = 0$$

The Secant Method is an iterative root-finding method similar to Newton-Raphson, but it **doesn't require the derivative** of the function. Instead, it approximates the derivative using the **slope of a secant line** through two previous points.

---

### Idea Behind It:

Instead of using the tangent (like Newton-Raphson), we use the secant line between two points 
$(x_{n-1}, f(x_{n-1}))$ and $(x_n, f(x_n))$ to estimate the next root:

$$
x_{n+1} = x_n - \frac{f(x_n)(x_n - x_{n-1})}{f(x_n) - f(x_{n-1})}
$$

---

###  Step-by-Step Procedure:

1. **Choose two initial guesses:**  
   Pick $x_0$ and $x_1$, ideally close to the root.

2. **Apply the iteration formula:**  
   Use:
   $$
   x_{n+1} = x_n - \frac{f(x_n)(x_n - x_{n-1})}{f(x_n) - f(x_{n-1})}
   $$

3. **Repeat:**  
   For each step, replace:

   - $x_{n-1} \leftarrow x_n$
   - $x_n \leftarrow x_{n+1}$

   Then compute the next value.

4. **Stop when:**  
   Either:

   - $|x_{n+1} - x_n| < \varepsilon$ (tolerance), or  
   - $|f(x_{n+1})|$ is small enough

---

###  When Do You Replace $x$, and With What?

At every iteration:

- After computing $x_{n+1}$, you shift values to prepare for the next round:
  - $x_{n-1} \leftarrow x_n$
  - $x_n \leftarrow x_{n+1}$

You **always need two previous values** to compute the next one — that’s what makes it the **secant** method.

## Secant Method Example (3 Iterations)

### Problem:

Find a root of the equation:  
$$
f(x) = x^2 - 2
$$

We know that the square root of 2 is approximately 1.4142, so we expect the root to be near that.

---

### Step 1: Choose Initial Guesses

Let:
- $x_0 = 1$
- $x_1 = 2$

Compute $f(x_0)$ and $f(x_1)$:

- $f(1) = 1^2 - 2 = -1$
- $f(2) = 2^2 - 2 = 2$

---

### Step 2: Apply the Secant Formula

#### Iteration 1:

$$
x_2 = x_1 - \frac{f(x_1)(x_1 - x_0)}{f(x_1) - f(x_0)} = 2 - \frac{2(2 - 1)}{2 - (-1)} = 2 - \frac{2}{3} = \frac{4}{3} \approx 1.3333
$$

---

####  Iteration 2:

Let:
- $x_0 = 2$
- $x_1 = 1.3333$

Compute:
- $f(1.3333) = (1.3333)^2 - 2 \approx 1.7778 - 2 = -0.2222$
- $f(2) = 4 - 2 = 2$

Then:
$$
x_3 = x_1 - \frac{f(x_1)(x_1 - x_0)}{f(x_1) - f(x_0)} = 1.3333 - \frac{-0.2222(1.3333 - 2)}{-0.2222 - 2}
$$

Simplify:
$$
x_3 = 1.3333 - \frac{-0.2222(-0.6667)}{-2.2222} = 1.3333 - \frac{0.1481}{-2.2222} \approx 1.3333 + 0.0667 = 1.4
$$

---

#### Iteration 3:

Let:
- $x_0 = 1.3333$
- $x_1 = 1.4$

Compute:
- $f(1.4) = (1.4)^2 - 2 = 1.96 - 2 = -0.04$
- $f(1.3333) \approx -0.2222$ (from earlier)

Then:
$$
x_4 = x_1 - \frac{f(x_1)(x_1 - x_0)}{f(x_1) - f(x_0)} = 1.4 - \frac{-0.04(1.4 - 1.3333)}{-0.04 - (-0.2222)}
$$

Simplify:
$$
x_4 = 1.4 - \frac{-0.04(0.0667)}{0.1822} \approx 1.4 + 0.0147 = 1.4147
$$

---

###  Final Result after 3 Iterations:

Approximate root:  
$$
x_4 \approx 1.4147
$$

Which is very close to the true value $\sqrt{2} \approx 1.4142$


#  Newton-Raphson Method

###  Goal:

To find a root of a nonlinear equation:

$$
f(x) = 0
$$

The **Newton-Raphson method** is a powerful and fast-converging iterative method that uses both the function and its derivative to find roots.

---

### Idea Behind It:

It starts from an initial guess $x_0$ and uses the **tangent line** at $x_0$ to approximate the root.

The formula for the next iteration is:

$$
x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}
$$

This formula is derived from the equation of the tangent line at $(x_n, f(x_n))$ and setting it equal to zero to find where the tangent crosses the x-axis.

---

### Step-by-Step Procedure:

1. **Choose an initial guess:**  
   Pick a starting point $x_0$ near the expected root.

2. **Apply the Newton-Raphson iteration formula:**  
   $$
   x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}
   $$

3. **Repeat until convergence:**  
   Stop when either:
   - $|x_{n+1} - x_n| < \varepsilon$ (a small tolerance), or
   - $|f(x_{n+1})|$ is very small (close to 0)

---

###  When Do You Replace $x$, and With What?

At every iteration:

- After calculating $x_{n+1}$, you **replace**:
  - $x_n \leftarrow x_{n+1}$
- Then repeat the formula using the updated $x_n$

So the value of $x$ is **always updated to the latest approximation** from the formula.

## Newton-Raphson Method Example (3 Iterations)

###  Goal:

Find a root of the equation:
$$
f(x) = x^2 - 2
$$

This equation has a known root at $\sqrt{2} \approx 1.4142$

---

### Step 1: Compute the Derivative

We need both $f(x)$ and $f'(x)$:

- $f(x) = x^2 - 2$
- $f'(x) = 2x$

---

### Step 2: Choose an Initial Guess

Let:
$$
x_0 = 1.5
$$

---

### Iteration 1:

Apply the Newton-Raphson formula:
$$
x_1 = x_0 - \frac{f(x_0)}{f'(x_0)} = 1.5 - \frac{(1.5)^2 - 2}{2 \cdot 1.5}
$$

Compute:
- $f(1.5) = 2.25 - 2 = 0.25$
- $f'(1.5) = 3$

So:
$$
x_1 = 1.5 - \frac{0.25}{3} = 1.5 - 0.0833 = 1.4167
$$

---

### Iteration 2:

Now use $x_1 = 1.4167$

$$
x_2 = x_1 - \frac{f(x_1)}{f'(x_1)} = 1.4167 - \frac{(1.4167)^2 - 2}{2 \cdot 1.4167}
$$

Compute:
- $f(1.4167) \approx 2.0069 - 2 = 0.0069$
- $f'(1.4167) \approx 2.8334$

So:
$$
x_2 = 1.4167 - \frac{0.0069}{2.8334} \approx 1.4167 - 0.0024 = 1.4143
$$

---

### Iteration 3:

Now use $x_2 = 1.4143$

$$
x_3 = x_2 - \frac{f(x_2)}{f'(x_2)} = 1.4143 - \frac{(1.4143)^2 - 2}{2 \cdot 1.4143}
$$

Compute:
- $f(1.4143) \approx 2.000007 - 2 = 0.000007$
- $f'(1.4143) \approx 2.8286$

So:
$$
x_3 = 1.4143 - \frac{0.000007}{2.8286} \approx 1.4143 - 0.0000025 = 1.4142
$$

---

### Final Approximation After 3 Iterations:

$$
x_3 \approx 1.4142
$$

Which is very close to the actual value of $\sqrt{2}$

#  Regula Falsi Method (False Position):

###  Goal

To find the root of a nonlinear equation:

$$
f(x) = 0
$$

This method is similar to the **Bisection Method** in that it starts with two points $a$ and $b$ such that:

$$
f(a) \cdot f(b) < 0
$$

This means the function has **opposite signs** at $a$ and $b$, so there is at least one root between them (by the Intermediate Value Theorem).

---

###  Idea Behind It

Unlike the Bisection Method, which takes the midpoint, Regula Falsi uses **linear interpolation** between $a$ and $b$ to guess the root more accurately.

#### Formula for Next Approximation:

Let $c$ be the next approximation. Then:

$$
c = b - \frac{f(b)(b - a)}{f(b) - f(a)}
$$

This formula comes from the x-intercept of the line joining the points $(a, f(a))$ and $(b, f(b))$ — that is, the **secant line**.

---

###  Step-by-Step Procedure

1. **Choose initial interval** $[a, b]$ such that:

   $$
   f(a) \cdot f(b) < 0
   $$

2. **Calculate the next approximation** using:

   $$
   c = b - \frac{f(b)(b - a)}{f(b) - f(a)}
   $$

3. **Evaluate $f(c)$** and check:

   - If $f(c) = 0$, then $c$ is the root.
   - If $f(c) \cdot f(a) < 0$, the root lies between $a$ and $c$, so **replace** $b$ with $c$.
   - If $f(c) \cdot f(b) < 0$, the root lies between $c$ and $b$, so **replace** $a$ with $c$.

4. **Repeat** the process until convergence (i.e., $|f(c)|$ is small or $|b - a| < \varepsilon$).

---

###  When Do You Replace $x$, and With What?

After each iteration:

- If $f(c) \cdot f(a) < 0$, then set:

  $$
  b \leftarrow c
  $$

- If $f(c) \cdot f(b) < 0$, then set:

  $$
  a \leftarrow c
  $$

**You never replace both** $a$ and $b$ in the same iteration — only one side is updated depending on where the sign change occurs.

---

###  Advantages

- Generally faster than Bisection Method
- Doesn’t require the derivative like Newton-Raphson

---

###  Drawbacks

- Can converge slowly if one side of the interval doesn't move (can "stall" if $f(a)$ or $f(b)$ stays close to 0).

---

Let me know if you'd like an example with 3 iterations too!
