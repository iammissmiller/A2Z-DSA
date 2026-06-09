# Search in Rotated Sorted Array - I

## Problem Statement

You are given:

* a **sorted array**
* the array is rotated at some pivot
* all elements are unique
* a target `x`

Return the index of `x`.

If not found, return `-1`.

---

## Example
arr = [4,5,6,7,0,1,2]
x = 0

Output = 4
```

---

# Key Observation

Originally sorted array:

[0,1,2,4,5,6,7]
```

After rotation:

[4,5,6,7,0,1,2]
```

Important property:

At least one half is always sorted
```

This is the main trick.

---

# 1. Brute Force Solution

## Idea

Traverse the array and find the target.

---

## Algorithm

for every element:

    if arr[i] == x:
        return i

return -1
```

---

## Code (C++)

int search(vector<int>& arr, int x) {

    for(int i = 0; i < arr.size(); i++) {

        if(arr[i] == x)
            return i;
    }

    return -1;
}
```

---

## Time Complexity
O(n)
```

## Space Complexity

O(1)
```

---

# 2. Better Solution

There is no meaningful “better” solution between linear search and binary search here.

So the next improvement is the optimal binary search approach.

---

# 3. Optimal Solution — Modified Binary Search

## Core Intuition

Normal binary search works only on fully sorted arrays.

But here:

one half of the array is always sorted
```

We identify:

* which half is sorted
* whether target lies inside that half

Then eliminate the other half.

---

# Main Logic

At every step:

mid = (low + high)/2
```

Now check:

Is left half sorted?
```

Condition:

arr[low] <= arr[mid]
```

If true:

Left side is sorted
```

Now check whether target lies inside it.

---

# Case 1 — Left Half Sorted

Condition:

arr[low] <= arr[mid]
```

Now:

## If target lies inside left half
arr[low] <= x < arr[mid]
```

Move LEFT:

high = mid - 1
```

Otherwise:

low = mid + 1
```

---

# Case 2 — Right Half Sorted

Else:

Right half is sorted
```

Check:
arr[mid] < x <= arr[high]
```

If true:

low = mid + 1
```

Else:

high = mid - 1
```

---

# Optimal Code (C++)

int search(vector<int>& arr, int x) {

    int low = 0;
    int high = arr.size() - 1;

    while(low <= high) {

        int mid = low + (high - low) / 2;

        // target found
        if(arr[mid] == x)
            return mid;

        // LEFT HALF SORTED
        if(arr[low] <= arr[mid]) {

            // target exists in left half
            if(arr[low] <= x && x < arr[mid]) {
                high = mid - 1;
            }

            else {
                low = mid + 1;
            }
        }

        // RIGHT HALF SORTED
        else {

            // target exists in right half
            if(arr[mid] < x && x <= arr[high]) {
                low = mid + 1;
            }

            else {
                high = mid - 1;
            }
        }
    }

    return -1;
}
```

---

# Dry Run

arr = [4,5,6,7,0,1,2]
x = 0
```

---

# Step 1

low = 0
high = 6

mid = 3
arr[mid] = 7
```

Check:

arr[low] <= arr[mid]
4 <= 7
```

Left half sorted.

Now check:
Is 0 inside [4...7]?
NO
```

Move right:
low = mid + 1
```

---

# Step 2

low = 4
high = 6

mid = 5
arr[mid] = 1
```

Again left half sorted.

Check:

```text id="jlwm51"
0 inside [0...1]?
YES
```

Move left:

high = mid - 1
```

---

# Step 3

mid = 4
arr[mid] = 0
```

Found target.

Answer:
4
```

---

# Time Complexity

Binary search reduces search space by half:
O(log n)
```

---

# Space Complexity
O(1)
```

---

# Important Pattern

This problem teaches:

How to apply binary search on partially sorted arrays
```

Very important for:

* Minimum in rotated array
* Rotated array with duplicates
* Peak element
* Binary search on answers

---

# Common Mistakes

## 1. Forgetting equality

Correct:

```cpp id="jlwm58"
arr[low] <= arr[mid]
```

NOT:

```cpp id="jlwm59"
arr[low] < arr[mid]
```

---

## 2. Wrong target range condition

Correct:

```cpp id="jlwm60"
arr[low] <= x && x < arr[mid]
```

Carefully observe boundaries.

---

## 3. Infinite loop

Always use:

```cpp id="jlwm61"
while(low <= high)
```

---
