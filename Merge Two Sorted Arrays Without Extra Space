# Merge Two Sorted Arrays Without Extra Space

## Problem

Given two **sorted arrays**, merge them such that:

* Final result is **sorted**
* Do it **in-place** (no extra space)

---

### Example

```text
Input:
arr1 = [1,3,5,7]
arr2 = [0,2,6,8,9]

Output:
arr1 = [0,1,2,3]
arr2 = [5,6,7,8,9]
```

---

# 1. Brute Force Approach

## Idea

* Copy both arrays into one
* Sort
* Put back

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

void mergeBrute(vector<int>& a, vector<int>& b)
{
    vector<int> temp;

    for(int x : a) temp.push_back(x);
    for(int x : b) temp.push_back(x);

    sort(temp.begin(), temp.end());

    int n = a.size();

    for(int i = 0; i < n; i++)
        a[i] = temp[i];

    for(int i = 0; i < b.size(); i++)
        b[i] = temp[n + i];
}
```

### Complexity

* Time → **O((n+m) log(n+m))**
* Space → **O(n+m)** 

---

# 2. Better Approach (Two Pointer + Swap)

## Idea

* Compare last of `a` with first of `b`
* Swap if needed
* Sort both arrays again

---

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

void mergeBetter(vector<int>& a, vector<int>& b)
{
    int n = a.size();
    int m = b.size();

    int left = n - 1;
    int right = 0;

    while(left >= 0 && right < m)
    {
        if(a[left] > b[right])
        {
            swap(a[left], b[right]);
            left--;
            right++;
        }
        else
        {
            break;
        }
    }

    sort(a.begin(), a.end());
    sort(b.begin(), b.end());
}
```

### Complexity

* Time → **O(n log n + m log m)**
* Space → **O(1)**

---

# 3. Optimal Approach (Gap Method / Shell Sort Idea) 

## Idea

Use a **gap**:

```text
gap = ceil((n+m)/2)
```

Compare elements `gap` apart and reduce gap.

---

# C++ Code (Most Important)

```cpp
#include <bits/stdc++.h>
using namespace std;

void mergeOptimal(vector<int>& a, vector<int>& b)
{
    int n = a.size();
    int m = b.size();

    int len = n + m;
    int gap = (len / 2) + (len % 2); // ceil

    while(gap > 0)
    {
        int left = 0;
        int right = left + gap;

        while(right < len)
        {
            // case 1: both in a
            if(left < n && right < n)
            {
                if(a[left] > a[right])
                    swap(a[left], a[right]);
            }
            // case 2: left in a, right in b
            else if(left < n && right >= n)
            {
                if(a[left] > b[right - n])
                    swap(a[left], b[right - n]);
            }
            // case 3: both in b
            else
            {
                if(b[left - n] > b[right - n])
                    swap(b[left - n], b[right - n]);
            }

            left++;
            right++;
        }

        if(gap == 1) break;

        gap = (gap / 2) + (gap % 2);
    }
}
```

---

# Complexity (Optimal)

* Time → **O((n+m) log(n+m))**
* Space → **O(1)** 

---

# Dry Run (Concept)

```
a = [1,3,5,7]
b = [0,2,6,8,9]

Combined: [1,3,5,7 | 0,2,6,8,9]

Gap = 5 → compare distant elements
Gap = 3 → refine
Gap = 2 → refine
Gap = 1 → final pass
```

---

# Interview Tip 

If interviewer says:

```text
merge without extra space
```

Think:

```text
Gap Method (Shell Sort idea)
```

---

# Key Differences

| Approach | Space    | Time       |
| -------- | -------- | ---------- |
| Brute    | O(n+m)  | O(n log n) |
| Better   | O(1)     | O(n log n) |
| Optimal  | O(1)    | O(n log n) |

---
