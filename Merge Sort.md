## 1️ What is Merge Sort?

**Merge Sort** is a **Divide and Conquer** sorting algorithm.

### Core idea

1. **Divide** the array into two halves
2. **Sort** each half recursively
3. **Merge** the two sorted halves into one sorted array

It keeps dividing until each subarray has **only one element** (which is already sorted).

---

## 2️ Why Merge Sort?

* Guaranteed **O(n log n)** time complexity
* Very stable and predictable
* Works well for large data sets

### Drawback

* Uses **extra space** (not in-place)

---

## 3️ How your code works (function by function)

---

###  `mergeSort(arr, left, right)`

```cpp
void mergeSort(int arr[], int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;

        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);

        merge(arr, left, mid, right);
    }
}
```

#### What it does

* Finds the middle index
* Recursively sorts:

  * left half → `left to mid`
  * right half → `mid+1 to right`
* Merges both halves

This is the **divide** part.

---

###  `merge(arr, left, mid, right)`

```cpp
void merge(int arr[], int left, int mid, int right)
```

#### What it does

* Merges **two already sorted subarrays**:

  * `arr[left .. mid]`
  * `arr[mid+1 .. right]`

Steps inside:

1. Create temporary arrays `L[]` and `R[]`
2. Copy data into them
3. Compare elements and merge back into `arr[]`
4. Copy remaining elements

This is the **conquer** part.

---

## 4️ Now let’s dry-run YOUR example

### Input

```cpp
arr = {38, 27, 43, 3, 9, 82, 10}
```

---

## Step 1: Recursive division

```
[38, 27, 43, 3, 9, 82, 10]
           ↓
[38, 27, 43, 3]     [9, 82, 10]
```

---

### Left half: `[38, 27, 43, 3]`

```
[38, 27]    [43, 3]
```

#### Sort `[38, 27]`

```
[38] [27] → merge → [27, 38]
```

#### Sort `[43, 3]`

```
[43] [3] → merge → [3, 43]
```

#### Merge `[27, 38]` and `[3, 43]`

```
Compare 27 and 3 → 3
Compare 27 and 43 → 27
Compare 38 and 43 → 38
Remaining → 43
```

Result:

```
[3, 27, 38, 43]
```

---

### Right half: `[9, 82, 10]`

```
[9]     [82, 10]
```

#### Sort `[82, 10]`

```
[82] [10] → merge → [10, 82]
```

#### Merge `[9]` and `[10, 82]`

```
Compare 9 and 10 → 9
Remaining → 10, 82
```

Result:

```
[9, 10, 82]
```

---

## Step 2: Final merge

Merge:

```
[3, 27, 38, 43] and [9, 10, 82]
```

Step-by-step:

```
3 < 9 → 3
9 < 27 → 9
10 < 27 → 10
27 < 82 → 27
38 < 82 → 38
43 < 82 → 43
Remaining → 82
```

---

## ✅ Final Sorted Array

```
[3, 9, 10, 27, 38, 43, 82]
```

---

## 5️ Time & Space Complexity

### Time

* Best / Average / Worst: **O(n log n)**

### Space

* **O(n)** (temporary arrays `L[]` and `R[]`)

---

## 6️ One-line exam explanation

> Merge sort repeatedly divides the array into halves, sorts each half recursively, and merges the sorted halves to produce a fully sorted array.

---
