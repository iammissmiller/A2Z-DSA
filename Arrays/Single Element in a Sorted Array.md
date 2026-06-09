# Single Element in a Sorted Array

## Problem

Given a sorted array where:

* every element appears exactly twice
* only one element appears once

Find the single element.

Example:

```cpp
arr = [1,1,2,2,3,4,4,5,5]

Answer = 3
```

---

# Brute Force Solution

## Idea

Count frequency of every element.

The element with frequency 1 is the answer.

---

## Code

```cpp
int singleNonDuplicate(vector<int>& arr) {

    int n = arr.size();

    for(int i = 0; i < n; i++) {

        int count = 0;

        for(int j = 0; j < n; j++) {

            if(arr[i] == arr[j])
                count++;
        }

        if(count == 1)
            return arr[i];
    }

    return -1;
}
```

---

## Time Complexity

```cpp
O(n^2)
```

## Space Complexity

```cpp
O(1)
```

---

# Better Solution — XOR

## Key Observation

```cpp
a ^ a = 0
a ^ 0 = a
```

All duplicate elements cancel out.

Only the single element remains.

---

## Code

```cpp
int singleNonDuplicate(vector<int>& arr) {

    int xorr = 0;

    for(int i = 0; i < arr.size(); i++) {
        xorr ^= arr[i];
    }

    return xorr;
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

In a perfect paired array:

```cpp
(even index, odd index)

(0,1)
(2,3)
(4,5)
```

Before the single element:

```cpp
first occurrence starts at even index
```

After the single element:

```cpp
first occurrence starts at odd index
```

This pattern helps us use binary search.

---

# Important Pattern

Example:

```cpp
arr = [1,1,2,2,3,4,4,5,5]
```

Indexes:

```cpp
0 1 2 3 4 5 6 7 8
```

Pairs before single element:

```cpp
(0,1)
(2,3)
```

After single element:

```cpp
(5,6)
(7,8)
```

Pattern breaks at the single element.

---

# Binary Search Logic

## Case 1

If:

```cpp
mid is even
arr[mid] == arr[mid+1]
```

then single element lies on RIGHT side.

---

## Case 2

If:

```cpp
mid is odd
arr[mid] == arr[mid-1]
```

then single element lies on RIGHT side.

---

## Otherwise

Single element lies on LEFT side including mid.

---

# Optimal Code

```cpp
int singleNonDuplicate(vector<int>& arr) {

    int low = 0;
    int high = arr.size() - 1;

    while(low < high) {

        int mid = low + (high - low) / 2;

        // make mid even
        if(mid % 2 == 1)
            mid--;

        // valid pair
        if(arr[mid] == arr[mid + 1]) {
            low = mid + 2;
        }

        // single element on left side
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

# Dry Run

```cpp
arr = [1,1,2,2,3,4,4,5,5]
```

---

## Step 1

```cpp
low = 0
high = 8

mid = 4
arr[mid] = 3
```

Check pair:

```cpp
arr[4] != arr[5]
```

Pattern broken.

Move left:

```cpp
high = mid
```

---

## Step 2

```cpp
low = 0
high = 4

mid = 2
```

Check:

```cpp
arr[2] == arr[3]
```

Valid pair.

Move right:

```cpp
low = mid + 2
```

---

## Step 3

```cpp
low = 4
high = 4
```

Answer:

```cpp
3
```

---
