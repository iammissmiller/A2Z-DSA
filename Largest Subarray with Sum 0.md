# Largest Subarray with Sum 0

## Problem

Given an array (can have **positive, negative, zero**), find the **length of the longest subarray** with sum = **0**.

---

### Example

```
Input:
arr = [15, -2, 2, -8, 1, 7, 10, 23]

Output:
5
```

Explanation:

```
Subarray = [-2, 2, -8, 1, 7]
Sum = 0
Length = 5
```

---

# 1. Brute Force Approach

## Idea

Check all subarrays and track sum.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int largestSubarrayBrute(vector<int>& arr)
{
    int n = arr.size();
    int maxLen = 0;

    for(int i = 0; i < n; i++)
    {
        int sum = 0;

        for(int j = i; j < n; j++)
        {
            sum += arr[j];

            if(sum == 0)
            {
                maxLen = max(maxLen, j - i + 1);
            }
        }
    }

    return maxLen;
}

int main()
{
    vector<int> arr = {15,-2,2,-8,1,7,10,23};

    cout << largestSubarrayBrute(arr);
}
```

### Complexity

Time → **O(n²)**
Space → **O(1)**

---

# 2. Optimal Approach (Prefix Sum + HashMap) ⭐

## Core Idea

If **same prefix sum repeats**, then subarray between them = 0

---

### Why?

```
prefix[i] = prefix[j]
→ sum(i+1 to j) = 0
```

---

# Optimal Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int largestSubarrayOptimal(vector<int>& arr)
{
    unordered_map<int,int> mp;

    int sum = 0;
    int maxLen = 0;

    for(int i = 0; i < arr.size(); i++)
    {
        sum += arr[i];

        if(sum == 0)
        {
            maxLen = i + 1;
        }

        if(mp.find(sum) != mp.end())
        {
            maxLen = max(maxLen, i - mp[sum]);
        }
        else
        {
            mp[sum] = i;
        }
    }

    return maxLen;
}

int main()
{
    vector<int> arr = {15,-2,2,-8,1,7,10,23};

    cout << largestSubarrayOptimal(arr);
}
```

---

# Complexity

Time → **O(n)**
Space → **O(n)**

---

# Dry Run

```
arr = [15,-2,2,-8,1,7,10,23]
```

Prefix sums:

```
15
13
15   → repeat → subarray sum = 0
7
8
15
25
48
```

Longest = **5**

---

# Key Interview Insight ⭐

### If question says:

```
Longest subarray sum = 0
```

Think:

```
Prefix Sum + HashMap
```

---

# Difference from Similar Problems

| Problem                | Technique         |
| ---------------------- | ----------------- |
| Longest subarray sum K | Prefix sum + map  |
| Count subarrays sum K  | Prefix sum + freq |
| Largest subarray sum 0 | Prefix sum repeat |

---
