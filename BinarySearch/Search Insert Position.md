# Search Insert Position

## Problem

Given a sorted array and a target `x`:

* If `x` exists → return its index
* Otherwise → return the index where it should be inserted to maintain sorted order

---

### Example 1

```id="v7h7sr"
Input:
arr = [1,3,5,6]
x = 5

Output:
2
```

---

### Example 2

```id="k48v5s"
Input:
arr = [1,3,5,6]
x = 2

Output:
1
```

---

### Example 3

```id="1n2z8o"
Input:
arr = [1,3,5,6]
x = 7

Output:
4
```

---

# Key Observation ⭐

This problem is exactly:

```id="qlrnt0"
Lower Bound of x
```

Because we need:

```id="w4kr2g"
first position where arr[i] >= x
```

---

# 1. Brute Force Approach

## Idea

Traverse and find first position ≥ x

### C++ Code

```cpp id="s3ohgm"
#include <bits/stdc++.h>
using namespace std;

int searchInsertBrute(vector<int>& arr, int x)
{
    for(int i = 0; i < arr.size(); i++)
    {
        if(arr[i] >= x)
            return i;
    }

    return arr.size();
}

int main()
{
    vector<int> arr = {1,3,5,6};
    int x = 2;

    cout << searchInsertBrute(arr, x);
}
```

### Complexity

* Time → **O(n)**
* Space → **O(1)**

---

# 2. Optimal Approach (Binary Search / Lower Bound) ⭐

## Idea

Find first index where:

```id="dgnjsi"
arr[mid] >= x
```

---

# C++ Code

```cpp id="m8wx6w"
#include <bits/stdc++.h>
using namespace std;

int searchInsert(vector<int>& arr, int x)
{
    int low = 0;
    int high = arr.size() - 1;
    int ans = arr.size();

    while(low <= high)
    {
        int mid = low + (high - low) / 2;

        if(arr[mid] >= x)
        {
            ans = mid;
            high = mid - 1;
        }
        else
        {
            low = mid + 1;
        }
    }

    return ans;
}

int main()
{
    vector<int> arr = {1,3,5,6};
    int x = 2;

    cout << searchInsert(arr, x);
}
```

---

# Complexity

* Time → **O(log n)**
* Space → **O(1)**

---

# Dry Run

```id="tl5jms"
arr = [1,3,5,6]
x = 2
```

| low | high | mid | arr[mid] | action         |
| --- | ---- | --- | -------- | -------------- |
| 0   | 3    | 1   | 3        | ans=1, go left |
| 0   | 0    | 0   | 1        | go right       |

Answer = **1**

---

# STL Shortcut

```cpp id="mb4bd6"
int index = lower_bound(arr.begin(), arr.end(), x) - arr.begin();
```

---

# Interview Pattern ⭐

| Problem                | Actually Means |
| ---------------------- | -------------- |
| Search Insert Position | Lower Bound    |

---

# Important Binary Search Patterns

| Problem          | Condition         |
| ---------------- | ----------------- |
| Lower Bound      | ≥ X               |
| Upper Bound      | > X               |
| Search Insert    | ≥ X               |
| First Occurrence | == X and go left  |
| Last Occurrence  | == X and go right |

---
