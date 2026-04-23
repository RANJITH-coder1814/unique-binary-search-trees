# 🌳 Unique Binary Search Trees (LeetCode 96)

## 📌 Problem Statement

Given an integer `n`, return the number of structurally unique **Binary Search Trees (BSTs)** that can be formed using values from `1` to `n`.

---

## 💡 Approach: Dynamic Programming (Catalan Number)

To construct a BST:

* Choose each number `i` from `1` to `n` as the root.
* Left subtree → values `[1 ... i-1]`
* Right subtree → values `[i+1 ... n]`

Thus,

```
dp[i] += dp[j-1] * dp[i-j]
```

Where:

* `dp[k]` = number of unique BSTs with `k` nodes

---

## 🧠 Intuition

Each root splits the problem into:

* Left subtree possibilities
* Right subtree possibilities

Total BSTs = **product of left and right subtree combinations**

---

## ✅ C++ Solution

```cpp
class Solution {
public:
    int numTrees(int n) {
        vector<int> dp(n + 1, 0);
        
        dp[0] = 1;
        dp[1] = 1;
        
        for (int i = 2; i <= n; i++) {
            for (int j = 1; j <= i; j++) {
                dp[i] += dp[j - 1] * dp[i - j];
            }
        }
        
        return dp[n];
    }
};
```

---

## ⏱️ Complexity Analysis

* **Time Complexity:** `O(n²)`
* **Space Complexity:** `O(n)`

---

## 📊 Example

```
Input: n = 3
Output: 5
```

---

## 🔢 Mathematical Insight (Catalan Number)

The result follows the **Catalan sequence**:

[
C_n = \frac{(2n)!}{(n+1)! \cdot n!}
]

---

## 🏷️ Tags

`Dynamic Programming` `Binary Search Tree` `Catalan Number`

---

## 📁 Repository Structure

```
Unique-BST/
│── solution.cpp
│── README.md
```

---

## 🚀 How to Run

1. Copy the code into your C++ compiler
2. Compile and run
3. Pass the value of `n`

---

## ⭐ If you found this helpful, consider giving a star!
