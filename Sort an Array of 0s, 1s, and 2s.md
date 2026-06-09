# Sort an Array of 0s, 1s, and 2s

This is a classic **array problem** often called the **Dutch National Flag Algorithm**.

### Problem

Given an array containing only **0, 1, and 2**, sort it **without using a sorting algorithm**.

Example:

```
Input:  [2, 0, 2, 1, 1, 0]
Output: [0, 0, 1, 1, 2, 2]
```

---

# 1. Brute Force Approach

### Idea

Simply sort the array using a built-in sort.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int main()
{
    vector<int> arr = {2,0,2,1,1,0};

    sort(arr.begin(), arr.end());

    for(int x : arr)
        cout << x << " ";

    return 0;
}
```

### Complexity

Time → **O(n log n)**
Space → **O(1)**

---

# 2. Better Approach (Counting Method)

### Idea

Count how many **0s, 1s, and 2s** exist, then rewrite the array.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

void sortArray(vector<int>& arr)
{
    int count0 = 0, count1 = 0, count2 = 0;

    for(int x : arr)
    {
        if(x == 0) count0++;
        else if(x == 1) count1++;
        else count2++;
    }

    int i = 0;

    while(count0--) arr[i++] = 0;
    while(count1--) arr[i++] = 1;
    while(count2--) arr[i++] = 2;
}

int main()
{
    vector<int> arr = {2,0,2,1,1,0};

    sortArray(arr);

    for(int x : arr)
        cout << x << " ";
}
```

### Complexity

Time → **O(n)**
Space → **O(1)**

---

# 3. Optimal Approach (Dutch National Flag Algorithm) ⭐

### Idea

Use **three pointers**:

```
low   → position for 0
mid   → current element
high  → position for 2
```

### Rules

| Element | Action                       |
| ------- | ---------------------------- |
| 0       | swap(low, mid), low++, mid++ |
| 1       | mid++                        |
| 2       | swap(mid, high), high--      |

---

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

void sort012(vector<int>& arr)
{
    int low = 0;
    int mid = 0;
    int high = arr.size() - 1;

    while(mid <= high)
    {
        if(arr[mid] == 0)
        {
            swap(arr[low], arr[mid]);
            low++;
            mid++;
        }
        else if(arr[mid] == 1)
        {
            mid++;
        }
        else
        {
            swap(arr[mid], arr[high]);
            high--;
        }
    }
}

int main()
{
    vector<int> arr = {2,0,2,1,1,0};

    sort012(arr);

    for(int x : arr)
        cout << x << " ";
}
```

---

# Complexity (Optimal)

Time → **O(n)**
Space → **O(1)**

---

# Visualization

```
Initial:
2 0 2 1 1 0

low mid        high
 ↓   ↓          ↓

After processing:

0 0 1 1 2 2
```

---

# Interview Tip ⭐

If interviewer says:

> **Sort array of 0,1,2**

Immediately think:

```
Dutch National Flag Algorithm
```
