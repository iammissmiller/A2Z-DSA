# Maximum Product Subarray

## Problem

Given an array (can contain **positive, negative, zero**), find the **maximum product of a contiguous subarray**.

---

### Example

```
Input:
arr = [2,3,-2,4]

Output:
6
```

Explanation:

```
Subarray = [2,3]
Product = 6
```

---

# Why This Problem is Tricky

Because of **negative numbers**:

```text
(-2) × (-3) = +6
```

So:

* Minimum can become maximum
* Maximum can become minimum

---

# 1. Brute Force Approach

## Idea

Check all subarrays and compute product.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int maxProductBrute(vector<int>& arr)
{
    int n = arr.size();
    int maxProd = INT_MIN;

    for(int i = 0; i < n; i++)
    {
        int prod = 1;

        for(int j = i; j < n; j++)
        {
            prod *= arr[j];
            maxProd = max(maxProd, prod);
        }
    }

    return maxProd;
}

int main()
{
    vector<int> arr = {2,3,-2,4};
    cout << maxProductBrute(arr);
}
```

### Complexity

* Time → **O(n²)**
* Space → **O(1)**

---

# 2. Optimal Approach (Kadane-like) ⭐

## Idea

Track:

```text
maxEndingHere
minEndingHere
```

Because:

* Negative flips sign
* Min can become max

---

# C++ Code (Most Important)

```cpp
#include <bits/stdc++.h>
using namespace std;

int maxProduct(vector<int>& arr)
{
    int n = arr.size();

    int maxProd = arr[0];
    int minProd = arr[0];
    int result = arr[0];

    for(int i = 1; i < n; i++)
    {
        if(arr[i] < 0)
            swap(maxProd, minProd);

        maxProd = max(arr[i], maxProd * arr[i]);
        minProd = min(arr[i], minProd * arr[i]);

        result = max(result, maxProd);
    }

    return result;
}

int main()
{
    vector<int> arr = {2,3,-2,4};
    cout << maxProduct(arr);
}
```

---

# Complexity

* Time → **O(n)**
* Space → **O(1)**

---

# Dry Run

```text
arr = [2,3,-2,4]
```

| Element | maxProd | minProd | result |
| ------- | ------- | ------- | ------ |
| 2       | 2       | 2       | 2      |
| 3       | 6       | 3       | 6      |
| -2      | -2      | -12     | 6      |
| 4       | 4       | -48     | 6      |

---

# Alternative Approach (Prefix & Suffix Trick)

## Idea

Traverse:

* Left → Right
* Right → Left

Multiply and track max

---

### Code

```cpp
int maxProduct(vector<int>& arr)
{
    int n = arr.size();

    int prefix = 1, suffix = 1;
    int maxProd = INT_MIN;

    for(int i = 0; i < n; i++)
    {
        if(prefix == 0) prefix = 1;
        if(suffix == 0) suffix = 1;

        prefix *= arr[i];
        suffix *= arr[n-1-i];

        maxProd = max({maxProd, prefix, suffix});
    }

    return maxProd;
}
```

---

# Key Differences

| Problem              | Logic              |
| -------------------- | ------------------ |
| Max Sum Subarray     | Kadane (sum reset) |
| Max Product Subarray | Track min + max    |

---

# Common Mistakes

❌ Ignoring negative numbers
❌ Not tracking min product
❌ Resetting like Kadane (wrong here)

---
