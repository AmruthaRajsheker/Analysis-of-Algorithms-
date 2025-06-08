Certainly. Below is a comprehensive, polished **15-mark semester exam answer** that merges both questions QB503(a) and QB504(a) into a single, coherent, detailed response. It covers the theory of approximation algorithms for NP-Hard problems, their motivation, characteristics, and also clearly outlines the systematic steps to find approximate solutions with a concrete example.

---

# Approximation Algorithms for NP-Hard Problems and Methodology to Find Approximate Solutions with Example

---

## 1. Introduction to NP-Hard Problems

In computational complexity, **NP-Hard problems** constitute a class of decision or optimization problems for which **no polynomial-time algorithm is known to exist** that solves them exactly (unless $P = NP$). These problems are considered intractable as their solution space grows exponentially with input size, making exact computation impractical for large instances.

**Formally,** a problem $L$ is NP-Hard if every problem in NP can be polynomially reduced to $L$. This implies that if an efficient (polynomial-time) algorithm exists for any NP-Hard problem, then all problems in NP can be efficiently solved, a scenario widely believed not to be true.

**Examples** of NP-Hard problems include:

* 0/1 Knapsack Problem
* Traveling Salesman Problem (TSP)
* Vertex Cover Problem
* Set Cover Problem
* Graph Coloring

---

## 2. Motivation for Approximation Algorithms

Given the **infeasibility of exact solutions** for NP-Hard problems in polynomial time, **approximation algorithms** become vital tools. They provide:

* **Efficient computation** by running in polynomial time.
* **Feasible, near-optimal solutions** instead of exact ones.
* **Performance guarantees** by bounding how close the approximate solution is to the optimum.

This trade-off is critical in practical applications like logistics, resource allocation, network design, where timely solutions are essential even if they are not perfectly optimal.

---

## 3. What is an Approximation Algorithm?

An **approximation algorithm** is a polynomial-time algorithm designed to tackle an NP-Hard optimization problem by producing a solution whose cost/value is provably close to the optimal. The quality of the approximation is quantified by the **approximation ratio** $\rho(n)$:

* For minimization problems:

$$
\frac{\text{Cost of Approximate Solution}}{\text{Cost of Optimal Solution}} \leq \rho(n)
$$

* For maximization problems:

$$
\frac{\text{Optimal Solution Value}}{\text{Value of Approximate Solution}} \leq \rho(n)
$$

where $\rho(n) \geq 1$, and the closer $\rho(n)$ is to 1, the better the approximation.

---

## 4. Characteristics of Approximation Algorithms

* **Polynomial time:** Efficient execution on large inputs.
* **Feasibility:** Solutions always satisfy problem constraints.
* **Provable bounds:** The worst-case performance relative to the optimum is mathematically bounded.
* **Variety:** Deterministic or randomized approaches.
* **Applicability:** Widely used for both minimization and maximization problems.

---

## 5. Types of Approximation Algorithms and Schemes

| Type                                               | Description                                                                                                              |
| -------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| Constant-factor Approximation                      | Fixed approximation ratio, e.g., 2-approximation.                                                                        |
| Polynomial-Time Approximation Scheme (PTAS)        | For any $\epsilon > 0$, produces $(1 + \epsilon)$-approximation. Runtime polynomial but degree may depend on $\epsilon$. |
| Fully Polynomial-Time Approximation Scheme (FPTAS) | Polynomial in both input size and $1/\epsilon$, allowing fine-grained control over accuracy and runtime.                 |

---

## 6. Systematic Steps to Find Approximate Solutions

To develop an approximation algorithm for an NP-Hard problem, the following steps are followed:

### Step 1: Problem Identification and Formalization

* Precisely define the optimization problem, including objective function, constraints, and decision variables.
* Confirm the problem’s NP-Hardness via known reductions or literature.

### Step 2: Select an Approximation Paradigm

Common approaches include:

* **Greedy algorithms:** Iterative, locally optimal choices.
* **Dynamic Programming with Rounding/Scaling:** Simplify problem parameters to reduce complexity.
* **Linear Programming Relaxation:** Relax integer constraints and round solutions.
* **Primal-Dual Methods:** Use dual solutions to guide approximations.
* **Local Search / Metaheuristics:** Iterative improvement heuristics.

### Step 3: Algorithm Design

* Construct a polynomial-time algorithm that yields a feasible solution.
* Leverage problem-specific properties for efficiency.

### Step 4: Performance Guarantee Analysis

* Mathematically prove the approximation ratio.
* Demonstrate the bound holds for all inputs.

### Step 5: Implementation and Optimization

* Implement the algorithm ensuring correctness.
* Optionally optimize for runtime or improve approximation bounds.

---

## 7. Illustrative Example: 0/1 Knapsack Problem Using FPTAS

### Problem Statement:

Given $n$ items with values $v_i$ and weights $w_i$, select a subset such that the total weight does not exceed capacity $W$ and the total value is maximized.

