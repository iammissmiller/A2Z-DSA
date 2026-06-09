# Count Subarrays with Given Sum

## Problem

Given an array and integer **K**, count the **number of subarrays** whose sum equals **K**.

### Example

```
Input:
arr = [1,1,1]
k = 2

Output:
2
```

Explanation:

```
[1,1] (index 0-1)
[1,1] (index 1-2)
```

---

# 1. Brute Force Approach

## Idea

Check all subarrays and count when sum == k

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int countSubarraysBrute(vector<int>& arr, int k)
{
    int n = arr.size();
    int count = 0;

    for(int i = 0; i < n; i++)
    {
        int sum = 0;

        for(int j = i; j < n; j++)
        {
            sum += arr[j];

            if(sum == k)
                count++;
        }
    }

    return count;
}

int main()
{
    vector<int> arr = {1,1,1};
    int k = 2;

    cout << countSubarraysBrute(arr,k);
}
```

### Complexity

Time → **O(n²)**
Space → **O(1)**

---

# 2. Optimal Approach (Prefix Sum + HashMap) ⭐

## Idea

We use prefix sum:

```
sum = sum + arr[i]
```

If:

```
sum - k exists
```

Then subarray with sum k exists.

We store:

```
prefixSum → frequency
```

---

### C++ Code (Most Important)

```cpp
#include <bits/stdc++.h>
using namespace std;

int countSubarraysOptimal(vector<int>& arr, int k)
{
    unordered_map<int,int> mp;

    mp[0] = 1;

    int sum = 0;
    int count = 0;

    for(int x : arr)
    {
        sum += x;

        if(mp.find(sum - k) != mp.end())
        {
            count += mp[sum - k];
        }

        mp[sum]++;
    }

    return count;
}

int main()
{
    vector<int> arr = {1,1,1};
    int k = 2;

    cout << countSubarraysOptimal(arr,k);
}
```

---

# Dry Run

```
arr = [1,1,1]
k = 2
```

Step-by-step:

| i | sum | sum-k | count |
| - | --- | ----- | ----- |
| 1 | 1   | -1    | 0     |
| 1 | 2   | 0     | 1     |
| 1 | 3   | 1     | 2     |

Answer = **2**

---

# Complexity

Time → **O(n)**
Space → **O(n)**

---

# Interview Pattern

If question says:

```
Count subarrays with sum k
```

Think:

```
Prefix Sum + HashMap
```

---

# Difference Between Similar Problems

| Problem                | Method                             |
| ---------------------- | ---------------------------------- |
| Longest subarray sum K | Prefix sum + map (store index)     |
| Count subarrays sum K  | Prefix sum + map (store frequency) |

This difference is **very important in interviews**.

---
