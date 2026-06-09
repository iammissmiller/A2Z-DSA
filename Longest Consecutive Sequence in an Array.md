# Longest Consecutive Sequence in an Array

## Problem

Given an **unsorted array**, find the **length of the longest sequence of consecutive integers**.

The elements do **not need to be adjacent in the array**, only consecutive in value.

---

### Example

```
Input:
arr = [100, 4, 200, 1, 3, 2]

Output:
4
```

Explanation:

```
Sequence = 1,2,3,4
Length = 4
```

---

# 1. Brute Force Approach

## Idea

For every element:

* Check if `x+1` exists
* Keep counting until sequence breaks

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

bool linearSearch(vector<int>& arr, int num)
{
    for(int x : arr)
        if(x == num)
            return true;

    return false;
}

int longestConsecutiveBrute(vector<int>& arr)
{
    int n = arr.size();
    int longest = 1;

    for(int i = 0; i < n; i++)
    {
        int x = arr[i];
        int count = 1;

        while(linearSearch(arr, x + 1))
        {
            x = x + 1;
            count++;
        }

        longest = max(longest, count);
    }

    return longest;
}

int main()
{
    vector<int> arr = {100,4,200,1,3,2};

    cout << longestConsecutiveBrute(arr);
}
```

### Complexity

Time → **O(n²)**
Space → **O(1)**

---

# 2. Better Approach (Sorting)

## Idea

1. Sort the array
2. Count consecutive elements

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int longestConsecutiveBetter(vector<int>& arr)
{
    sort(arr.begin(), arr.end());

    int longest = 1;
    int count = 1;

    for(int i = 1; i < arr.size(); i++)
    {
        if(arr[i] == arr[i-1] + 1)
        {
            count++;
        }
        else if(arr[i] != arr[i-1])
        {
            count = 1;
        }

        longest = max(longest, count);
    }

    return longest;
}

int main()
{
    vector<int> arr = {100,4,200,1,3,2};

    cout << longestConsecutiveBetter(arr);
}
```

### Complexity

Time → **O(n log n)**
Space → **O(1)**

---

# 3. Optimal Approach (HashSet) ⭐

This is the **most important interview solution**.

## Idea

Use a **set** to store elements.

Start sequence **only when the element is the start of a sequence**:

```
if (num - 1 not present)
```

Then count:

```
num, num+1, num+2 ...
```

---

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int longestConsecutive(vector<int>& arr)
{
    unordered_set<int> st(arr.begin(), arr.end());

    int longest = 0;

    for(int num : st)
    {
        if(st.find(num - 1) == st.end())
        {
            int current = num;
            int count = 1;

            while(st.find(current + 1) != st.end())
            {
                current++;
                count++;
            }

            longest = max(longest, count);
        }
    }

    return longest;
}

int main()
{
    vector<int> arr = {100,4,200,1,3,2};

    cout << longestConsecutive(arr);
}
```

---

# Complexity

Time → **O(n)**
Space → **O(n)**

---

# Visualization

Array:

```
100 4 200 1 3 2
```

Set becomes:

```
{100,4,200,1,3,2}
```

Start sequences only when **num-1 not present**.

```
1 → start sequence
1 → 2 → 3 → 4
length = 4
```

---

# Interview Pattern Recognition

If question says:

```
Longest consecutive numbers
```

Think immediately:

```
HashSet
```

Key condition:

```
start only when (num - 1 not present)
```

---
