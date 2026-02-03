# **Quick Sort**

### **1. What is Quick Sort?**

* **Quick Sort** is a **sorting algorithm** used to arrange elements (like numbers) in a list in ascending or descending order. It works using the **Divide and Conquer** strategy. 

---

## **2. Core Idea (Divide and Conquer)**

Quick Sort breaks a big problem into smaller sub-problems and solves them recursively:

1. **Divide:** Pick a *pivot* element from the list.
2. **Partition:** Rearrange the list so:

   * Elements **less than pivot** go to the left.
   * Elements **greater than pivot** go to the right.
     After this, pivot is in **correct final position**.
3. **Conquer:** Recursively apply the same process to left and right parts.
4. **Base Case:** Stop recursion when a sublist has **0 or 1** element. ([takeuforward][3])

---

## **3. How Quick Sort Works (Step-by-Step)**

### **Step 1: Choose a Pivot**

A pivot can be:

* first element
* last element
* random element
* median (or median-of-three)
  Good pivot choice improves performance. ([GeeksforGeeks][4])

### **Step 2: Partition the Array**

Partitioning rearranges elements so that the pivot ends up in its correct sorted position:

* All items ≤ pivot go to left.
* All items > pivot go to right.
  Then return pivot’s index. ([GeeksforGeeks][4])

### **Step 3: Recursively Sort Subarrays**

Call Quick Sort on:

* left part (before pivot)
* right part (after pivot)
  Repeat until subarrays are very small (≤ 1 element). ([GeeksforGeeks][4])

---

## **4. Recursion Visualization**

If the array looks like this:

```
[34, 7, 23, 32, 5, 62]
```

Pick pivot → partition → recursively sort left and right parts.

---

## **5. Time Complexity**

Quick Sort’s performance depends on how balanced the partitions are:

| Case             | Time Complexity                                  |                  |
| ---------------- | ------------------------------------------------ | ---------------- |
| **Best Case**    | O(n log n)                                       |                  |
| **Average Case** | O(n log n)                                       |                  |
| **Worst Case**   | O(n²) *bad pivot selection (e.g., sorted array)* | ([Wikipedia][2]) |

---

## **6. Space Complexity**

* Quick Sort performs sorting **in place**, so it doesn’t use extra arrays.
* But recursion uses stack space → **O(log n)** on average (worst-case O(n)). ([Wikipedia][2])

---

## **7. Characteristics**

* **In-Place Sort:** Yes (uses few extra space). ([W3Schools][5])
* **Stable Sort:** No (equal elements might change order). ([Wikipedia][2])
* **Divides array** into smaller partitions. ([takeuforward][3])

---

## **8. Pivot Selection Strategies**

Choosing a good pivot reduces chances of worst case:

* Random element
* Median of first, middle, last
* Middle element
  Poor pivot (like always first / last) can lead to unbalanced splits. ([GeeksforGeeks][4])

---

## **9. Example Pseudocode (Logical)**

```
quickSort(arr, low, high):
    if low < high:
        pivotIndex = partition(arr, low, high)
        quickSort(arr, low, pivotIndex - 1)
        quickSort(arr, pivotIndex + 1, high)

partition(arr, low, high):
    pivot = arr[high]
    i = low - 1
    for j from low to high - 1:
        if arr[j] <= pivot:
            i = i + 1
            swap(arr[i], arr[j])
    swap(arr[i + 1], arr[high])
    return i + 1
```

*(This is the standard “Lomuto partition”… other schemes exist too.)* ([GeeksforGeeks][4])

---

## **10. Practical Notes**

* Quick Sort is widely used in libraries (often with improvements like **Dual Pivot** or **IntroSort**). ([Wikipedia][2])
* On average it’s **very fast** and works well for large arrays. ([khanacademy.org][6])
