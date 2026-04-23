# Count Inversions

## Problem

Given an array, count the number of **inversions**.

An inversion is a pair **(i, j)** such that:

```text
i < j  AND  arr[i] > arr[j]
```

---

### Example

```
Input:
arr = [5,3,2,4,1]

Output:
8
```

Explanation (pairs):

```
(5,3), (5,2), (5,4), (5,1),
(3,2), (3,1),
(2,1),
(4,1)
→ total = 8
```

---

# 1. Brute Force Approach

## Idea

Check all pairs.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int countInversionsBrute(vector<int>& arr)
{
    int n = arr.size();
    int count = 0;

    for(int i = 0; i < n; i++)
    {
        for(int j = i+1; j < n; j++)
        {
            if(arr[i] > arr[j])
                count++;
        }
    }

    return count;
}

int main()
{
    vector<int> arr = {5,3,2,4,1};

    cout << countInversionsBrute(arr);
}
```

### Complexity

* Time → **O(n²)**
* Space → **O(1)**

---

# 2. Optimal Approach (Merge Sort) ⭐

## Key Idea

While merging two sorted halves:

* If `left[i] > right[j]`
  → All remaining elements in left are greater than `right[j]`

So:

```text
count += (mid - i + 1)
```

---

# C++ Code (Most Important)

```cpp
#include <bits/stdc++.h>
using namespace std;

int merge(vector<int>& arr, int low, int mid, int high)
{
    vector<int> temp;
    int left = low;
    int right = mid + 1;
    int count = 0;

    while(left <= mid && right <= high)
    {
        if(arr[left] <= arr[right])
        {
            temp.push_back(arr[left]);
            left++;
        }
        else
        {
            temp.push_back(arr[right]);
            count += (mid - left + 1); // inversion count
            right++;
        }
    }

    while(left <= mid)
    {
        temp.push_back(arr[left]);
        left++;
    }

    while(right <= high)
    {
        temp.push_back(arr[right]);
        right++;
    }

    for(int i = low; i <= high; i++)
    {
        arr[i] = temp[i - low];
    }

    return count;
}

int mergeSort(vector<int>& arr, int low, int high)
{
    int count = 0;

    if(low >= high) return 0;

    int mid = (low + high) / 2;

    count += mergeSort(arr, low, mid);
    count += mergeSort(arr, mid+1, high);
    count += merge(arr, low, mid, high);

    return count;
}

int main()
{
    vector<int> arr = {5,3,2,4,1};

    cout << mergeSort(arr, 0, arr.size()-1);
}
```

---

# Complexity (Optimal)

* Time → **O(n log n)**
* Space → **O(n)**

---

# Dry Run Insight

Array:

```
[5,3,2,4,1]
```

Split:

```
[5,3,2]  [4,1]
```

During merge:

```
5 > 3 → +1
5 > 2 → +1
3 > 2 → +1
...
```

Total = 8

---

# Interview Tip ⭐

If interviewer says:

```text
count inversions
```

Think:

```text
merge sort
```

---

# Why Merge Sort?

Because:

* We need **order + counting**
* Merge step gives **efficient counting**

---
