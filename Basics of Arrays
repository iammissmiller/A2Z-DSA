# Arrays – Basic DSA Notes

## 1. Basics of Array

### Definition

An **array** is a linear data structure that stores elements of the **same data type** in **contiguous memory locations**.

Example:

```
int arr[5] = {1, 2, 3, 4, 5};
```

### Basic Terminologies

| Term    | Meaning                                      |
| ------- | -------------------------------------------- |
| Index   | Position of element in array (starts from 0) |
| Element | Value stored at an index                     |
| Size    | Number of elements in the array              |
| Length  | Same as size (commonly used term)            |

Example:

```
arr = [10, 20, 30, 40]
Index: 0   1   2   3
```

### Maximum Size of an Array

* Depends on:

  * Programming language
  * System memory
* In C++:

  * Static array size depends on stack memory.
  * Dynamic arrays (`vector`) depend on heap memory.

---

## 2. Largest Element in an Array

### Brute Force Solution

**Steps:**

1. Sort the array.
2. Print the last element.

**Time Complexity:**
O(n log n)

---

### Optimal Solution

**Idea:** Traverse once and track the maximum.

**Steps:**

1. Assume `a[0]` as largest.
2. Traverse from index `1` to `n-1`.
3. Update largest if a bigger element is found.

**Time Complexity:**
O(n)

**Code:**

```cpp
#include <bits/stdc++.h>
using namespace std;

int largestElement(vector<int> a, int n)
{
    int largest = a[0];

    for(int i = 1; i < n; i++)
    {
        if(a[i] > largest)
        {
            largest = a[i];
        }
    }
    return largest;
}

int main()
{
    int n;
    cin >> n;

    vector<int> a(n);
    for(int i = 0; i < n; i++)
    {
        cin >> a[i];
    }

    cout << largestElement(a, n);
    return 0;
}
```

---

## 3. Second Largest Element in an Array

### Brute Force

**Steps:**

1. Sort the array.
2. Traverse from `n-2` to `0`.
3. Find first element not equal to largest.

**Time Complexity:**
O(n log n)

---

### Better Solution (Two Pass)

**Steps:**

1. Find largest in first pass.
2. In second pass, find the largest element not equal to largest.

**Time Complexity:**
O(2n) ≈ O(n)

---

### Optimal Solution (Single Pass)

**Idea:**
Track both largest and second largest simultaneously.

**Steps:**

1. Initialize:

   * `largest = a[0]`
   * `secondLargest = -1`
2. Traverse from index `1`.
3. Update both values accordingly.

**Time Complexity:**
O(n)

**Code:**

```cpp
#include <bits/stdc++.h>
using namespace std;

int secondLargestElement(vector<int> a, int n)
{
    int largest = a[0];
    int secondLargest = -1;

    for(int i = 1; i < n; i++)
    {
        if(a[i] > largest)
        {
            secondLargest = largest;
            largest = a[i];
        }
        else if(a[i] < largest && a[i] > secondLargest)
        {
            secondLargest = a[i];
        }
    }
    return secondLargest;
}

int main()
{
    int n;
    cin >> n;

    vector<int> a(n);
    for(int i = 0; i < n; i++)
    {
        cin >> a[i];
    }

    cout << secondLargestElement(a, n);
    return 0;
}
```

---

## 4. Check if Array is Sorted

### Idea

Check if every element is **less than or equal to the next element**.

**Time Complexity:**
O(n)

**Correct Logic:**

* Compare `a[i]` with `a[i+1]`.
* If any `a[i] > a[i+1]`, array is not sorted.

**Code:**

```cpp
#include <bits/stdc++.h>
using namespace std;

bool isSorted(vector<int> a, int n)
{
    for(int i = 0; i < n - 1; i++)
    {
        if(a[i] > a[i+1])
        {
            return false;
        }
    }
    return true;
}

int main()
{
    int n;
    cin >> n;

    vector<int> a(n);
    for(int i = 0; i < n; i++)
    {
        cin >> a[i];
    }

    cout << isSorted(a, n);
    return 0;
}
```

---

## 5. Remove Duplicates from an Array

### Brute Force (Using Set)

**Idea:**
Use a `set` to store unique elements.

**Time Complexity:**
O(n log n)

**Code:**

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> removeDuplicate(vector<int> a, int n)
{
    set<int> st;

    for(int i = 0; i < n; i++)
    {
        st.insert(a[i]);
    }

    int index = 0;
    for(auto it : st)
    {
        a[index] = it;
        index++;
    }

    a.resize(index);
    return a;
}

int main()
{
    int n;
    cin >> n;

    vector<int> a(n);
    for(int i = 0; i < n; i++)
    {
        cin >> a[i];
    }

    vector<int> result = removeDuplicate(a, n);

    for(int x : result)
    {
        cout << x << " ";
    }

    return 0;
}
```

---

### Better Solution (For Sorted Array)

**Idea:**
Use an extra array to store unique elements.

**Time Complexity:**
O(n)
**Space Complexity:** O(n)

---

### Optimal Solution (For Sorted Array)

**Idea:**
Use two-pointer technique.

**Steps:**

1. Let `i = 0`.
2. Traverse with `j` from `1` to `n-1`.
3. If `a[j] != a[i]`, move `i` forward and copy.

**Time Complexity:**
O(n)
**Space Complexity:** O(1)

**Code:**

```cpp
int removeDuplicates(vector<int>& a)
{
    int n = a.size();
    int i = 0;

    for(int j = 1; j < n; j++)
    {
        if(a[j] != a[i])
        {
            i++;
            a[i] = a[j];
        }
    }
    return i + 1; // new size
}
```

