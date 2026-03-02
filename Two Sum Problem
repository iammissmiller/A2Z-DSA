# Two Sum Problem (Very Important)

## Problem

Given an array and a target **K**, find **two indices** such that:

```
arr[i] + arr[j] = K
```

### Example

```
Input:
arr = [2, 6, 5, 8, 11]
K = 14

Output:
1 3

Explanation:
6 + 8 = 14
```

---

# 1. Brute Force Approach

## Idea

Check all pairs.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

pair<int,int> twoSumBrute(vector<int>& arr, int k)
{
    int n = arr.size();

    for(int i = 0; i < n; i++)
    {
        for(int j = i+1; j < n; j++)
        {
            if(arr[i] + arr[j] == k)
            {
                return {i, j};
            }
        }
    }

    return {-1, -1};
}

int main()
{
    vector<int> arr = {2,6,5,8,11};
    int k = 14;

    pair<int,int> ans = twoSumBrute(arr,k);

    cout << ans.first << " " << ans.second;
}
```

### Complexity

Time → **O(n²)**
Space → **O(1)**

---

# 2. Better Approach (HashMap) ⭐ Most Asked

## Idea

For each element:

```
needed = k - arr[i]
```

Check if needed exists.

---

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

pair<int,int> twoSumBetter(vector<int>& arr, int k)
{
    unordered_map<int,int> mp;

    for(int i = 0; i < arr.size(); i++)
    {
        int needed = k - arr[i];

        if(mp.find(needed) != mp.end())
        {
            return {mp[needed], i};
        }

        mp[arr[i]] = i;
    }

    return {-1,-1};
}

int main()
{
    vector<int> arr = {2,6,5,8,11};
    int k = 14;

    pair<int,int> ans = twoSumBetter(arr,k);

    cout << ans.first << " " << ans.second;
}
```

---

## Complexity

Time → **O(n)**
Space → **O(n)**

---

# 3. Optimal Approach (Two Pointers)

## Idea

Works only if **array is sorted**.

1. Left pointer at start
2. Right pointer at end
3. Move pointers based on sum.

---

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

bool twoSumOptimal(vector<int>& arr, int k)
{
    sort(arr.begin(), arr.end());

    int left = 0;
    int right = arr.size()-1;

    while(left < right)
    {
        int sum = arr[left] + arr[right];

        if(sum == k)
            return true;

        else if(sum < k)
            left++;

        else
            right--;
    }

    return false;
}

int main()
{
    vector<int> arr = {2,6,5,8,11};
    int k = 14;

    cout << twoSumOptimal(arr,k);
}
```

---

# Complexity Comparison

| Approach     | Time       | Space | Notes         |
| ------------ | ---------- | ----- | ------------- |
| Brute        | O(n²)      | O(1)  | Basic         |
| HashMap      | O(n)       | O(n)  | Most common   |
| Two Pointers | O(n log n) | O(1)  | Sorted arrays |

---

# Interview Tips ⭐

### Pattern Recognition

If interviewer says:

> "Find two numbers whose sum = K"

Think:

```
HashMap
```

---

# Common Variations

### Variant 1

Return indices → HashMap

### Variant 2

Return YES/NO → Two pointers or HashMap

### Variant 3

Sorted array → Two pointers

---
