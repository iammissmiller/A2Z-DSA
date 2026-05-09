# Count Occurrences in a Sorted Array

## Problem Statement

Given a **sorted array** and a target `x`, count how many times `x` appears in the array.

Example:

```text id="r9h5zw"
arr = [1,2,2,2,3,4]
x = 2

Output = 3
```

---

# Key Observation

Since the array is sorted:

* all occurrences of `x` appear together
* if we find:

  * first occurrence
  * last occurrence

then:

```text id="j2tw8m"
count = last - first + 1
```

---

# 1. Brute Force Approach

## Idea

Traverse the entire array and count every occurrence.

---

## Code (C++)

```cpp id="p0s2yk"
int countOccurrences(vector<int>& arr, int x) {

    int count = 0;

    for(int i = 0; i < arr.size(); i++) {

        if(arr[i] == x)
            count++;
    }

    return count;
}
```

---

## Time Complexity

```text id="yx66jw"
O(n)
```

## Space Complexity

```text id="b2ls4o"
O(1)
```

---

# 2. Better Approach

## Idea

Use:

* first occurrence
* last occurrence

with linear search.

---

## Algorithm

```text id="84nl0f"
Find first index of x
Find last index of x

count = last - first + 1
```

Still linear in worst case.

---

# 3. Optimal Approach — Binary Search

Because the array is sorted, we can use binary search.

---

# Step 1 — Find First Occurrence

## Intuition

When:

```text id="w0e95d"
arr[mid] == x
```

store answer and continue LEFT.

Why?

Because maybe another occurrence exists earlier.

---

## Code

```cpp id="gupn5u"
int firstOccurrence(vector<int>& arr, int x) {

    int low = 0;
    int high = arr.size() - 1;

    int ans = -1;

    while(low <= high) {

        int mid = low + (high - low) / 2;

        if(arr[mid] == x) {
            ans = mid;
            high = mid - 1;
        }

        else if(arr[mid] < x) {
            low = mid + 1;
        }

        else {
            high = mid - 1;
        }
    }

    return ans;
}
```

---

# Step 2 — Find Last Occurrence

## Intuition

When:

```text id="ttk8q6"
arr[mid] == x
```

store answer and continue RIGHT.

Why?

Because maybe another occurrence exists later.

---

## Code

```cpp id="pwsb5s"
int lastOccurrence(vector<int>& arr, int x) {

    int low = 0;
    int high = arr.size() - 1;

    int ans = -1;

    while(low <= high) {

        int mid = low + (high - low) / 2;

        if(arr[mid] == x) {
            ans = mid;
            low = mid + 1;
        }

        else if(arr[mid] < x) {
            low = mid + 1;
        }

        else {
            high = mid - 1;
        }
    }

    return ans;
}
```

---

# Final Optimal Solution

```cpp id="lgix6m"
int countOccurrences(vector<int>& arr, int x) {

    int first = firstOccurrence(arr, x);

    // element not found
    if(first == -1)
        return 0;

    int last = lastOccurrence(arr, x);

    return last - first + 1;
}
```

---

# Time Complexity

Two binary searches:

```text id="j9fh1n"
O(log n) + O(log n)
= O(log n)
```

---

# Space Complexity

```text id="0lhf1f"
O(1)
```

---

# Dry Run

```text id="5srry4"
arr = [1,2,2,2,3,4]
x = 2
```

---

# First Occurrence

Binary search finds:

```text id="f9fpz5"
first = 1
```

---

# Last Occurrence

Binary search finds:

```text id="1rfq0z"
last = 3
```

---

# Count

```text id="8ub2je"
count = 3 - 1 + 1
      = 3
```

---

# STL Approach (C++)

Using:

* `lower_bound()`
* `upper_bound()`

---

# Concepts

## Lower Bound

First index where:

```text id="5o7y0f"
arr[i] >= x
```

## Upper Bound

First index where:

```text id="09jlwm"
arr[i] > x
```

---

# Formula

```text id="j0l4hh"
count = upper_bound - lower_bound
```

---

# STL Code

```cpp id="50jlwm"
int countOccurrences(vector<int>& arr, int x) {

    int first = lower_bound(arr.begin(), arr.end(), x) - arr.begin();

    int last = upper_bound(arr.begin(), arr.end(), x) - arr.begin();

    return last - first;
}
```

---

# Why This Works

Example:

```text id="tfr1dq"
arr = [1,2,2,2,3]
```

```text id="cn7p4z"
lower_bound(2) -> index 1
upper_bound(2) -> index 4
```

So:

```text id="hq0m1p"
4 - 1 = 3 occurrences
```

---

# Important Pattern

This binary search pattern appears in:

* First & last occurrence
* Lower bound
* Upper bound
* Search insert position
* Frequency counting in sorted arrays

---

# Common Mistakes

## 1. Forgetting “not found” case

If:

```text id="h29gpk"
first == -1
```

then count should be:

```text id="mkjlwm"
0
```

---

## 2. Returning immediately when found

Wrong:

```cpp id="vcjlwm"
if(arr[mid] == x)
    return mid;
```

You must continue searching.

---
