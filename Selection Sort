# Selection Sort

## 1. What is Selection Sort?

**Selection Sort** is a simple sorting algorithm where:

* We divide the array into **sorted** and **unsorted** parts.
* Repeatedly **select the smallest element** from the unsorted part. ------- main logic
* Swap it with the **first element of the unsorted part**.
* Move the boundary of the sorted part one step to the right.

After every pass, **one element is placed in its correct position**.

---

## 2. Your Function: `selectionsort()`

```cpp
void selectionsort(int arr[] , int n )
{
    for(int i = 0 ; i<= n-2 ; i++)
    {
        int minimum = i;
        for(int j = i ; j <= n-1 ; j++)
        {
            if (arr[minimum] > arr[j])
            {
                minimum = j;
            }
        }

        int temp = arr[minimum];
        arr[minimum] = arr[i];
        arr[i] = temp;
    }
}
```

Let’s break this **line by line**.

---

### Outer loop (`i` loop)

```cpp
for(int i = 0 ; i<= n-2 ; i++)
```

* Controls **which position** we are filling.
* `i` represents the **current position** where the smallest element should go.
* We go only till `n-2` because the last element will already be sorted.

At start of each iteration:

* Index `0` to `i-1` → sorted
* Index `i` to `n-1` → unsorted

---

### Minimum index initialization

```cpp
int minimum = i;
```

* Assume the **first element of the unsorted part** is the smallest.
* `minimum` stores the index of the smallest element found so far.

---

### Inner loop (`j` loop)

```cpp
for(int j = i ; j <= n-1 ; j++)
```

* Scans the **unsorted part** of the array.
* Compares each element with the current minimum.

---

### Finding the smallest element

```cpp
if (arr[minimum] > arr[j])
{
    minimum = j;
}
```

* If a smaller element is found:

  * Update `minimum` to that index.

By the end of this loop:

* `minimum` holds the **index of the smallest element** in the unsorted part.

---

### Swapping

```cpp
int temp = arr[minimum];
arr[minimum] = arr[i];
arr[i] = temp;
```

* Swap the smallest element with the element at position `i`.
* This places the correct element at its sorted position.

---

## 3. Dry Run Example (Very Important)

### Input

```
n = 5
arr = [64, 25, 12, 22, 11]
```

---

### Pass 1 (`i = 0`)

Unsorted: `[64, 25, 12, 22, 11]`
Smallest element = `11` (index 4)

Swap `arr[0]` and `arr[4]`

```
[11, 25, 12, 22, 64]
```

Sorted part: `[11]`

---

### Pass 2 (`i = 1`)

Unsorted: `[25, 12, 22, 64]`
Smallest element = `12` (index 2)

Swap `arr[1]` and `arr[2]`

```
[11, 12, 25, 22, 64]
```

Sorted part: `[11, 12]`

---

### Pass 3 (`i = 2`)

Unsorted: `[25, 22, 64]`
Smallest element = `22` (index 3)

Swap `arr[2]` and `arr[3]`

```
[11, 12, 22, 25, 64]
```

Sorted part: `[11, 12, 22]`

---

### Pass 4 (`i = 3`)

Unsorted: `[25, 64]`
Smallest element = `25` (already at correct place)

```
[11, 12, 22, 25, 64]
```

Array is now **fully sorted**.

---

## 4. `main()` Function Explanation

```cpp
int n;
cin >> n;
```

* Takes number of elements.

```cpp
int arr[n];
```

* Declares array of size `n`.

```cpp
for(int i = 0 ; i <n ; i++)
{
    cin >> arr[i];
}
```

* Takes array input.

```cpp
selectionsort(arr,n);
```

* Calls selection sort function.

```cpp
for(int i = 0 ; i <n ; i++)
{
    cout << arr[i] << " ";
}
```

* Prints sorted array.

---

## 5. Time & Space Complexity

* **Time Complexity:**

  * Best, Average, Worst → **O(n²)**

* **Space Complexity:**

  * **O(1)** (in-place sorting)

---

## 6. Key Points to Remember (Exam-friendly)

* Selection sort repeatedly finds the **minimum element**.
* Swaps it with the first unsorted position.
* Number of swaps is **minimum** compared to bubble sort.
* Not suitable for large datasets.
