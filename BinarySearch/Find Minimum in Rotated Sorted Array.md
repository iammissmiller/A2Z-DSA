# Find Minimum in Rotated Sorted Array

## Problem

Given a sorted array rotated some number of times, find the minimum element.

All elements are unique.

Example:

```cpp
arr = [4,5,6,7,0,1,2]

Answer = 0
```

---

# Brute Force Solution

## Idea

Traverse the entire array and keep track of the minimum.

---

## Code

```cpp
int findMin(vector<int>& arr) {

    int mini = arr[0];

    for(int i = 1; i < arr.size(); i++) {
        mini = min(mini, arr[i]);
    }

    return mini;
}
```

---

## Time Complexity

```cpp
O(n)
```

## Space Complexity

```cpp
O(1)
```

---

# Better Solution

## Idea

If the array is already sorted:

```cpp
arr[0] < arr[n-1]
```

then the first element itself is the minimum.

Otherwise linearly find the breaking point where:

```cpp
arr[i] < arr[i-1]
```

---

## Code

```cpp
int findMin(vector<int>& arr) {

    int n = arr.size();

    // already sorted
    if(arr[0] < arr[n-1])
        return arr[0];

    for(int i = 1; i < n; i++) {

        if(arr[i] < arr[i-1])
            return arr[i];
    }

    return arr[0];
}
```

---

## Time Complexity

```cpp
O(n)
```

## Space Complexity

```cpp
O(1)
```

---

# Optimal Solution — Binary Search

## Key Observation

In a rotated sorted array:

```cpp
At least one half is always sorted
```

---

## Important Logic

### If current search space is sorted:

```cpp
arr[low] <= arr[high]
```

then:

```cpp
arr[low] is the minimum
```

---

# Binary Search Logic

## Case 1 — Left Half Sorted

```cpp
arr[low] <= arr[mid]
```

Meaning left half is sorted.

So:

```cpp
arr[low] is a possible minimum
```

Move right:

```cpp
low = mid + 1
```

---

## Case 2 — Right Half Sorted

Else:

```cpp
right half is sorted
```

So:

```cpp
arr[mid] is a possible minimum
```

Move left:

```cpp
high = mid - 1
```

---

## Code

```cpp
int findMin(vector<int>& arr) {

    int low = 0;
    int high = arr.size() - 1;

    int ans = INT_MAX;

    while(low <= high) {

        // already sorted
        if(arr[low] <= arr[high]) {
            ans = min(ans, arr[low]);
            break;
        }

        int mid = low + (high - low) / 2;

        // left half sorted
        if(arr[low] <= arr[mid]) {

            ans = min(ans, arr[low]);

            low = mid + 1;
        }

        // right half sorted
        else {

            ans = min(ans, arr[mid]);

            high = mid - 1;
        }
    }

    return ans;
}
```

---

## Time Complexity

```cpp
O(log n)
```

## Space Complexity

```cpp
O(1)
```

---

# Cleaner Optimal Approach

## Idea

Compare:

```cpp
arr[mid] with arr[high]
```

---

## Logic

### If:

```cpp
arr[mid] > arr[high]
```

minimum lies on right side.

### Else:

```cpp
arr[mid] <= arr[high]
```

minimum lies on left side including mid.

---

## Code

```cpp
int findMin(vector<int>& arr) {

    int low = 0;
    int high = arr.size() - 1;

    while(low < high) {

        int mid = low + (high - low) / 2;

        if(arr[mid] > arr[high]) {
            low = mid + 1;
        }

        else {
            high = mid;
        }
    }

    return arr[low];
}
```

---

## Time Complexity

```cpp
O(log n)
```

## Space Complexity

```cpp
O(1)
```

---
