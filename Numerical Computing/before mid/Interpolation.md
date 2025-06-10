# Lagrange Interpolation Method

Lagrange interpolation is a method for constructing a polynomial that passes through a given set of points. This method is especially useful when you have data points and want to find a polynomial that fits all of them exactly. 

#### **Overview:**
Given a set of$n+1$data points$(x_0, y_0), (x_1, y_1), \dots, (x_n, y_n)$, Lagrange interpolation constructs the polynomial of degree at most$n$that passes through all these points.

### **Lagrange Interpolation Polynomial Formula**

The Lagrange interpolation polynomial$P(x)$is given by:

$$
P(x) = \sum_{i=0}^{n} L_i(x) y_i
$$

Where:

-$y_i$is the value of the function at the point$x_i$,
-$L_i(x)$is the Lagrange basis polynomial for the$i$-th point, which is defined as:

$$
L_i(x) = \prod_{\substack{0 \leq j \leq n \\ j \neq i}} \frac{x - x_j}{x_i - x_j}
$$

This product is over all$j$from 0 to$n$, excluding$i$. The Lagrange basis polynomial$L_i(x)$is constructed such that$L_i(x_j) = 1$when$i = j$, and$L_i(x_j) = 0$for$i \neq j$. This property ensures that the polynomial$P(x)$interpolates the given points exactly.

### **Steps to Construct the Polynomial:**

1. **Identify the data points:** You need$n+1$data points$(x_0, y_0), (x_1, y_1), \dots, (x_n, y_n)$.

2. **Construct the Lagrange basis polynomials$L_i(x)$:** For each$i$from 0 to$n$, calculate the Lagrange basis polynomial$L_i(x)$. This involves computing the product for each point, excluding$x_i$.

3. **Sum the contributions of each basis polynomial:** The polynomial$P(x)$is a weighted sum of the basis polynomials, with each basis polynomial multiplied by the corresponding$y_i$value.

### **Examples:**

#### **Linear Polynomial (Degree 1)**

For 2 points$(x_0, y_0)$and$(x_1, y_1)$, the linear Lagrange interpolation polynomial is given by:

$$
P(x) = L_0(x) y_0 + L_1(x) y_1
$$

Where:

-$L_0(x) = \frac{x - x_1}{x_0 - x_1}$
-$L_1(x) = \frac{x - x_0}{x_1 - x_0}$

Thus, the linear Lagrange polynomial is:

$$
P(x) = \frac{x - x_1}{x_0 - x_1} y_0 + \frac{x - x_0}{x_1 - x_0} y_1
$$

#### **Quadratic Polynomial (Degree 2)**

For 3 points$(x_0, y_0)$,$(x_1, y_1)$, and$(x_2, y_2)$, the quadratic Lagrange interpolation polynomial is given by:

$$
P(x) = L_0(x) y_0 + L_1(x) y_1 + L_2(x) y_2
$$

Where:

-$L_0(x) = \frac{(x - x_1)(x - x_2)}{(x_0 - x_1)(x_0 - x_2)}$
-$L_1(x) = \frac{(x - x_0)(x - x_2)}{(x_1 - x_0)(x_1 - x_2)}$
-$L_2(x) = \frac{(x - x_0)(x - x_1)}{(x_2 - x_0)(x_2 - x_1)}$

Thus, the quadratic Lagrange polynomial is:

$$
P(x) = \frac{(x - x_1)(x - x_2)}{(x_0 - x_1)(x_0 - x_2)} y_0 + \frac{(x - x_0)(x - x_2)}{(x_1 - x_0)(x_1 - x_2)} y_1 + \frac{(x - x_0)(x - x_1)}{(x_2 - x_0)(x_2 - x_1)} y_2
$$

#### **Cubic Polynomial (Degree 3)**

For 4 points$(x_0, y_0)$,$(x_1, y_1)$,$(x_2, y_2)$, and$(x_3, y_3)$, the cubic Lagrange interpolation polynomial is given by:

$$
P(x) = L_0(x) y_0 + L_1(x) y_1 + L_2(x) y_2 + L_3(x) y_3
$$

Where:

-$L_0(x) = \frac{(x - x_1)(x - x_2)(x - x_3)}{(x_0 - x_1)(x_0 - x_2)(x_0 - x_3)}$
-$L_1(x) = \frac{(x - x_0)(x - x_2)(x - x_3)}{(x_1 - x_0)(x_1 - x_2)(x_1 - x_3)}$
-$L_2(x) = \frac{(x - x_0)(x - x_1)(x - x_3)}{(x_2 - x_0)(x_2 - x_1)(x_2 - x_3)}$
-$L_3(x) = \frac{(x - x_0)(x - x_1)(x - x_2)}{(x_3 - x_0)(x_3 - x_1)(x_3 - x_2)}$

