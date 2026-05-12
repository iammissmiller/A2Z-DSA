# Find Minimum in Rotated Sorted Array - II

## Problem Statement

You are given:

* a sorted array rotated some number of times
* all elements are unique

Find the **minimum element**.

---

## Example
arr = [3,4,5,1,2]

Output = 1
```

---

## Another Example

arr = [4,5,6,7,0,1,2]

Output = 0
```

---

# Key Observation

Originally sorted array:

[0,1,2,4,5,6,7]
```

After rotation:

[4,5,6,7,0,1,2]
```

The minimum element is the:

pivot / breaking point
```

---

# Important Insight

In a rotated sorted array:

At least one half is always sorted
```

We use this property in binary search.

---

# 1. Brute Force Solution

## Idea

Traverse the entire array and keep track of minimum.

---

## Algorithm

mini = arr[0]

for every element:

    mini = min(mini, arr[i])
```

---

## Code (C++)

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

O(n)
```

## Space Complexity
O(1)
```

---

# 2. Better Solution

No meaningful intermediate solution exists here.

The optimal binary search is the main improvement.

---

# 3. Optimal Solution — Binary Search

---

# Core Intuition

We want to eliminate half the array each time.

Important observations:

---

## Observation 1

If entire search space is already sorted:

arr[low] <= arr[high]
```

then:

arr[low] is the minimum
```

Why?

Because sorted array’s first element is minimum.

---

## Observation 2

Check which half is sorted.

---

# Case 1 — Left Half Sorted

Condition:
arr[low] <= arr[mid]
```

This means:

left half is sorted
```

So minimum from left half is:

arr[low]
```

Store it.

Then move RIGHT:

low = mid + 1
```

because smaller element may exist there.

---

# Case 2 — Right Half Sorted

Else:

right half is sorted
```

Minimum candidate is:
arr[mid]
```

Store it.

Then move LEFT:

high = mid - 1
```

---

# Optimal Code (C++)

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

        // LEFT HALF SORTED
        if(arr[low] <= arr[mid]) {

            ans = min(ans, arr[low]);

            low = mid + 1;
        }

        // RIGHT HALF SORTED
        else {

            ans = min(ans, arr[mid]);

            high = mid - 1;
        }
    }

    return ans;
}
```

---

# Dry Run
arr = [4,5,6,7,0,1,2]
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

Minimum candidate:

ans = 4
```

Move right:

low = mid + 1
```

---

# Step 2

low = 4
high = 6
```

Now:

arr[low] <= arr[high]
0 <= 2
```

Entire portion sorted.

Minimum:

arr[low] = 0
```

Final answer:

0
```

---

# Time Complexity

Binary search:

O(log n)
```

---

# Space Complexity
O(1)
```

---

# Alternative Shorter Binary Search

Very popular approach.

---

## Intuition

Compare:
arr[mid] with arr[high]
```

---

## Logic

### If:
arr[mid] > arr[high]
```

minimum lies RIGHT.

### Else:

arr[mid] <= arr[high]
```

minimum lies LEFT including mid.

---

## Code

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

# Why This Works

If:

arr[mid] > arr[high]
```

then rotation point must be on right side.

Otherwise minimum lies on left including mid.

---

# Time Complexity
O(log n)
```

---

# Space Complexity

O(1)
```

