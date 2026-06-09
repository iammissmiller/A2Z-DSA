# Next Permutation

## Problem

Given an array representing a **permutation of numbers**, find the **next lexicographically greater permutation**.

If no next permutation exists (array is in descending order), return the **smallest permutation (sorted ascending)**.

---

### Example 1

```
Input:  [1,2,3]
Output: [1,3,2]
```

### Example 2

```
Input:  [3,2,1]
Output: [1,2,3]
```

### Example 3

```
Input:  [1,1,5]
Output: [1,5,1]
```

---

# Key Idea

The next permutation is the **next bigger arrangement of numbers**.

Steps:

1. Find the **breakpoint** (first element from right where `arr[i] < arr[i+1]`)
2. Find the **next greater element** from right
3. Swap them
4. Reverse the right part

---

# Optimal Algorithm

### Step-by-step

Example:

```
1 2 3 6 5 4
```

### Step 1: Find breakpoint

```
3 < 6  → index = 2
```

### Step 2: Find next greater element

```
swap 3 with 4
```

Array becomes:

```
1 2 4 6 5 3
```

### Step 3: Reverse remaining part

```
1 2 4 3 5 6
```

---

# C++ Implementation

```cpp
#include <bits/stdc++.h>
using namespace std;

void nextPermutation(vector<int>& arr)
{
    int n = arr.size();
    int index = -1;

    // Step 1: find breakpoint
    for(int i = n-2; i >= 0; i--)
    {
        if(arr[i] < arr[i+1])
        {
            index = i;
            break;
        }
    }

    // if no breakpoint
    if(index == -1)
    {
        reverse(arr.begin(), arr.end());
        return;
    }

    // Step 2: find next greater element
    for(int i = n-1; i > index; i--)
    {
        if(arr[i] > arr[index])
        {
            swap(arr[i], arr[index]);
            break;
        }
    }

    // Step 3: reverse right side
    reverse(arr.begin() + index + 1, arr.end());
}

int main()
{
    vector<int> arr = {1,2,3};

    nextPermutation(arr);

    for(int x : arr)
        cout << x << " ";
}
```

---

# Complexity

Time → **O(n)**
Space → **O(1)**

---

# Visualization

Example:

```
2 1 5 4 3 0 0
```

Step 1:

```
1 < 5 → breakpoint
```

Step 2:

```
swap 1 with 3
```

Step 3:

```
reverse right side
```

Result:

```
2 3 0 0 1 4 5
```

---

# Interview Tip

If interviewer says:

```
Next lexicographical permutation
```

Think immediately:

```
Breakpoint → Swap → Reverse
```

---

# Important Fact

This exact algorithm is used internally in:

* `next_permutation()` from the C++ STL.

Example:

```cpp
next_permutation(arr.begin(), arr.end());
```

---