Thus, the cubic Lagrange polynomial is:

$$
P(x) = \frac{(x - x_1)(x - x_2)(x - x_3)}{(x_0 - x_1)(x_0 - x_2)(x_0 - x_3)} y_0 + \frac{(x - x_0)(x - x_2)(x - x_3)}{(x_1 - x_0)(x_1 - x_2)(x_1 - x_3)} y_1 + \frac{(x - x_0)(x - x_1)(x - x_3)}{(x_2 - x_0)(x_2 - x_1)(x_2 - x_3)} y_2 + \frac{(x - x_0)(x - x_1)(x - x_2)}{(x_3 - x_0)(x_3 - x_1)(x_3 - x_2)} y_3
$$

### **Summary of Key Formulae:**

1. **Linear (Degree 1):**
  $$P(x) = \frac{x - x_1}{x_0 - x_1} y_0 + \frac{x - x_0}{x_1 - x_0} y_1$$

2. **Quadratic (Degree 2):**
  $$P(x) = \frac{(x - x_1)(x - x_2)}{(x_0 - x_1)(x_0 - x_2)} y_0 + \frac{(x - x_0)(x - x_2)}{(x_1 - x_0)(x_1 - x_2)} y_1 + \frac{(x - x_0)(x - x_1)}{(x_2 - x_0)(x_2 - x_1)} y_2$$

3. **Cubic (Degree 3):**
  $$P(x) = \frac{(x - x_1)(x - x_2)(x - x_3)}{(x_0 - x_1)(x_0 - x_2)(x_0 - x_3)} y_0 + \frac{(x - x_0)(x - x_2)(x - x_3)}{(x_1 - x_0)(x_1 - x_2)(x_1 - x_3)} y_1 + \frac{(x - x_0)(x - x_1)(x - x_3)}{(x_2 - x_0)(x_2 - x_1)(x_2 - x_3)} y_2 + \frac{(x - x_0)(x - x_1)(x - x_2)}{(x_3 - x_0)(x_3 - x_1)(x_3 - x_2)} y_3$$

This method can be extended to higher degrees, but the principle remains the same: construct the Lagrange basis polynomials for each data point, and then sum them up weighted by the function values$y_i$.

### Example: Lagrange Interpolation

Given the data points:

-$(x_0, y_0) = (1, 2)$
-$(x_1, y_1) = (2, 3)$
-$(x_2, y_2) = (3, 5)$

We will use Lagrange interpolation to find the quadratic polynomial that passes through these points.

### Step 1: Construct the Lagrange basis polynomials

#### For$L_0(x)$:
$$
L_0(x) = \frac{(x - x_1)(x - x_2)}{(x_0 - x_1)(x_0 - x_2)} = \frac{(x - 2)(x - 3)}{(1 - 2)(1 - 3)} = \frac{(x - 2)(x - 3)}{2}
$$

#### For$L_1(x)$:
$$
L_1(x) = \frac{(x - x_0)(x - x_2)}{(x_1 - x_0)(x_1 - x_2)} = \frac{(x - 1)(x - 3)}{(2 - 1)(2 - 3)} = \frac{(x - 1)(x - 3)}{-1}
$$
$$
L_1(x) = -(x - 1)(x - 3)
$$

#### For$L_2(x)$:
$$
L_2(x) = \frac{(x - x_0)(x - x_1)}{(x_2 - x_0)(x_2 - x_1)} = \frac{(x - 1)(x - 2)}{(3 - 1)(3 - 2)} = \frac{(x - 1)(x - 2)}{2}
$$

### Step 2: Construct the Lagrange interpolation polynomial

The quadratic polynomial$P(x)$is given by:

$$
P(x) = L_0(x) y_0 + L_1(x) y_1 + L_2(x) y_2
$$

Substitute the values for$L_0(x)$,$L_1(x)$, and$L_2(x)$, and the corresponding$y_0 = 2$,$y_1 = 3$, and$y_2 = 5$:

$$
P(x) = \left(\frac{(x - 2)(x - 3)}{2}\right) \cdot 2 + \left(-(x - 1)(x - 3)\right) \cdot 3 + \left(\frac{(x - 1)(x - 2)}{2}\right) \cdot 5
$$

