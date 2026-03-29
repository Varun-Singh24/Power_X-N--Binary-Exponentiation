# Binary Exponentiation - Pow(x, n) Implementation

This repository contains an optimized C++ solution for calculating $x^n$ (x raised to the power n) using the **Binary Exponentiation** algorithm.

---

## 🚀 How the Algorithm Works

Standard multiplication takes $O(n)$ time. Binary Exponentiation reduces this to $O(\log n)$ by using the properties of exponents:
* If $n$ is even: $x^n = (x^2)^{n/2}$
* If $n$ is odd: $x^n = x \cdot (x^2)^{(n-1)/2}$

### Steps:
1.  **Handle Negative Exponents:** If $n < 0$, we transform the problem: $x^n = (1/x)^{-n}$.
2.  **Binary Loop:** While the exponent is greater than 0:
    * If the exponent is **odd**, multiply the result by the current $x$.
    * **Square the base** ($x = x \cdot x$) and divide the exponent by 2.
3.  **Efficiency:** This approach effectively processes the bits of the exponent from least significant to most significant.

## 📊 Complexity Analysis

| Metric | Complexity | Description |
| :--- | :--- | :--- |
| **Time Complexity** | $O(\log n)$ | The exponent is halved in every iteration of the loop. |
| **Space Complexity** | $O(1)$ | Only a few variables are used to store the intermediate results. |

---

## 💻 Code Overview

The solution uses a `long` variable to prevent overflow when negating `INT_MIN`:

```cpp
double myPow(double x, int n) { 
    long binf = n;   
    double ans = 1;

    if(n < 0) {
        x = 1 / x;
        binf = -binf;
    }

    while(binf > 0) {
        if (binf % 2 == 1) {
            ans *= x;
        }
        x *= x;
        binf = binf / 2;
    }
    return ans; 
}

```

#  📝 ExampleInput:
x = 2.00000, 
n = 10Binary
breakdown: $2^{10} = (2^2)^5 = 4^5 = 4 \cdot (4^2)^2 = 4 \cdot 16^2 = 4 \cdot 256 = 1024$

Output: 1024.00000
