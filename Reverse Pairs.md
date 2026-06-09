# Reverse Pairs

## Problem

Given an array, count the number of **reverse pairs**.

A reverse pair is:

```text
i < j  AND  arr[i] > 2 * arr[j]
```

---

### Example

```text
Input:
arr = [1,3,2,3,1]

Output:
2
```

Explanation:

```
(3,1) and (3,1)
```

---

# 1. Brute Force Approach

## Idea

Check all pairs.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int reversePairsBrute(vector<int>& arr)
{
    int n = arr.size();
    int count = 0;

    for(int i = 0; i < n; i++)
    {
        for(int j = i+1; j < n; j++)
        {
            if(arr[i] > 2LL * arr[j])
                count++;
        }
    }

    return count;
}

int main()
{
    vector<int> arr = {1,3,2,3,1};
    cout << reversePairsBrute(arr);
}
```

---

### Complexity

* Time → **O(n²)**
* Space → **O(1)**

---

# 2. Optimal Approach (Merge Sort) ⭐

## Key Idea

Same as inversion count but condition changes:

```text
arr[i] > 2 * arr[j]
```

We:

1. Divide array (merge sort)
2. Before merging → count reverse pairs
3. Then merge normally

---

# Important Trick

For each element in left:

* Move pointer in right until condition fails

---

# C++ Code (Most Important)

```cpp
#include <bits/stdc++.h>
using namespace std;

int countPairs(vector<int>& arr, int low, int mid, int high)
{
    int right = mid + 1;
    int count = 0;

    for(int i = low; i <= mid; i++)
    {
        while(right <= high && arr[i] > 2LL * arr[right])
            right++;

        count += (right - (mid + 1));
    }

    return count;
}

void merge(vector<int>& arr, int low, int mid, int high)
{
    vector<int> temp;
    int left = low;
    int right = mid + 1;

    while(left <= mid && right <= high)
    {
        if(arr[left] <= arr[right])
            temp.push_back(arr[left++]);
        else
            temp.push_back(arr[right++]);
    }

    while(left <= mid)
        temp.push_back(arr[left++]);

    while(right <= high)
        temp.push_back(arr[right++]);

    for(int i = low; i <= high; i++)
        arr[i] = temp[i - low];
}

int mergeSort(vector<int>& arr, int low, int high)
{
    if(low >= high) return 0;

    int mid = (low + high) / 2;

    int count = 0;

    count += mergeSort(arr, low, mid);
    count += mergeSort(arr, mid+1, high);

    count += countPairs(arr, low, mid, high);

    merge(arr, low, mid, high);

    return count;
}

int reversePairs(vector<int>& arr)
{
    return mergeSort(arr, 0, arr.size()-1);
}

int main()
{
    vector<int> arr = {1,3,2,3,1};

    cout << reversePairs(arr);
}
```

---

# Complexity

* Time → **O(n log n)**
* Space → **O(n)**

---

# Dry Run

```text
arr = [1,3,2,3,1]
```

During merge:

```
3 > 2*1 → yes
3 > 2*1 → yes
```

Total = **2**

---

# Key Difference vs Inversion Count

| Problem      | Condition           |
| ------------ | ------------------- |
| Inversion    | arr[i] > arr[j]     |
| Reverse Pair | arr[i] > 2 * arr[j] |

---
