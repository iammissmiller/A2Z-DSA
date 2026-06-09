# Search X in Sorted Array

## Problem

Given a **sorted array**, find the index of element **X**.
If not found → return **-1**.

---

### Example

```
Input:
arr = [1,3,5,7,9]
X = 7

Output:
3
```

---

# 1. Brute Force (Linear Search)

## Idea

Traverse the array and check each element.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int linearSearch(vector<int>& arr, int x)
{
    for(int i = 0; i < arr.size(); i++)
    {
        if(arr[i] == x)
            return i;
    }
    return -1;
}

int main()
{
    vector<int> arr = {1,3,5,7,9};
    int x = 7;

    cout << linearSearch(arr, x);
}
```

### Complexity

* Time → **O(n)**
* Space → **O(1)**

---

# 2. Optimal Approach (Binary Search) ⭐

## Idea

Since array is sorted:

* Divide search space in half each time

---

## Steps

1. mid = (low + high) / 2
2. Compare arr[mid] with X
3. Move left or right accordingly

---

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int binarySearch(vector<int>& arr, int x)
{
    int low = 0;
    int high = arr.size() - 1;

    while(low <= high)
    {
        int mid = low + (high - low) / 2;

        if(arr[mid] == x)
            return mid;

        else if(arr[mid] < x)
            low = mid + 1;

        else
            high = mid - 1;
    }

    return -1;
}

int main()
{
    vector<int> arr = {1,3,5,7,9};
    int x = 7;

    cout << binarySearch(arr, x);
}
```

---

# Complexity

* Time → **O(log n)**
* Space → **O(1)**

---

# Dry Run

```
arr = [1,3,5,7,9], x = 7

low=0, high=4
mid=2 → 5 < 7 → go right

low=3, high=4
mid=3 → 7 == 7 → found
```

---

# Important Variations (Very Asked)

Once you understand this, next questions are:

1. First occurrence
2. Last occurrence
3. Lower bound
4. Upper bound
5. Search in rotated array

---

# Common Mistakes

❌ Using `(low + high)/2` → overflow risk
✅ Use:

```cpp
mid = low + (high - low) / 2;
```

---
