# Leaders in an Array

## Problem

An element in the array is called a **leader** if it is **greater than all the elements to its right**.

The **rightmost element is always a leader**.

---

### Example

```text
Input:
arr = [10, 22, 12, 3, 0, 6]

Output:
[22, 12, 6]
```

Explanation:

* **22** > all elements to its right
* **12** > 3,0,6
* **6** is the last element

---

# 1. Brute Force Approach

## Idea

For every element, check all elements to its right.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> leadersBrute(vector<int>& arr)
{
    int n = arr.size();
    vector<int> ans;

    for(int i = 0; i < n; i++)
    {
        bool leader = true;

        for(int j = i+1; j < n; j++)
        {
            if(arr[j] > arr[i])
            {
                leader = false;
                break;
            }
        }

        if(leader)
            ans.push_back(arr[i]);
    }

    return ans;
}

int main()
{
    vector<int> arr = {10,22,12,3,0,6};

    vector<int> ans = leadersBrute(arr);

    for(int x : ans)
        cout << x << " ";
}
```

### Complexity

Time → **O(n²)**
Space → **O(n)**

---

# 2. Optimal Approach (Right-to-Left Traversal) ⭐

## Idea

Traverse from the **right side** and track the **maximum element seen so far**.

If current element > max → it is a **leader**.

---

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> leadersOptimal(vector<int>& arr)
{
    int n = arr.size();
    vector<int> ans;

    int maxRight = INT_MIN;

    for(int i = n-1; i >= 0; i--)
    {
        if(arr[i] > maxRight)
        {
            ans.push_back(arr[i]);
            maxRight = arr[i];
        }
    }

    reverse(ans.begin(), ans.end());

    return ans;
}

int main()
{
    vector<int> arr = {10,22,12,3,0,6};

    vector<int> ans = leadersOptimal(arr);

    for(int x : ans)
        cout << x << " ";
}
```

---

# Complexity

Time → **O(n)**
Space → **O(n)**

---

# Dry Run

Array:

```
10 22 12 3 0 6
```

Traverse from right:

| Element | MaxRight | Leader? |
| ------- | -------- | ------- |
| 6       | 6        | Yes     |
| 0       | 6        | No      |
| 3       | 6        | No      |
| 12      | 12       | Yes     |
| 22      | 22       | Yes     |
| 10      | 22       | No      |

Leaders:

```
22 12 6
```

---

# Interview Tip

If interviewer says:

```
Leader element in array
```

Think:

```
Traverse from right and keep max
```

---
