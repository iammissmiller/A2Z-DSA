# Kadane’s Algorithm – Maximum Subarray Sum

## Problem

Given an array of integers (can include **negative numbers**), find the **maximum sum of any contiguous subarray**.

### Example

```
Input:
arr = [-2,1,-3,4,-1,2,1,-5,4]

Output:
6
```

Explanation:

```
Subarray = [4,-1,2,1]
Sum = 6
```

---

# 1. Brute Force Approach

## Idea

Check every possible subarray and calculate the sum.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int maxSubarrayBrute(vector<int>& arr)
{
    int n = arr.size();
    int maxSum = INT_MIN;

    for(int i = 0; i < n; i++)
    {
        for(int j = i; j < n; j++)
        {
            int sum = 0;

            for(int k = i; k <= j; k++)
            {
                sum += arr[k];
            }

            maxSum = max(maxSum, sum);
        }
    }

    return maxSum;
}

int main()
{
    vector<int> arr = {-2,1,-3,4,-1,2,1,-5,4};

    cout << maxSubarrayBrute(arr);
}
```

### Complexity

Time → **O(n³)**
Space → **O(1)**

---

# 2. Better Approach

## Idea

Remove the innermost loop and accumulate sum.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int maxSubarrayBetter(vector<int>& arr)
{
    int n = arr.size();
    int maxSum = INT_MIN;

    for(int i = 0; i < n; i++)
    {
        int sum = 0;

        for(int j = i; j < n; j++)
        {
            sum += arr[j];
            maxSum = max(maxSum, sum);
        }
    }

    return maxSum;
}

int main()
{
    vector<int> arr = {-2,1,-3,4,-1,2,1,-5,4};

    cout << maxSubarrayBetter(arr);
}
```

### Complexity

Time → **O(n²)**
Space → **O(1)**

---

# 3. Optimal Approach – Kadane’s Algorithm ⭐

## Idea

If the sum becomes negative, **reset it to 0** because a negative sum cannot help future subarrays.

Steps:

1. Add current element to sum
2. Update maximum sum
3. If sum becomes negative → reset to 0

---

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int maxSubarrayKadane(vector<int>& arr)
{
    int sum = 0;
    int maxSum = INT_MIN;

    for(int x : arr)
    {
        sum += x;

        maxSum = max(maxSum, sum);

        if(sum < 0)
            sum = 0;
    }

    return maxSum;
}

int main()
{
    vector<int> arr = {-2,1,-3,4,-1,2,1,-5,4};

    cout << maxSubarrayKadane(arr);
}
```

---

# Complexity (Optimal)

Time → **O(n)**
Space → **O(1)**

---

# Dry Run

Array:

```
-2 1 -3 4 -1 2 1 -5 4
```

| Element | Current Sum | Max Sum |
| ------- | ----------- | ------- |
| -2      | -2 → reset  | -2      |
| 1       | 1           | 1       |
| -3      | -2 → reset  | 1       |
| 4       | 4           | 4       |
| -1      | 3           | 4       |
| 2       | 5           | 5       |
| 1       | 6           | 6       |
| -5      | 1           | 6       |
| 4       | 5           | 6       |

Final Answer → **6**

---

# Interview Tip ⭐

If interviewer says:

```
maximum subarray sum
```

Immediately think:

```
Kadane's Algorithm
```

This is **one of the most famous algorithms in DSA**.

---
