# Find the Repeating and Missing Number

## Problem

You are given an array of size **n** containing numbers from **1 to n**.

* One number is **missing**
* One number is **repeating**

Find both.

---

### Example

```text
Input:
arr = [3,1,2,5,3]

Output:
Repeating = 3
Missing = 4
```

---

# 1. Brute Force Approach

## Idea

For each number from **1 to n**, count occurrences.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

pair<int,int> findRMBrute(vector<int>& arr, int n)
{
    int repeating = -1, missing = -1;

    for(int i = 1; i <= n; i++)
    {
        int count = 0;

        for(int j = 0; j < n; j++)
        {
            if(arr[j] == i)
                count++;
        }

        if(count == 2) repeating = i;
        if(count == 0) missing = i;
    }

    return {repeating, missing};
}
```

### Complexity

* Time → **O(n²)**
* Space → **O(1)**

---

# 2. Better Approach (Hashing)

## Idea

Use frequency array.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

pair<int,int> findRMBetter(vector<int>& arr, int n)
{
    vector<int> freq(n+1, 0);

    for(int x : arr)
        freq[x]++;

    int repeating = -1, missing = -1;

    for(int i = 1; i <= n; i++)
    {
        if(freq[i] == 2) repeating = i;
        if(freq[i] == 0) missing = i;
    }

    return {repeating, missing};
}
```

### Complexity

* Time → **O(n)**
* Space → **O(n)**

---

# 3. Optimal Approach (Math Equation Method) ⭐

## Idea

Let:

```text
S  = sum of first n numbers
S2 = sum of squares of first n numbers
```

Compute:

```text
Actual sum = S - x + y
Actual square sum = S2 - x² + y²
```

Where:

```text
x = missing
y = repeating
```

---

## Form Equations

```text
S - actualSum = x - y   ...(1)
S2 - actualSquareSum = x² - y² = (x-y)(x+y) ...(2)
```

From (1) and (2), find x and y.

---

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

pair<int,int> findRMOptimal(vector<int>& arr, int n)
{
    long long S = (long long)n * (n + 1) / 2;
    long long S2 = (long long)n * (n + 1) * (2*n + 1) / 6;

    long long sum = 0, sqSum = 0;

    for(int x : arr)
    {
        sum += x;
        sqSum += (long long)x * x;
    }

    long long val1 = S - sum;                 // x - y
    long long val2 = S2 - sqSum;              // x² - y²

    val2 = val2 / val1;                      // x + y

    long long x = (val1 + val2) / 2;         // missing
    long long y = x - val1;                  // repeating

    return {(int)y, (int)x};
}
```

---

# 4. Best Approach (XOR Method) ⭐⭐⭐

## Idea

Use XOR properties:

```text
a ^ a = 0
a ^ 0 = a
```

---

## Steps

1. XOR all array elements + numbers from 1 to n
2. Result = x ^ y
3. Find rightmost set bit
4. Divide numbers into 2 groups
5. XOR separately to get x and y

---

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

pair<int,int> findRMXOR(vector<int>& arr, int n)
{
    int xr = 0;

    for(int i = 0; i < n; i++)
        xr ^= arr[i];

    for(int i = 1; i <= n; i++)
        xr ^= i;

    // rightmost set bit
    int bit = xr & -xr;

    int zero = 0, one = 0;

    for(int x : arr)
    {
        if(x & bit) one ^= x;
        else zero ^= x;
    }

    for(int i = 1; i <= n; i++)
    {
        if(i & bit) one ^= i;
        else zero ^= i;
    }

    // check which is repeating
    for(int x : arr)
    {
        if(x == one)
            return {one, zero};
    }

    return {zero, one};
}
```

---

# Complexity Comparison

| Approach | Time  | Space  |
| -------- | ----- | ------ |
| Brute    | O(n²) | O(1)   |
| Hashing  | O(n)  | O(n)   |
| Math     | O(n)  | O(1)   |
| XOR      | O(n)  | O(1) ⭐ |

---

# Interview Tips ⭐

If interviewer says:

```text
one missing, one repeating
```

Think:

```text
XOR OR Math
```

---

# Key Patterns

| Problem             | Best Method |
| ------------------- | ----------- |
| Missing number      | Sum / XOR   |
| Single number       | XOR         |
| Missing + repeating | XOR / Math  |

---