### Challenge:

* Exact solutions have exponential complexity due to combinatorial explosion.
* The problem is NP-Hard.

### Approximation Approach: Fully Polynomial-Time Approximation Scheme (FPTAS)

1. **Scaling of Values:**

   * Let $V_{\max} = \max_i v_i$.
   * For a chosen accuracy parameter $\epsilon > 0$:

   $$
   v'_i = \left\lfloor \frac{v_i \times n}{\epsilon V_{\max}} \right\rfloor
   $$

   This reduces the range of values, simplifying the dynamic programming state space.

2. **Dynamic Programming Solution:**

   * Apply DP on the scaled values $v'_i$ to find an optimal subset in the reduced space.

3. **Solution Reconstruction:**

   * Map the DP solution back to the original problem space.

4. **Performance Guarantee:**

   * The total value of the approximate solution is at least $(1 - \epsilon)$ times the optimal value.
   * The algorithm runs in time polynomial in $n$ and $1/\epsilon$.

---

## 8. Summary Table of Common Approximation Algorithms

| Problem      | Algorithm Paradigm      | Approximation Ratio | Complexity                      |
| ------------ | ----------------------- | ------------------- | ------------------------------- |
| Vertex Cover | Greedy                  | 2                   | Polynomial                      |
| Set Cover    | Greedy                  | $\ln n$             | Polynomial                      |
| Metric TSP   | Christofides’ Algorithm | 1.5                 | Polynomial                      |
| 0/1 Knapsack | FPTAS (Scaling + DP)    | $1 - \epsilon$      | Polynomial in $n$, $1/\epsilon$ |

---

## 9. Conclusion

Approximation algorithms are indispensable in handling NP-Hard problems where exact computation is impractical. They systematically balance **efficiency and solution quality** through well-founded mathematical guarantees. By following structured design steps—from problem formalization to performance analysis—practitioners can develop robust algorithms that deliver high-quality solutions within acceptable computational limits. The 0/1 Knapsack example highlights how theoretical insights translate into practical, scalable solutions.

---

Let me know if you require an academic-style formatted document or additional diagrams to accompany this answer.



Below is a **15-mark semester exam-style answer** for **QC101(a)**, addressing both parts—**LCM using recursion** and **Fibonacci using recursion**—with formal derivations, time complexity analysis, and recurrence relations, tailored for academic rigor.

---

## QC101 (a)

### i) Analyze the recursive version to find the **LCM (Least Common Multiple)** of two numbers. Derive the recurrence relation for the same. (8 Marks)

---

### **Concept Overview**

The **Least Common Multiple (LCM)** of two integers $a$ and $b$ is the smallest positive integer divisible by both. It can be computed using the formula:

$$
\text{LCM}(a, b) = \frac{|a \cdot b|}{\text{GCD}(a, b)}
$$

Thus, the LCM calculation fundamentally depends on computing the **Greatest Common Divisor (GCD)** efficiently.

---

### **Recursive Algorithm for GCD (Euclidean Algorithm)**

```python
def gcd(a, b):
    if b == 0:
        return a
    else:
        return gcd(b, a % b)
```

Once GCD is computed, LCM is derived using:

```python
def lcm(a, b):
    return (a * b) // gcd(a, b)
```

---

### **Recurrence Relation Derivation (for GCD)**

Let $T(n)$ be the time taken by `gcd(a, b)` where $n = \min(a, b)$.
The recurrence relation for the Euclidean algorithm is:

$$
T(n) = T(n \mod m) + O(1)
$$

Where each recursive call reduces the problem size using the modulus operator.

In the worst case, it mimics **Fibonacci number reductions** (e.g., $gcd(F_{k+1}, F_k)$), so the **depth of recursion** is $O(\log \min(a, b))$.

---

### **Time Complexity of LCM Function**

* **GCD computation:** $O(\log \min(a, b))$
* **Multiplication and division:** Constant time operations.

Hence, **overall time complexity:**

$$
O(\log \min(a, b))
$$

---

### **Conclusion for Part (i)**

The recursive version of LCM leverages the recursive Euclidean GCD algorithm. The **recurrence relation** is:

$$
T(n) = T(n \bmod m) + O(1)
$$

and the total time complexity is $O(\log \min(a, b))$, which is efficient even for large numbers.

---

### ii) Analyze the recursive version of the **Fibonacci function**. Derive the recurrence relation for the same. (7 Marks)

---

### **Definition**

The Fibonacci sequence is defined recursively as:

$$
F(n) =
\begin{cases}
0, & \text{if } n = 0 \\
1, & \text{if } n = 1 \\
F(n-1) + F(n-2), & \text{if } n > 1
\end{cases}
$$

---

### **Naïve Recursive Implementation**

```python
def fibonacci(n):
    if n <= 1:
        return n
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)
```

---

### **Recurrence Relation**

Let $T(n)$ be the number of steps for `fibonacci(n)`:

