Here's a **comprehensive, semester-standard theoretical write-up** for **QB103 (a)** including problem analysis, recursive Python code, explanation, and time complexity classification – suitable for a **15-mark question**.



## ✅ QB103 (a) – Analyze the Algorithm and Write a Python Program to Calculate the Sum of the Series 1 + 2 + 3 + … + N Using a Recursive Function and Estimate Its Category of Running Time



#### **1. Problem Statement**

> Given a positive integer `N`, compute the sum of the first `N` natural numbers using a **recursive function**. Additionally, perform a **theoretical analysis** of the algorithm's time complexity and classify it in terms of **asymptotic notation**.



#### **2. Mathematical Background**

The **sum of the first `N` natural numbers** is:

$$
S = 1 + 2 + 3 + \dots + N = \frac{N(N + 1)}{2}
$$

However, this formula is constant-time. Since the question explicitly requires a **recursive implementation**, we must define the problem recursively.



#### **3. Recursive Algorithm Design**

A recursive function breaks the problem down as:

$$
\text{sum}(N) =
\begin{cases}
0 & \text{if } N = 0 \\
N + \text{sum}(N-1) & \text{if } N > 0
\end{cases}
$$

This forms the basis for our algorithm:

* **Base Case:** sum(0) = 0
* **Recursive Case:** sum(N) = N + sum(N - 1)



#### **4. Python Program: Recursive Implementation**

```python
# Recursive function to compute sum of 1 to N
def recursive_sum(n):
    if n == 0:
        return 0                # Base case
    else:
        return n + recursive_sum(n - 1)  # Recursive step

# Driver Code
N = int(input("Enter a number N: "))
total = recursive_sum(N)
print(f"The sum of first {N} natural numbers is: {total}")
```



#### **5. Example Execution**

##### Input:

```
Enter a number N: 5
```

##### Output:

```
The sum of first 5 natural numbers is: 15
```



#### **6. Execution Trace**

For `N = 4`, the call stack looks like:

```
recursive_sum(4)
→ 4 + recursive_sum(3)
     → 3 + recursive_sum(2)
         → 2 + recursive_sum(1)
             → 1 + recursive_sum(0)
                 → 0
```

The return values unwind as:

```
→ 1 + 0 = 1
→ 2 + 1 = 3
→ 3 + 3 = 6
→ 4 + 6 = 10
```



#### **7. Time and Space Complexity Analysis**

##### **Time Complexity**

Each recursive call performs one addition and makes **one recursive call** until it reaches 0. So for input `N`, we make `N` recursive calls.

$$
T(N) = T(N - 1) + O(1)
\Rightarrow T(N) = O(N)
$$

> ✅ **Time Complexity: O(N)**
> (Linear time, because the function is called `N` times)

##### **Space Complexity**

Since recursion uses the **call stack**, we store one frame for each level of recursion, resulting in:

> ✅ **Space Complexity: O(N)**

> ⚠️ Stack overflow may occur for very large `N` (e.g., >1000), unless optimized using **tail recursion** (which Python doesn't support natively).



#### **8. Algorithm Classification (Asymptotic Category)**

| Category         | Analysis                            |
| - | -- |
| Best Case        | O(N) – all recursive calls executed |
| Worst Case       | O(N) – no early termination         |
| Average Case     | O(N) – linear stack and ops         |
| Time Complexity  | **Linear – O(N)**                   |
| Space Complexity | **Linear – O(N)**                   |

Thus, the algorithm is categorized under **linear-time recursive algorithms**.



#### **9. Conclusion**

The recursive function for summing the first `N` natural numbers effectively illustrates:

* **Recursive problem solving**
* **Stack-based execution**
* **Linear time and space complexity**

Although this method is **educational**, for high-performance systems, the **constant-time formula** $(N(N+1))/2$ is preferred.

> ✅ **Recommendation:** Use recursion for clarity in educational contexts; use the formula for performance-critical applications.



Would you like a version of this program written with memoization or iteration for comparative analysis?
