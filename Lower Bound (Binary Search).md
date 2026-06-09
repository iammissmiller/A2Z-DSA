# Lower Bound (Binary Search)

## Definition

**Lower Bound** = the **first index** where element is **≥ X**

---

### Example

```id="0cxtt9"
arr = [1,2,4,4,5,6]
X = 4

Output: 2
```

Explanation:

* First position where value ≥ 4 is index **2**

---

### Another Example

```id="8y37zs"
arr = [1,2,4,4,5,6]
X = 3

Output: 2
```

Because:

* First element ≥ 3 is **4 at index 2**

---

### Edge Case

```id="mn3s3x"
arr = [1,2,4,4,5]
X = 7

Output: n (5)
```

---

# 1. Brute Force

## Idea

Traverse and return first element ≥ X

### Code

```cpp id="iq4uh3"
int lowerBoundBrute(vector<int>& arr, int x)
{
    for(int i = 0; i < arr.size(); i++)
    {
        if(arr[i] >= x)
            return i;
    }
    return arr.size();
}
```

### Complexity

* Time → **O(n)**

---

# 2. Optimal Approach (Binary Search) ⭐

## Idea

We want the **first occurrence** where:

```id="qj2bzb"
arr[mid] >= X
```

---

## C++ Code

```cpp id="z8w7yo"
#include <bits/stdc++.h>
using namespace std;

int lowerBound(vector<int>& arr, int x)
{
    int low = 0;
    int high = arr.size() - 1;
    int ans = arr.size();

    while(low <= high)
    {
        int mid = low + (high - low) / 2;

        if(arr[mid] >= x)
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

    cout << lowerBound(arr, x);
}
```

---

# Complexity

* Time → **O(log n)**
* Space → **O(1)**

---

# Dry Run

```id="3zbh8o"
arr = [1,2,4,4,5,6], x = 4
```

| low | high | mid | arr[mid] | action         |
| --- | ---- | --- | -------- | -------------- |
| 0   | 5    | 2   | 4        | ans=2, go left |
| 0   | 1    | 0   | 1        | go right       |
| 1   | 1    | 1   | 2        | go right       |

Answer = **2**

---

# STL Shortcut

C++ already provides this:

```cpp id="dmdrsm"
auto it = lower_bound(arr.begin(), arr.end(), x);
int index = it - arr.begin();
```

---

# Difference from Upper Bound

| Function    | Meaning   |
| ----------- | --------- |
| Lower Bound | First ≥ X |
| Upper Bound | First > X |

---

# Interview Tip ⭐

If interviewer says:

```id="hdfd2g"
first element >= X
```

Think:

```id="2sxsc2"
Lower Bound
```

---