Simplify each term:

$$
P(x) = (x - 2)(x - 3) + 3(x - 1)(x - 3) + \frac{5}{2}(x - 1)(x - 2)
$$

Now, expand each factor:

1.$(x - 2)(x - 3) = x^2 - 5x + 6$
2.$3(x - 1)(x - 3) = 3(x^2 - 4x + 3) = 3x^2 - 12x + 9$
3.$\frac{5}{2}(x - 1)(x - 2) = \frac{5}{2}(x^2 - 3x + 2) = \frac{5}{2}x^2 - \frac{15}{2}x + 5$

Now, combine all terms:

$$
P(x) = (x^2 - 5x + 6) + (3x^2 - 12x + 9) + \left(\frac{5}{2}x^2 - \frac{15}{2}x + 5\right)
$$

Combine like terms:

-$x^2 + 3x^2 + \frac{5}{2}x^2 = \frac{10}{2}x^2 + \frac{5}{2}x^2 = \frac{15}{2}x^2$
-$-5x - 12x - \frac{15}{2}x = \frac{-10}{2}x - \frac{24}{2}x - \frac{15}{2}x = \frac{-49}{2}x$
-$6 + 9 + 5 = 20$

Thus, the final polynomial is:

$$
P(x) = \frac{15}{2}x^2 - \frac{49}{2}x + 20
$$

### Final Answer:

The quadratic polynomial that passes through the points$(1, 2), (2, 3), (3, 5)$is:

$$
P(x) = \frac{15}{2}x^2 - \frac{49}{2}x + 20
$$

# Newton's Divided Difference Interpolation Method: Detailed Explanation

Newton's Divided Difference Method is a powerful technique used to construct an **interpolating polynomial** for a given set of data points. It is especially useful when data points are **not equally spaced**.

---

## Overview

Given a set of$n+1$data points:

$$
(x_0, y_0), (x_1, y_1), \dots, (x_n, y_n)
$$

Newton's Divided Difference method builds an interpolation polynomial in the following form:

$$
P(x) = f[x_0] + f[x_0, x_1](x - x_0) + f[x_0, x_1, x_2](x - x_0)(x - x_1) + \dots + f[x_0, x_1, \dots, x_n](x - x_0)(x - x_1)\dots(x - x_{n-1})
$$

---

## Definitions

-$f[x_i] = y_i$— the function value at$x_i$
-$f[x_i, x_{i+1}] = \frac{f[x_{i+1}] - f[x_i]}{x_{i+1} - x_i}$— the **first divided difference**
-$f[x_i, x_{i+1}, x_{i+2}] = \frac{f[x_{i+1}, x_{i+2}] - f[x_i, x_{i+1}]}{x_{i+2} - x_i}$— the **second divided difference**
- And so on...

---

## General Formula

For any order of divided differences:

$$
f[x_i, x_{i+1}, \dots, x_{i+k}] = \frac{f[x_{i+1}, \dots, x_{i+k}] - f[x_i, \dots, x_{i+k-1}]}{x_{i+k} - x_i}
$$

---

## Steps to Construct the Polynomial

1. **Set up a table of values** for the$x_i$and$y_i = f[x_i]$.
2. **Compute divided differences** using the recursive formula.
3. **Plug values into the Newton interpolating polynomial** format.

---

## Example Table (for 4 points)

|$x$  |$f[x]$  |$f[x_i,x_{i+1}]$|$f[x_i,x_{i+1},x_{i+2}]$|$f[x_i,x_{i+1},x_{i+2},x_{i+3}]$|
| ------- | ---------- | ------------------ | -------------------------- | ---------------------------------- |
|$x_0$|$f[x_0]$|                    |                            |                                    |
|$x_1$|$f[x_1]$|                    |                            |                                    |
|$x_2$|$f[x_2]$|                    |                            |                                    |
|$x_3$|$f[x_3]$|                    |                            |                                    |

---

## Newton Polynomial Forms

### Linear (2 points):

$$
P(x) = f[x_0] + f[x_0,x_1](x - x_0)
$$

### Quadratic (3 points):

$$
P(x) = f[x_0] + f[x_0,x_1](x - x_0) + f[x_0,x_1,x_2](x - x_0)(x - x_1)
$$

### Cubic (4 points):

$$
P(x) = f[x_0] + f[x_0,x_1](x - x_0) + f[x_0,x_1,x_2](x - x_0)(x - x_1) + f[x_0,x_1,x_2,x_3](x - x_0)(x - x_1)(x - x_2)
$$

