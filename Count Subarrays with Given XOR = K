# Count Subarrays with Given XOR = K

## Problem

Given an array and a number **K**, count the number of subarrays whose **XOR = K**.

---

### Example

```
Input:
arr = [4,2,2,6,4]
K = 6

Output:
4
```

Explanation:
Subarrays with XOR = 6:

```
[4,2]
[2,2,6]
[6]
[4,2,2,6,4]
```

---

# 1. Brute Force Approach

## Idea

Check all subarrays and compute XOR.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int countXorBrute(vector<int>& arr, int k)
{
    int n = arr.size();
    int count = 0;

    for(int i = 0; i < n; i++)
    {
        int xorr = 0;

        for(int j = i; j < n; j++)
        {
            xorr ^= arr[j];

            if(xorr == k)
                count++;
        }
    }

    return count;
}

int main()
{
    vector<int> arr = {4,2,2,6,4};
    int k = 6;

    cout << countXorBrute(arr, k);
}
```

### Complexity

Time → **O(n²)**
Space → **O(1)**

---

# 2. Optimal Approach (Prefix XOR + HashMap) ⭐

## Key Idea

Let:

```
prefixXor = xor from 0 to i
```

We want:

```
subarray XOR = K
```

So:

```
prefixXor ^ previousXor = K
```

Rearrange:

```
previousXor = prefixXor ^ K
```

---

## Algorithm

1. Maintain prefix XOR
2. Check if `(prefixXor ^ K)` exists in map
3. Add its frequency to count
4. Store prefixXor in map

---

# Optimal C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int countXorOptimal(vector<int>& arr, int k)
{
    unordered_map<int,int> mp;

    int xorr = 0;
    int count = 0;

    mp[0] = 1;  // important

    for(int x : arr)
    {
        xorr ^= x;

        int needed = xorr ^ k;

        if(mp.find(needed) != mp.end())
        {
            count += mp[needed];
        }

        mp[xorr]++;
    }

    return count;
}

int main()
{
    vector<int> arr = {4,2,2,6,4};
    int k = 6;

    cout << countXorOptimal(arr, k);
}
```

---

# Dry Run

```
arr = [4,2,2,6,4]
K = 6
```

| Element | XOR | needed (xor^k) | count |
| ------- | --- | -------------- | ----- |
| 4       | 4   | 2              | 0     |
| 2       | 6   | 0              | 1     |
| 2       | 4   | 2              | 1     |
| 6       | 2   | 4              | 2     |
| 4       | 6   | 0              | 4     |

---

# Complexity

Time → **O(n)**
Space → **O(n)**

---

# Interview Pattern ⭐

If question says:

```
Count subarrays with XOR = K
```

Think:

```
Prefix XOR + HashMap
```

---

# Important Difference

| Problem | Formula |
| ------- | ------- |
| Sum K   | sum - k |
| XOR K   | xor ^ k |

---

# Key Trick to Remember

```
sum → subtraction
xor → XOR again
```
