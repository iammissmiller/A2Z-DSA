## What is Insertion Sort? (Idea + Example)

Insertion sort works the same way you sort **playing cards in your hand**:

* You keep the left part **sorted**
* You take one element from the right
* You **insert it into the correct position** in the sorted part

### Example input

```
n = 5
arr = [5, 3, 4, 1, 2]
```

We assume:

* First element is already sorted

```
Sorted part | Unsorted part
[5]         | [3, 4, 1, 2]
```

---

### Pass 1 (i = 1 → element = 3)

Compare `3` with `5`

```
[5, 3, 4, 1, 2]
 ↑  ↑
```

Since `3 < 5`, swap:

```
[3, 5, 4, 1, 2]
```

Now:

```
[3, 5] | [4, 1, 2]
```

---

### Pass 2 (i = 2 → element = 4)

Compare with `5`, then `3`

```
[3, 5, 4, 1, 2]
```

* `4 < 5` → swap
* `4 > 3` → stop

```
[3, 4, 5, 1, 2]
```

---

### Pass 3 (i = 3 → element = 1)

Move `1` left step-by-step:

```
[3, 4, 5, 1, 2]
↓ ↓ ↓
[1, 3, 4, 5, 2]
```

---

### Pass 4 (i = 4 → element = 2)

Move `2` left:

```
[1, 2, 3, 4, 5]
```

 Fully sorted!

---

## 2️ How **YOUR CODE** Implements Insertion Sort

Here’s your function again:

```cpp
void insertionsort(int arr[], int n)
{
    for(int i = 1; i < n; i++)
    {
        int j = i;

        while(j > 0 && arr[j - 1] > arr[j])
        {
            swap(arr[j], arr[j - 1]);
            j--;
        }
    }
}
```

Let’s explain **each part**.

---

### `for(int i = 1; i < n; i++)`

* Starts from index `1`
* Because a single element (`arr[0]`) is already sorted
* Each iteration inserts `arr[i]` into the sorted left portion

```
Index: 0 | 1 2 3 4
Sorted  | Unsorted
```

---

###  `int j = i;`

* `j` tracks where the current element should move
* Initially, it starts at position `i`

---

### `while(j > 0 && arr[j - 1] > arr[j])`

This loop checks:

1. `j > 0` → don’t go out of bounds
2. `arr[j - 1] > arr[j]` → element is in the wrong position

As long as both are true → **swap backward**

---

### `swap(arr[j], arr[j - 1]);`

* Swaps the current element with the previous one
* This moves the element **left** into its correct position

---

### `j--;`

* Continue checking further left
* Keeps shifting until the element is correctly placed

---

## 3️ What Happens in `main()`

```cpp
int n;
cin >> n;
```

Reads size of array

```cpp
int arr[n];
```

 This works in GCC but **not standard C++**
(usually we use `vector<int>`)

```cpp
insertionsort(arr, n);
```

Calls insertion sort

```cpp
cout << arr[i] << " ";
```

Prints sorted array

---

## 4️ Time & Space Complexity

| Case                   | Time      |
| ---------------------- | --------- |
| Best (already sorted)  | **O(n)**  |
| Average                | **O(n²)** |
| Worst (reverse sorted) | **O(n²)** |

* **Space:** O(1) (in-place)
* **Stable:**  Yes

---

## 5️ Why Your Version Is Good

 Simple
 Correct
 In-place
 Easy to understand

This is a **swap-based insertion sort**, which is perfect for learning.

---