---

## Summary

- Newton's Divided Difference method builds polynomials incrementally using divided differences.
- It’s good for **unevenly spaced data**.
- You can **add more points without recomputing everything** — just extend the table and the polynomial.

## Solved Example: Newton's Divided Difference Interpolation

Let's use the Newton's Divided Difference method to interpolate the value of a function given these data points:

|$x$|$f(x)$|
|------|----------|
| 1    | 1        |
| 2    | 4        |
| 3    | 9        |

We want to construct a polynomial that passes through all these points and evaluate it at$x = 2.5$.

---

## Step 1: Setup the Table of Divided Differences

|$x$|$f[x]$|$f[x_0,x_1]$|$f[x_0,x_1,x_2]$|
|------|----------|----------------|---------------------|
| 1    | 1        |                |                     |
| 2    | 4        |                |                     |
| 3    | 9        |                |                     |

### Compute First Divided Differences:
$$
f[x_0,x_1] = \frac{f[2] - f[1]}{2 - 1} = \frac{4 - 1}{1} = 3
$$
$$
f[x_1,x_2] = \frac{f[3] - f[2]}{3 - 2} = \frac{9 - 4}{1} = 5
$$

|$x$|$f[x]$|$f[x_0,x_1]$|$f[x_0,x_1,x_2]$|
|------|----------|----------------|---------------------|
| 1    | 1        | 3              |                     |
| 2    | 4        | 5              |                     |
| 3    | 9        |                |                     |

### Compute Second Divided Difference:
$$
f[x_0,x_1,x_2] = \frac{f[x_1,x_2] - f[x_0,x_1]}{x_2 - x_0} = \frac{5 - 3}{3 - 1} = \frac{2}{2} = 1
$$

|$x$|$f[x]$|$f[x_0,x_1]$|$f[x_0,x_1,x_2]$|
| ----- | -------- | -------------- | ------------------ |
| 1     | 1        | 3              | 1                  |
| 2     | 4        | 5              |                    |
| 3     | 9        |                |                    |

---

## Step 2: Construct the Interpolation Polynomial

$$
P(x) = f[x_0] + f[x_0,x_1](x - x_0) + f[x_0,x_1,x_2](x - x_0)(x - x_1)
$$
$$
P(x) = 1 + 3(x - 1) + 1(x - 1)(x - 2)
$$

---

## Step 3: Evaluate at$x = 2.5$

$$
P(2.5) = 1 + 3(2.5 - 1) + 1(2.5 - 1)(2.5 - 2)
$$
$$
= 1 + 3(1.5) + (1.5)(0.5)
$$
$$
= 1 + 4.5 + 0.75 = \boxed{6.25}
$$

---

## Final Answer

The interpolated value at$x = 2.5$is:

$$
\boxed{P(2.5) = 6.25}
$$

Let me know if you want the general polynomial expanded or plotted!


# Newton's Backward Difference Interpolation

Newton's Backward Difference Formula is a method used to interpolate a value near the **end** of a uniformly spaced data table. It is especially useful when the value to be estimated is **closer to the last entries** in the table.

---

## When to Use:

- Use this method when:
  - The data points are **equally spaced** (uniform step size$h$).
  - The desired value of$x$lies **closer to the last entries** in the data set.

---

## Notation:

Let the data points be:

$$
x_0, x_1, x_2, \ldots, x_n \quad \text{with step size } h = x_{i+1} - x_i
$$

Let the corresponding function values be:

$$
y_0, y_1, y_2, \ldots, y_n
$$

---

## Backward Differences Table

We define:

-$\nabla y_n = y_n - y_{n-1}$
-$\nabla^2 y_n = \nabla y_n - \nabla y_{n-1}$
- and so on...

This is the **backward difference table**, where each difference is calculated going upward.

---

## Formula

Let:
$$
u = \frac{x - x_n}{h}
$$

Then the Newton’s Backward Difference Interpolation Formula is:

$$
P(x) = y_n + u \nabla y_n + \frac{u(u+1)}{2!} \nabla^2 y_n + \frac{u(u+1)(u+2)}{3!} \nabla^3 y_n + \cdots
$$

In general:

$$
P(x) = \sum_{k=0}^{n} \left[ \frac{u(u+1)(u+2)\cdots(u+k-1)}{k!} \nabla^k y_n \right]
$$

Note:
- All differences are taken **from the bottom of the table**.
-$u$increases in steps of$+1$for each term.

---

## Steps to Use the Method

