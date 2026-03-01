# Longest Subarray with Sum K (Positives + Negatives Allowed)

This is the **important version** (harder than sliding window).

---

## Problem

Given an array and a number **K**, find the **length of the longest subarray** with sum = K.

Numbers can be:

* Positive
* Negative
* Zero

### Example

```
Input:
arr = [1, -1, 5, -2, 3]
K = 3

Output:
4

Subarray:
[1, -1, 5, -2]
```

---

# Why Sliding Window Fails 

Sliding window works only for **positive numbers**.

Example:

```
[2, -1, 2]
K = 3
```

Sliding window breaks because sum may decrease after adding elements.

---

# 1. Brute Force Approach

## Idea

Check all subarrays.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int longestSubarrayBrute(vector<int>& a, int k)
{
    int n = a.size();
    int maxLen = 0;

    for(int i = 0; i < n; i++)
    {
        int sum = 0;

        for(int j = i; j < n; j++)
        {
            sum += a[j];

            if(sum == k)
                maxLen = max(maxLen, j-i+1);
        }
    }

    return maxLen;
}

int main()
{
    vector<int> a = {1,-1,5,-2,3};
    int k = 3;

    cout << longestSubarrayBrute(a,k);
}
```

### Complexity

Time = **O(n²)**
Space = **O(1)**

---

# 2. Optimal Approach (HashMap Method) ⭐ MOST IMPORTANT

## Idea

Use **prefix sum + map**

We store:

```
prefixSum → first index
```

Key Formula:

```
if (prefixSum - K exists)
then subarray sum = K
```

---

### Example

```
arr = [1,-1,5,-2,3]
K = 3
```

Prefix sums:

```
1
0
5
3
6
```

When prefixSum = 3 → answer found.

---

# Optimal Code (Very Important)

```cpp
#include <bits/stdc++.h>
using namespace std;

int longestSubarrayOptimal(vector<int>& a, int k)
{
    unordered_map<int,int> mp;

    int sum = 0;
    int maxLen = 0;

    for(int i = 0; i < a.size(); i++)
    {
        sum += a[i];

        if(sum == k)
            maxLen = i + 1;

        if(mp.find(sum-k) != mp.end())
        {
            maxLen = max(maxLen, i - mp[sum-k]);
        }

        if(mp.find(sum) == mp.end())
        {
            mp[sum] = i;
        }
    }

    return maxLen;
}

int main()
{
    int n;
    cin >> n;

    vector<int> a(n);

    for(int i=0;i<n;i++)
        cin>>a[i];

    int k;
    cin>>k;

    cout<<longestSubarrayOptimal(a,k);
}
```

---

# Complexity

Time → **O(n)**
Space → **O(n)**

---

# Interview Pattern Recognition 

| Problem Type          | Method               |
| --------------------- | -------------------- |
| Only positives        | Sliding Window       |
| Positives + Negatives | Prefix Sum + HashMap |

---

# Interview Trick 

Immediately think:

```
Longest subarray sum K → HashMap
```

---
