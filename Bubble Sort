## 1. What is Bubble Sort?

**Bubble Sort** is a simple comparison-based sorting algorithm.

### Core idea

*Repeatedly compare adjacent elements and swap them if they are in the wrong order.*

* In each pass, the **largest element “bubbles up” to the end**.
* After every pass, **one element is placed in its correct position at the end**.

---

## 2. Your Function: `bubblesort()`

```cpp
void bubblesort(int arr[], int n)
{
    for(int i = 0; i < n - 1; i++)          // passes
    {
        for(int j = 0; j < n - i - 1; j++)  // adjacent comparisons
        {
            if(arr[j] > arr[j + 1])
            {
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}
```

Let’s break this **line by line**.

---

### Outer loop (`i` loop) — Passes

```cpp
for(int i = 0; i < n - 1; i++)
```

* Controls the **number of passes**.
* After each pass, the **largest element moves to the end**.
* We need only `n - 1` passes because:

  * After `n - 1` elements are sorted, the last one is automatically sorted.

---

### Inner loop (`j` loop) — Comparisons

```cpp
for(int j = 0; j < n - i - 1; j++)
```

* Compares **adjacent elements**:

  * `arr[j]` and `arr[j + 1]`
* `n - i - 1` because:

  * The last `i` elements are already sorted
  * No need to compare them again

---

### Swapping condition

```cpp
if(arr[j] > arr[j + 1])
```

* If the left element is **greater**, they are in the wrong order.

---

### Swap logic

```cpp
int temp = arr[j];
arr[j] = arr[j + 1];
arr[j + 1] = temp;
```

* Swaps adjacent elements
* Larger element moves one step to the right

---

## 3. Dry Run Example (Very Important)

### Input

```
n = 5
arr = [64, 25, 12, 22, 11]
```

---

### Pass 1 (`i = 0`)

Compare adjacent elements:

* 64 > 25 → swap → `[25, 64, 12, 22, 11]`
* 64 > 12 → swap → `[25, 12, 64, 22, 11]`
* 64 > 22 → swap → `[25, 12, 22, 64, 11]`
* 64 > 11 → swap → `[25, 12, 22, 11, 64]`

Largest element **64** reaches the end.

---

### Pass 2 (`i = 1`)

Unsorted part: `[25, 12, 22, 11]`

* 25 > 12 → swap → `[12, 25, 22, 11, 64]`
* 25 > 22 → swap → `[12, 22, 25, 11, 64]`
* 25 > 11 → swap → `[12, 22, 11, 25, 64]`

Largest of this pass **25** fixed at index 3.

---

### Pass 3 (`i = 2`)

Unsorted part: `[12, 22, 11]`

* 12 > 22 → no swap
* 22 > 11 → swap → `[12, 11, 22, 25, 64]`

---

### Pass 4 (`i = 3`)

Unsorted part: `[12, 11]`

* 12 > 11 → swap → `[11, 12, 22, 25, 64]`

Array is now **fully sorted**.

---

## 4. `main()` Function Explanation

```cpp
int n;
cin >> n;
```

* Reads number of elements.

```cpp
int arr[n];
```

* Declares array.

```cpp
for(int i = 0; i < n; i++)
{
    cin >> arr[i];
}
```

* Takes input.

```cpp
bubblesort(arr, n);
```

* Calls bubble sort function.

```cpp
for(int i = 0; i < n; i++)
{
    cout << arr[i] << " ";
}
```

* Prints sorted array.

---

## 5. Time & Space Complexity

* **Best Case:** `O(n²)` *(in this version, no early stopping)*
* **Average Case:** `O(n²)`
* **Worst Case:** `O(n²)`
* **Space Complexity:** `O(1)` (in-place)

---

## 6. Key Points to Remember (Exam-ready)

* Bubble sort works by **repeated swapping of adjacent elements**.
* Largest element moves to the end in each pass.
* Very **easy to understand**, but **inefficient** for large arrays.
* Performs **more swaps** compared to Selection Sort.

---

## 7. Bubble Sort vs Selection Sort (Quick)

| Feature    | Bubble Sort    | Selection Sort |
| ---------- | -------------- | -------------- |
| Strategy   | Adjacent swaps | Select minimum |
| Swaps      | Many           | Very few       |
| Complexity | O(n²)          | O(n²)          |
| Simplicity | Very easy      | Easy           |

---