1. **Make sure data points are equally spaced.**

2. **Construct the backward difference table.**

3. **Choose the last point$x_n$, and calculate$u = \frac{x - x_n}{h}$.**

4. **Use the formula to evaluate$P(x)$.**

---

## Example Formulae for Low Degrees

### Linear (Degree 1):
$$
P(x) = y_n + u \nabla y_n
$$

### Quadratic (Degree 2):
$$
P(x) = y_n + u \nabla y_n + \frac{u(u+1)}{2!} \nabla^2 y_n
$$

### Cubic (Degree 3):
$$
P(x) = y_n + u \nabla y_n + \frac{u(u+1)}{2!} \nabla^2 y_n + \frac{u(u+1)(u+2)}{3!} \nabla^3 y_n
$$

## Example: Newton's Backward Difference Interpolation

### Given Data

| x   | f(x) |
|-----|------|
| 1.0 | 0.0  |
| 1.1 | 0.0953 |
| 1.2 | 0.1823 |
| 1.3 | 0.2624 |
| 1.4 | 0.3365 |

We are asked to estimate$f(1.38)$using Newton's Backward Difference Formula.

---

## Step 1: Check if data is uniformly spaced

Step size:  
$h = 1.1 - 1.0 = 0.1$ 
✅ Uniform spacing

---

## Step 2: Construct the Backward Difference Table

Let’s build the difference table starting from the bottom.

| x   | f(x)  | ∇f     | ∇²f    | ∇³f    | ∇⁴f     |
|-----|-------|--------|--------|--------|---------|
| 1.0 | 0.0000|        |        |        |         |
| 1.1 | 0.0953|        |        |        |         |
| 1.2 | 0.1823| 0.0870 |        |        |         |
| 1.3 | 0.2624| 0.0801 | -0.0069|        |         |
| 1.4 | 0.3365| 0.0741 | -0.0060| +0.0009| -0.0009 |

---

## Step 3: Compute$u = \frac{x - x_n}{h}$

We take$x_n = 1.4$,$h = 0.1$, and$x = 1.38$:

$$
u = \frac{1.38 - 1.4}{0.1} = -0.2
$$

---

## Step 4: Apply Newton's Backward Interpolation Formula

$$
f(x) \approx y_n + u ∇y_n + \frac{u(u+1)}{2!} ∇^2y_n + \frac{u(u+1)(u+2)}{3!} ∇^3y_n + \frac{u(u+1)(u+2)(u+3)}{4!} ∇^4y_n
$$

Substitute the known values:

-$y_n = 0.3365$
-$∇y_n = 0.0741$
-$∇²y_n = -0.0060$
-$∇³y_n = 0.0009$
-$∇⁴y_n = -0.0009$

$$
f(1.38) ≈ 0.3365 
+ (-0.2)(0.0741) 
+ \frac{(-0.2)(-0.2+1)}{2}(-0.0060) 
+ \frac{(-0.2)(0.8)(1.8)}{6}(0.0009) 
+ \frac{(-0.2)(0.8)(1.8)(2.8)}{24}(-0.0009)
$$

Break it down:

- First term:$0.3365$
- Second term:$-0.01482$
- Third term:$\frac{(-0.2)(0.8)}{2}(-0.0060) = \frac{-0.16}{2}(-0.0060) = -0.08 \times -0.0060 = 0.00048$
- Fourth term:$\frac{-0.2 \cdot 0.8 \cdot 1.8}{6} \cdot 0.0009 = \frac{-0.288}{6} \cdot 0.0009 ≈ -0.048 \cdot 0.0009 = -0.0000432$
- Fifth term:  
 $\frac{-0.2 \cdot 0.8 \cdot 1.8 \cdot 2.8}{24} \cdot (-0.0009) \approx \frac{-0.8064}{24} \cdot (-0.0009) ≈ -0.0336 \cdot -0.0009 = 0.00003024$

Now sum all:

$$
f(1.38) ≈ 0.3365 - 0.01482 + 0.00048 - 0.0000432 + 0.00003024
$$

$$
f(1.38) ≈ 0.322146
$$

---

## Final Answer:

$$
\boxed{f(1.38) ≈ 0.3221}
$$

# Newton's Forward Difference Formula: Detailed Explanation

Newton's Forward Difference Interpolation is a method used to estimate the value of a function at a given point, using a known set of tabulated values with **equal spacing** in the x-values. It is most accurate when the interpolation point is **near the beginning** of the table.

---

