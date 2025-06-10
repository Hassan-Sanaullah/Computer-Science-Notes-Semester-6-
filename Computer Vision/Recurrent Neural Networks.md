# Recurrent Neural Networks (RNNs)

Recurrent Neural Networks (RNNs) are a class of neural networks designed for processing sequential data. Unlike feedforward neural networks, RNNs have loops that allow information to persist across time steps.

## 1. Architecture

At the core of RNNs is the idea of a **hidden state** that captures information about the sequence. For each time step $t$, the RNN takes an input vector $x_t$, updates its hidden state $h_t$, and optionally produces an output $y_t$.

### Diagram:
```
      x₁ → [RNN Cell] → h₁ → y₁
                ↓
      x₂ → [RNN Cell] → h₂ → y₂
                ↓
      ...
                ↓
      x_T → [RNN Cell] → h_T → y_T
```

Each `[RNN Cell]` shares the same weights across all time steps.

## 2. Mathematical Formulation

For a basic RNN:

- Input at time $t$: $x_t \in \mathbb{R}^n$
- Hidden state at time $t$: $h_t \in \mathbb{R}^m$
- Output at time $t$: $y_t \in \mathbb{R}^k$

### Update Equations

1. **Hidden state**:
   $$
   h_t = \tanh(W_h h_{t-1} + W_x x_t + b_h)
   $$

2. **Output** (optional, depending on use case):
   $$
   y_t = W_y h_t + b_y
   $$

- $W_h \in \mathbb{R}^{m \times m}$ — weight matrix for hidden state
- $W_x \in \mathbb{R}^{m \times n}$ — weight matrix for input
- $W_y \in \mathbb{R}^{k \times m}$ — weight matrix for output
- $b_h, b_y$ — bias vectors

## 3. Components

- **Hidden State ($h_t$)**: Stores information from previous time steps.
- **Input Sequence ($x_1, x_2, ..., x_T$)**: The data fed into the network step-by-step.
- **Output Sequence ($y_1, y_2, ..., y_T$)**: Can be generated at each step or only at the end.
- **Weight Sharing**: All time steps use the same weights.

## 4. Sequence Modeling Types

### 1. One-to-One

- Input: Single item
- Output: Single item
- Example: Image classification

### 2. One-to-Many

- Input: Single item
- Output: Sequence
- Example: Image captioning

```
  x → [RNN] → y₁ → y₂ → y₃ → ...
```

### 3. Many-to-One

- Input: Sequence
- Output: Single item
- Example: Sentiment classification

```
  x₁ → x₂ → x₃ → [RNN] → y
```

### 4. Many-to-Many (Same Length)

- Input: Sequence
- Output: Sequence
- Example: POS tagging

```
  x₁ → [RNN] → y₁
  x₂ → [RNN] → y₂
  x₃ → [RNN] → y₃
```

### 5. Many-to-Many (Different Lengths)

- Input: Sequence
- Output: Sequence (different length)
- Example: Machine translation (Encoder-Decoder)

```
Encoder:
  x₁ → x₂ → x₃ → [RNN] → h

Decoder:
                     h → y₁ → y₂ → y₃
```

## 5. Limitations of Vanilla RNN

- **Vanishing/Exploding Gradients**: Difficult to learn long-term dependencies.
- **Sequential Computation**: Can't parallelize across time steps.
- **Memory Bottleneck**: Hidden state is a bottleneck for all past information.

## 6. Improvements

- **LSTM (Long Short-Term Memory)**: Adds gates to control information flow.
- **GRU (Gated Recurrent Unit)**: Simplified version of LSTM.

# Weight Sharing and Loss Computation in RNNs

## 1. **Weight Sharing Across Time Steps**

In a vanilla RNN, **the same weights are used at every time step**. This is crucial because:

- It **reduces the number of parameters**, making the model more memory-efficient.
- It allows the model to **generalize across sequence lengths** — the same computation applies regardless of how long the sequence is.

### Shared Weights:

- $W_x$, $W_h$, and $b_h$ are used in every time step $t$ to compute the hidden state:
  $$
  h_t = \tanh(W_h h_{t-1} + W_x x_t + b_h)
  $$

- If there's an output, $W_y$ and $b_y$ are also shared:
  $$
  y_t = W_y h_t + b_y
  $$

So, the **same set of weights** (learnable parameters) is **reused** at each time step to process the sequence one element at a time.

---

## 2. **Loss Computation Across Time Steps**

