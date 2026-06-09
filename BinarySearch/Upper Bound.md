# Upper Bound (Binary Search)

## Definition

**Upper Bound** = the **first index** where element is **> X**

---

### Example 1

```id="4f8n4p"
arr = [1,2,4,4,5,6]
X = 4

Output: 4
```

Explanation:

* First element **greater than 4** is **5 at index 4**

---

### Example 2

```id="b0w4sb"
arr = [1,2,4,4,5,6]
X = 3

Output: 2
```

Because:

* First element > 3 is **4 at index 2**

---

### Edge Case

```id="4b7xvx"
arr = [1,2,4,4,5]
X = 10

Output: n (5)
```

---

# 1. Brute Force

## Idea

Traverse and return first element > X

### C++ Code

```cpp id="4r7h0v"
int upperBoundBrute(vector<int>& arr, int x)
{
    for(int i = 0; i < arr.size(); i++)
    {
        if(arr[i] > x)
            return i;
    }
    return arr.size();
}
```

### Complexity

* Time → **O(n)**

---

# 2. Optimal Approach (Binary Search) 

## Idea

We need the **first element strictly greater than X**

---

### C++ Code

```cpp id="kb81yq"
#include <bits/stdc++.h>
using namespace std;

int upperBound(vector<int>& arr, int x)
{
    int low = 0;
    int high = arr.size() - 1;
    int ans = arr.size();

    while(low <= high)
    {
        int mid = low + (high - low) / 2;

        if(arr[mid] > x)
        {
            ans = mid;
            high = mid - 1;  // go left
        }
        else
        {
            low = mid + 1;   // go right
        }
    }

    return ans;
}

int main()
{
    vector<int> arr = {1,2,4,4,5,6};
    int x = 4;

    cout << upperBound(arr, x);
}
```

---

# Complexity

* Time → **O(log n)**
* Space → **O(1)**

---

# Dry Run

```id="yq2z6u"
arr = [1,2,4,4,5,6], x = 4
```

| low | high | mid | arr[mid] | action         |
| --- | ---- | --- | -------- | -------------- |
| 0   | 5    | 2   | 4        | go right       |
| 3   | 5    | 4   | 5        | ans=4, go left |
| 3   | 3    | 3   | 4        | go right       |

Answer = **4**

---

# STL Shortcut

```cpp id="j0jz5k"
auto it = upper_bound(arr.begin(), arr.end(), x);
int index = it - arr.begin();
```

---

# Lower Bound vs Upper Bound

| Function    | Condition |
| ----------- | --------- |
| Lower Bound | ≥ X       |
| Upper Bound | > X       |

---

# Interview Tip

If interviewer says:

```id="4scy9y"
first element > X
```

Think:

```id="ffp5y1"
Upper Bound
```

---

# Very Important Use Cases

* Count occurrences:

```id="s5c6xv"
count = upperBound - lowerBound
```

---