$$
T(n) = T(n-1) + T(n-2) + O(1)
$$

This is the **same recurrence** as the Fibonacci series itself.

---

### **Time Complexity Analysis**

The recurrence:

$$
T(n) = T(n-1) + T(n-2) + O(1)
$$

leads to an **exponential time complexity**:

$$
T(n) = O(2^n)
$$

This occurs because the recursion tree has overlapping subproblems and duplicates many computations (e.g., `fibonacci(n - 2)` gets recomputed multiple times).

---

### **Space Complexity**

* **Stack depth** of the recursion: $O(n)$
* **No memoization**: high redundancy in calls.

---

### **Conclusion for Part (ii)**

* The recursive Fibonacci function has a recurrence:

  $$
  T(n) = T(n - 1) + T(n - 2) + O(1)
  $$
* Time complexity: $O(2^n)$
* The solution is **computationally inefficient** without optimization techniques such as **memoization** or **dynamic programming**.

---

## Final Remarks

| Function      | Recurrence Relation                 | Time Complexity      |
| ------------- | ----------------------------------- | -------------------- |
| LCM (via GCD) | $T(n) = T(n \mod m) + O(1)$         | $O(\log \min(a, b))$ |
| Fibonacci     | $T(n) = T(n - 1) + T(n - 2) + O(1)$ | $O(2^n)$             |

This detailed breakdown satisfies a full-length academic explanation suitable for 15-mark university-level questions. Let me know if you need a diagram or dry-run trace for either.

---
---
Certainly. Below is a **comprehensive, academically rigorous answer** to your problem statement, formatted for **7-mark or short 10-mark exam questions** under the **Greedy (Fractional Knapsack)** paradigm. This is tailored with an analytical approach, intermediate calculations, and rationale for every decision step.

---

### 🧮 Problem Statement:

Find an optimal solution to the **Knapsack problem instance** using **Greedy Strategy (Fractional Knapsack)**.

* **Number of items (n)**: 4
* **Knapsack Capacity (m)**: 15 units
* **Profits (p)**: (10, 5, 7, 11)
* **Weights (w)**: (3, 4, 3, 5)

---

### ✅ Step 1: Calculate Profit-to-Weight Ratio for Each Item

To apply the greedy method, compute the ratio $\frac{p_i}{w_i}$ for each item:

| Item | Profit ($p_i$) | Weight ($w_i$) | Ratio $\frac{p_i}{w_i}$ |
| ---- | -------------- | -------------- | ----------------------- |
| 1    | 10             | 3              | 3.33                    |
| 2    | 5              | 4              | 1.25                    |
| 3    | 7              | 3              | 2.33                    |
| 4    | 11             | 5              | 2.20                    |

---

### ✅ Step 2: Sort Items by Decreasing Profit-to-Weight Ratio

To maximize profit, prioritize items with **higher ratios**.

**Sorted Order (Descending Ratio):**
→ Item 1 → Item 3 → Item 4 → Item 2

---

### ✅ Step 3: Greedy Selection – One by One (Fractional Allowed)

Knapsack Capacity = 15
We proceed to add items in this order until the capacity is filled.

| Step | Picked Item | Weight Taken | Profit Gained | Remaining Capacity |
| ---- | ----------- | ------------ | ------------- | ------------------ |
| 1    | Item 1      | 3            | 10            | 15 − 3 = 12        |
| 2    | Item 3      | 3            | 7             | 12 − 3 = 9         |
| 3    | Item 4      | 5            | 11            | 9 − 5 = 4          |
| 4    | Item 2      | 4            | 5             | 4 − 4 = 0 ✅        |

Since **total weight (3 + 3 + 5 + 4 = 15)** equals capacity, **no fractional selection** is required.

---

### 🟢 All Items Fit — No Truncation Needed

This implies that the **greedy strategy gives an optimal solution** for this instance — even though this is generally **not guaranteed** for **0/1 knapsack**, it works perfectly here due to alignment of capacity and weights.

---

### ✅ Step 4: Final Computation and Result

* **Total Weight Used** = 15
* **Total Profit Gained** = 10 + 7 + 11 + 5 = **33**
* **Items Selected** = Item 1, 3, 4, 2
* **Order of Selection** = Based on decreasing ratio

---

### 📌 Final Answer

> ✅ **Optimal Profit** = **33**
> ✅ **Items Selected** = Item 1, Item 3, Item 4, Item 2
> ✅ **Approach Used** = Greedy Strategy (Fractional Knapsack)

---

### ⚠️ Important Notes (for academic depth):

* The **greedy method** is optimal only for the **fractional knapsack problem**, **not** for the classic **0/1 knapsack**.
* In this case, since all items fit without needing fractional parts, **greedy yields the optimal solution** that matches what you'd obtain via **0/1 dynamic programming**.

Let me know if you’d like this solution visualized as a bar chart or tabulated matrix.

---
---