Even though weights are shared, **the loss is typically computed at every time step** (especially in sequence-to-sequence tasks).

### Example: Many-to-Many with equal length

Suppose the target sequence is $\hat{y}_1, \hat{y}_2, ..., \hat{y}_T$ and the predicted outputs are $y_1, y_2, ..., y_T$.

The total loss is the **sum or average of losses** at each time step:

$$
\mathcal{L}_{total} = \sum_{t=1}^{T} \mathcal{L}(y_t, \hat{y}_t)
$$

Where $\mathcal{L}(y_t, \hat{y}_t)$ could be:

- **Cross-entropy** for classification tasks
- **Mean squared error** for regression tasks

---
# Character-level Language Model Example: "hello"

Let's walk through what happens at the architectural level when training an RNN as a **character-level language model**.

---

## 1. **Task Overview**

- **Goal**: Predict the next character given a sequence of characters.
- **Input**: `"hell"`
- **Target (label)**: `"ello"`

The model learns:
- $x_1 = h \rightarrow y_1 = e$
- $x_2 = e \rightarrow y_2 = l$
- $x_3 = l \rightarrow y_3 = l$
- $x_4 = l \rightarrow y_4 = o$

---

## 2. **Vocabulary**

Characters: `[h, e, l, o]`  
Vocabulary size $V = 4$

Each character is converted into a **one-hot vector** of size $4$:

```
h = [1, 0, 0, 0]
e = [0, 1, 0, 0]
l = [0, 0, 1, 0]
o = [0, 0, 0, 1]
```

---

## 3. **Architecture Components**

- **Input size** = $V = 4$
- **Hidden size** = say $H = 8$
- **Output size** = $V = 4$

### Parameters:
- $W_x \in \mathbb{R}^{H \times V}$  → input to hidden
- $W_h \in \mathbb{R}^{H \times H}$  → hidden to hidden
- $b_h \in \mathbb{R}^{H}$           → hidden bias
- $W_y \in \mathbb{R}^{V \times H}$  → hidden to output
- $b_y \in \mathbb{R}^{V}$           → output bias

---

## 4. **Step-by-Step Flow**

Assume input sequence = `["h", "e", "l", "l"]`  
Target sequence = `["e", "l", "l", "o"]`

Initial hidden state: $h_0 = 0$

For each time step $t$:

### Step 1: Input Encoding
Convert character to one-hot vector $x_t$

### Step 2: Hidden State Update
$$
h_t = \tanh(W_x x_t + W_h h_{t-1} + b_h)
$$

### Step 3: Output Prediction
$$
y_t = \text{softmax}(W_y h_t + b_y)
$$

### Step 4: Compute Loss
Compare $y_t$ with target $\hat{y}_t$ using **cross-entropy**:
$$
\mathcal{L}_t = -\log(y_t[\hat{y}_t])
$$

### Step 5: Accumulate Total Loss
$$
\mathcal{L}_{total} = \sum_{t=1}^{T} \mathcal{L}_t
$$

---

## 5. **Unrolled Architecture Diagram (Conceptual)**

```
Input:    h   →  e   →  l   →  l
           ↓     ↓     ↓     ↓
         [RNN] [RNN] [RNN] [RNN]
           ↓     ↓     ↓     ↓
Output:   e     l     l     o
```

---

## 6. **During Inference (Text Generation)**

Given a start character, say `"h"`:

1. Feed `"h"` to RNN → get $y_1$ (probability distribution over `[h, e, l, o]`)
2. Sample next char (e.g., `"e"`)
3. Feed `"e"` → get $y_2$
4. Repeat for desired length

---

## Summary

- Each input character is one-hot encoded.
- RNN uses shared weights to update hidden state and predict next character.
- Loss is computed at each time step comparing predicted char vs target.
- The model learns character transitions, enabling it to generate text one character at a time.
---
# Backpropagation Through Time (BPTT)

**Backpropagation Through Time (BPTT)** is the algorithm used to train Recurrent Neural Networks (RNNs) by computing gradients over sequences. It's an extension of the backpropagation algorithm to handle temporal dependencies in sequences.

---

## 1. **Why BPTT?**

In RNNs, the same weights are used at every time step. So when you compute the total loss across all time steps, you need to:
- Compute how each weight contributed to all outputs.
- Accumulate gradients across time.

BPTT allows us to compute these gradients by **unrolling** the RNN across time steps.

---

## 2. **Unrolling the RNN**

