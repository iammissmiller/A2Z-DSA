# Find Out How Many Times the Array is Rotated

## Problem

Given a sorted array rotated `k` times, find the number of rotations.

Example:

```cpp
arr = [4,5,6,7,0,1,2]

Answer = 4
```

Because:

```cpp
Original:
[0,1,2,4,5,6,7]

After 4 rotations:
[4,5,6,7,0,1,2]
```

---

# Key Observation

```cpp
Number of rotations = index of minimum element
```

So the problem becomes:

```cpp
Find index of minimum element
```

---

# Brute Force Solution

## Idea

Traverse the entire array and find the minimum element along with its index.

---

## Code

```cpp
int countRotations(vector<int>& arr) {

    int mini = arr[0];
    int index = 0;

    for(int i = 1; i < arr.size(); i++) {

        if(arr[i] < mini) {
            mini = arr[i];
            index = i;
        }
    }

    return index;
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

If array is already sorted:

```cpp
arr[0] <= arr[n-1]
```

then it is rotated 0 times.

Otherwise linearly find the breaking point:

```cpp
arr[i] < arr[i-1]
```

---

## Code

```cpp
int countRotations(vector<int>& arr) {

    int n = arr.size();

    // already sorted
    if(arr[0] <= arr[n-1])
        return 0;

    for(int i = 1; i < n; i++) {

        if(arr[i] < arr[i-1])
            return i;
    }

    return 0;
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

```cpp
Index of minimum element = number of rotations
```

We use binary search to find the minimum element index.

---

# Binary Search Logic

## Case 1 — Left Half Sorted

```cpp
arr[low] <= arr[mid]
```

Meaning:

```cpp
left half is sorted
```

So minimum candidate is:

```cpp
arr[low]
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

Minimum candidate:

```cpp
arr[mid]
```

Move left:

```cpp
high = mid - 1
```

---

# Optimal Code

```cpp
int countRotations(vector<int>& arr) {

    int low = 0;
    int high = arr.size() - 1;

    int mini = INT_MAX;
    int index = -1;

    while(low <= high) {

        // already sorted
        if(arr[low] <= arr[high]) {

            if(arr[low] < mini) {
                mini = arr[low];
                index = low;
            }

            break;
        }

        int mid = low + (high - low) / 2;

        // left half sorted
        if(arr[low] <= arr[mid]) {

            if(arr[low] < mini) {
                mini = arr[low];
                index = low;
            }

            low = mid + 1;
        }

        // right half sorted
        else {

            if(arr[mid] < mini) {
                mini = arr[mid];
                index = mid;
            }

            high = mid - 1;
        }
    }

    return index;
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
int countRotations(vector<int>& arr) {

    int low = 0;
    int high = arr.size() - 1;

    while(low < high) {

        int mid = low + (high - low) / 2;

        // minimum lies right
        if(arr[mid] > arr[high]) {
            low = mid + 1;
        }

        // minimum lies left including mid
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
arr = [4,5,6,7,0,1,2]
```

## Step 1

```cpp
low = 0
high = 6

mid = 3
arr[mid] = 7
arr[high] = 2
```

Since:

```cpp
7 > 2
```

minimum lies right.

```cpp
low = mid + 1
```

---

## Step 2

```cpp
low = 4
high = 6

mid = 5
arr[mid] = 1
arr[high] = 2
```

Since:

```cpp
1 <= 2
```

minimum lies left including mid.

```cpp
high = mid
```

Eventually:

```cpp
low = 4
```

Answer:

```cpp
4 rotations
```

---

# Important Points

```cpp
1. Rotations = index of minimum element

2. At least one half is always sorted

3. Compare arr[mid] with arr[high]

4. Use high = mid
   because mid itself can be minimum
```

---
