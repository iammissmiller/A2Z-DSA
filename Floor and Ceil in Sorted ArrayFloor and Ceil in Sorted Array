# Floor and Ceil in Sorted Array

## Problem Understanding

You are given:

* A **sorted array**
* A target value `x`

You need to find:

* **Floor** → greatest element ≤ `x`
* **Ceil** → smallest element ≥ `x`

Example:


arr = [1, 2, 4, 6, 10]
x = 5

Floor = 4
Ceil = 6
```

Another example:


arr = [1, 2, 8, 10]
x = 8

Floor = 8
Ceil = 8
```

---

# 1. Brute Force Approach

## Idea

Traverse the entire array and:

* keep updating floor whenever element ≤ x
* keep updating ceil whenever element ≥ x

Since array is sorted, this is unnecessary work, but it works.

---

## Algorithm

### Floor

```text
Initialize floor = -1

For every element:
    if arr[i] <= x:
        floor = arr[i]
```

### Ceil

```text
Initialize ceil = -1

For every element:
    if arr[i] >= x:
        ceil = arr[i]
        break
```

---

## Code (C++)

```cpp
pair<int, int> getFloorAndCeil(vector<int>& arr, int x) {
    int floorVal = -1;
    int ceilVal = -1;

    for (int i = 0; i < arr.size(); i++) {

        if (arr[i] <= x)
            floorVal = arr[i];

        if (arr[i] >= x) {
            ceilVal = arr[i];
            break;
        }
    }

    return {floorVal, ceilVal};
}
```

---

## Time Complexity

```text
O(n)
```

## Space Complexity

```text
O(1)
```

---

# 2. Better / Optimal Approach — Binary Search

Since the array is **sorted**, binary search is the best approach.

---

# Finding Floor using Binary Search

## Intuition

We need:

```text
greatest value <= x
```

Whenever:

```text
arr[mid] <= x
```

this can be a possible floor.

But maybe a larger valid floor exists on the right side.

So:

```text
store answer
move right
```

---

## Floor Algorithm

```text
ans = -1

while(low <= high):

    mid = (low + high)/2

    if arr[mid] <= x:
        ans = arr[mid]
        low = mid + 1

    else:
        high = mid - 1
```

---

# Finding Ceil using Binary Search

## Intuition

We need:

```text
smallest value >= x
```

Whenever:

```text
arr[mid] >= x
```

this can be a possible ceil.

But maybe a smaller valid ceil exists on the left side.

So:

```text
store answer
move left
```

---

## Ceil Algorithm

```text
ans = -1

while(low <= high):

    mid = (low + high)/2

    if arr[mid] >= x:
        ans = arr[mid]
        high = mid - 1

    else:
        low = mid + 1
```

---

# Optimal Combined Code (C++)

```cpp
pair<int, int> getFloorAndCeil(vector<int>& arr, int x) {

    int n = arr.size();

    int floorVal = -1;
    int ceilVal = -1;

    // Finding Floor
    int low = 0, high = n - 1;

    while (low <= high) {

        int mid = low + (high - low) / 2;

        if (arr[mid] <= x) {
            floorVal = arr[mid];
            low = mid + 1;
        }
        else {
            high = mid - 1;
        }
    }

    // Finding Ceil
    low = 0;
    high = n - 1;

    while (low <= high) {

        int mid = low + (high - low) / 2;

        if (arr[mid] >= x) {
            ceilVal = arr[mid];
            high = mid - 1;
        }
        else {
            low = mid + 1;
        }
    }

    return {floorVal, ceilVal};
}
```

---

# Time Complexity

Two binary searches:

```text
O(log n) + O(log n)
= O(log n)
```

---

# Space Complexity

```text
O(1)
```

---

# Dry Run

```text
arr = [1,2,4,6,10]
x = 5
```

## Floor

```text
mid = 4 -> valid floor
move right

mid = 6 -> too big
move left

Answer = 4
```

---

## Ceil

```text
mid = 4 -> too small
move right

mid = 6 -> valid ceil
move left

Answer = 6
```

---

# Important Observation

This problem is basically:

* **Floor = last smaller/equal element**
* **Ceil = first greater/equal element**

This pattern appears in:

* Lower Bound
* Upper Bound
* Search Insert Position
* First & Last Occurrence
* Binary Search on Answers

---

# Common Mistakes

## 1. Forgetting to store answer before moving

Wrong:

```cpp
low = mid + 1;
```

Correct:

```cpp
ans = arr[mid];
low = mid + 1;
```

---

## 2. Infinite loop

Always use:

```cpp
while(low <= high)
```

---

## 3. Mid overflow

Prefer:

```cpp
mid = low + (high - low) / 2;
```

instead of:

```cpp
(low + high) / 2
```

---