Suppose you have an input sequence of length $T$:  
$x_1, x_2, ..., x_T$

You **unroll** the RNN into $T$ copies, each corresponding to a time step:

```
x₁ → [RNN₁] → h₁ → y₁
x₂ → [RNN₂] → h₂ → y₂
x₃ → [RNN₃] → h₃ → y₃
...
x_T → [RNN_T] → h_T → y_T
```

Even though each `[RNN_t]` is a separate "copy" in the unrolled graph, **all share the same weights**.

---

## 3. **Forward Pass Recap**

At each time step $t$:
- Input: $x_t$
- Hidden state: 
  $$
  h_t = \tanh(W_x x_t + W_h h_{t-1} + b_h)
  $$
- Output:
  $$
  y_t = W_y h_t + b_y
  $$
- Loss:
  $$
  \mathcal{L}_t = \text{Loss}(y_t, \hat{y}_t)
  $$
- Total loss:
  $$
  \mathcal{L}_{total} = \sum_{t=1}^{T} \mathcal{L}_t
  $$

---

## 4. **Backward Pass: BPTT**

We now compute gradients of $\mathcal{L}_{total}$ w.r.t. the shared weights: $W_x$, $W_h$, $W_y$.

### Goal:
Compute:
- $\frac{\partial \mathcal{L}_{total}}{\partial W_x}$
- $\frac{\partial \mathcal{L}_{total}}{\partial W_h}$
- $\frac{\partial \mathcal{L}_{total}}{\partial W_y}$

### Key Challenge:
Each hidden state $h_t$ **affects all future outputs** $y_{t+1}, y_{t+2}, ..., y_T$. So we need to backpropagate **through time** to capture these dependencies.

---

## 5. **Chain Rule Over Time**

For a given time step $t$, the total derivative of the loss w.r.t. $h_t$ includes its impact on:
- Output at time $t$
- All future hidden states

So we compute:

$$
\frac{\partial \mathcal{L}_{total}}{\partial h_t} = \sum_{k=t}^{T} \frac{\partial \mathcal{L}_k}{\partial h_k} \cdot \frac{\partial h_k}{\partial h_t}
$$

This is where the **recursive structure** of RNNs makes things complex.

---

## 6. **Gradient Flow Equations**

Let’s look at a simplified flow:

1. **Gradient of loss w.r.t. output layer:**
   $$
   \delta^{(y)}_t = \frac{\partial \mathcal{L}_t}{\partial y_t}
   $$
   This is standard (e.g., softmax + cross-entropy).

2. **Backpropagate to hidden state:**
   $$
   \delta^{(h)}_t = W_y^T \delta^{(y)}_t + W_h^T \delta^{(h)}_{t+1} \circ (1 - h_t^2)
   $$
   where:
   - $W_h^T \delta^{(h)}_{t+1}$ is the recursive gradient from the next time step.
   - $\circ$ is element-wise multiplication (Hadamard product).
   - $(1 - h_t^2)$ is from derivative of $\tanh$.

3. **Compute gradients w.r.t weights:**
   $$
   \frac{\partial \mathcal{L}_{total}}{\partial W_x} = \sum_{t=1}^{T} \delta^{(h)}_t \cdot x_t^T
   $$
   $$
   \frac{\partial \mathcal{L}_{total}}{\partial W_h} = \sum_{t=1}^{T} \delta^{(h)}_t \cdot h_{t-1}^T
   $$

---

## 7. **Vanishing and Exploding Gradients**

Because of the recursive gradient:
$$
\delta^{(h)}_t = W_h^T \delta^{(h)}_{t+1} \circ (1 - h_t^2)
$$

- If $W_h$ has eigenvalues < 1: gradients shrink exponentially → **vanishing gradient**
- If $W_h$ has eigenvalues > 1: gradients grow exponentially → **exploding gradient**

This is why vanilla RNNs struggle with **long-term dependencies**.

---

## 8. **Truncated BPTT**

To reduce computational cost and mitigate vanishing/exploding gradients, we often use **truncated BPTT**:

- Only backpropagate through a fixed number of steps (e.g., 5–20).
- The rest of the history is ignored during gradient computation.

---

## Summary

- BPTT unrolls the RNN across time to compute gradients over all time steps.
- The same weights are reused, but gradients are accumulated from all time steps.
- Gradient flow is recursive and depends on both current and future losses.
- It suffers from vanishing/exploding gradients, which LSTMs and GRUs address.

Would you like a visual diagram or pseudocode of BPTT next?
