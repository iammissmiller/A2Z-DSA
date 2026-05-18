# Find Peak Element

## Problem

Given an array, find a peak element.

A peak element is an element that is:

```cpp
greater than its neighbours
```

Return the index of any peak element.

---

## Example 1

```cpp
arr = [1,2,3,1]

Answer = 2
```

Because:

```cpp
arr[2] = 3
```

is greater than:

```cpp
2 and 1
```

---

## Example 2

```cpp
arr = [1,2,1,3,5,6,4]

Answer = 1 or 5
```

Both are valid peaks.

---

# Brute Force Solution

## Idea

Check every element and see whether it is greater than neighbours.

---

## Code

```cpp
int findPeakElement(vector<int>& arr) {

    int n = arr.size();

    // single element
    if(n == 1)
        return 0;

    // first element
    if(arr[0] > arr[1])
        return 0;

    // last element
    if(arr[n-1] > arr[n-2])
        return n-1;

    // middle elements
    for(int i = 1; i < n-1; i++) {

        if(arr[i] > arr[i-1] && arr[i] > arr[i+1])
            return i;
    }

    return -1;
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

No meaningful intermediate solution exists.

Optimal approach is Binary Search.

---

# Optimal Solution — Binary Search

## Key Observation

If:

```cpp
arr[mid] < arr[mid+1]
```

then:

```cpp
peak exists on right side
```

Why?

Because array is increasing.

Eventually it must either:

```cpp
1. become a peak
OR
2. reach the end
```

---

## Similarly

If:

```cpp
arr[mid] > arr[mid+1]
```

then:

```cpp
peak exists on left side including mid
```

---

# Binary Search Logic

## Case 1

```cpp
arr[mid] < arr[mid+1]
```

Move right:

```cpp
low = mid + 1
```

---

## Case 2

```cpp
arr[mid] > arr[mid+1]
```

Move left:

```cpp
high = mid
```

---

# Optimal Code

```cpp
int findPeakElement(vector<int>& arr) {

    int low = 0;
    int high = arr.size() - 1;

    while(low < high) {

        int mid = low + (high - low) / 2;

        // increasing slope
        if(arr[mid] < arr[mid + 1]) {
            low = mid + 1;
        }

        // decreasing slope
        else {
            high = mid;
        }
    }

    return low;
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

# Dry Run

```cpp
arr = [1,2,3,1]
```

---

## Step 1

```cpp
low = 0
high = 3

mid = 1
arr[mid] = 2
arr[mid+1] = 3
```

Since:

```cpp
2 < 3
```

Peak lies on right side.

```cpp
low = mid + 1
```

---

## Step 2

```cpp
low = 2
high = 3

mid = 2
arr[mid] = 3
arr[mid+1] = 1
```

Since:

```cpp
3 > 1
```

Peak lies on left including mid.

```cpp
high = mid
```

---

## Final

```cpp
low = high = 2
```

Answer:

```cpp
2
```

---

# Why Binary Search Works

A peak always exists because:

```cpp
1. Increasing array → last element is peak

2. Decreasing array → first element is peak

3. Otherwise some turning point becomes peak
```

---