## When to Use:
- The x-values must be equally spaced (i.e., same `h` between each `x` value).
- The value to interpolate should be **closer to the top of the table**.

---

## Formula:

Given:
- Data points:$(x_0, y_0), (x_1, y_1), ..., (x_n, y_n)$
- Step size$h = x_1 - x_0 = x_2 - x_1 = \dots$

Let:
-$u = \frac{x - x_0}{h}$
-$Δy_0, Δ^2y_0, \dots$are forward differences

The interpolation formula is:

$$
f(x) \approx y_0 + uΔy_0 + \frac{u(u - 1)}{2!}Δ^2y_0 + \frac{u(u - 1)(u - 2)}{3!}Δ^3y_0 + \dots
$$

Or in general form:

$$
f(x) \approx \sum_{k=0}^{n} \left( \frac{u(u-1)(u-2)\dots(u-k+1)}{k!} \cdot Δ^k y_0 \right)
$$

---

## Forward Difference Table Construction

Build a difference table like this:

| x     | y      | Δy     | Δ²y    | Δ³y   |
|-------|--------|--------|--------|-------|
| x₀    | y₀     |        |        |       |
| x₁    | y₁     | Δy₀    |        |       |
| x₂    | y₂     | Δy₁    | Δ²y₀   |       |
| x₃    | y₃     | Δy₂    | Δ²y₁   | Δ³y₀  |
| ...   | ...    | ...    | ...    | ...   |

Where:
-$Δy_i = y_{i+1} - y_i$
-$Δ^2y_i = Δy_{i+1} - Δy_i$, and so on.

---

## Summary of Terms:

-$u = \frac{x - x_0}{h}$
-$y_0 = f(x_0)$
-$Δ^k y_0$is the k-th order forward difference starting from$y_0$

---

## Example Formulae:

### Linear (First Order):

$$
f(x) \approx y_0 + uΔy_0
$$

### Quadratic (Second Order):

$$
f(x) \approx y_0 + uΔy_0 + \frac{u(u-1)}{2!}Δ^2y_0
$$

### Cubic (Third Order):

$$
f(x) \approx y_0 + uΔy_0 + \frac{u(u-1)}{2!}Δ^2y_0 + \frac{u(u-1)(u-2)}{3!}Δ^3y_0
$$

---

## When to Stop Expanding Terms?

You can stop at a degree where:
- The degree of the polynomial fits the number of points minus one
- Or when higher-order differences become very small/negligible

## Example: Newton's Forward Difference Formula

We are given the following data:

| x   | f(x) |
|-----|------|
| 1   | 1    |
| 2   | 8    |
| 3   | 27   |
| 4   | 64   |

We want to estimate the value of$f(2.5)$.

---

## Step 1: Construct the Forward Difference Table

| x   | f(x) = y | Δy     | Δ²y    | Δ³y   |
|-----|----------|--------|--------|-------|
| 1   | 1        | 7      | 6      | 0     |
| 2   | 8        | 19     | 6      |       |
| 3   | 27       | 37     |        |       |
| 4   | 64       |        |        |       |

Calculations:
- $Δy₀ = 8 - 1 = 7$
- $Δy₁ = 27 - 8 = 19$
- $Δy₂ = 64 - 27 = 37$

- $Δ²y₀ = 19 - 7 = 12$
- $Δ²y₁ = 37 - 19 = 18$

- $Δ³y₀ = 18 - 12 = 6$

---

## Step 2: Identify values

- $x_0 = 1$
- $y_0 = 1$
- $h = 1$
- $x = 2.5 \Rightarrow u = \frac{2.5 - 1}{1} = 1.5$

---

## Step 3: Apply Newton’s Forward Formula

$$
f(x) \approx y_0 + uΔy_0 + \frac{u(u - 1)}{2!}Δ^2y_0 + \frac{u(u - 1)(u - 2)}{3!}Δ^3y_0
$$

$$
f(2.5) \approx 1 + (1.5)(7) + \frac{1.5(0.5)}{2}(12) + \frac{1.5(0.5)(-0.5)}{6}(6)
$$

$$
= 1 + 10.5 + \frac{0.75}{2}(12) + \frac{-0.375}{6}(6)
$$

$$
= 1 + 10.5 + (0.375)(12) + (-0.0625)(6)
$$

$$
= 1 + 10.5 + 4.5 - 0.375 = 15.625
$$

---

## ✅ Final Answer:

$$
f(2.5) \approx \boxed{15.625}
$$

Let me know if you'd like to see an example with uneven spacing or higher-order terms.
