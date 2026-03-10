# Rearrange Array Elements by Sign

## Problem

Given an array containing **equal number of positive and negative numbers**, rearrange the array so that:

* Positive and negative numbers appear **alternatively**
* First element should be **positive**

### Example

```
Input:
arr = [3,1,-2,-5,2,-4]

Output:
[3,-2,1,-5,2,-4]
```

---

# 1. Brute Force Approach

## Idea

1. Store positives and negatives separately.
2. Place them alternately back into the array.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> rearrangeBrute(vector<int>& arr)
{
    vector<int> pos, neg;

    for(int x : arr)
    {
        if(x > 0)
            pos.push_back(x);
        else
            neg.push_back(x);
    }

    vector<int> result(arr.size());

    for(int i = 0; i < pos.size(); i++)
    {
        result[2*i] = pos[i];
        result[2*i + 1] = neg[i];
    }

    return result;
}

int main()
{
    vector<int> arr = {3,1,-2,-5,2,-4};

    vector<int> ans = rearrangeBrute(arr);

    for(int x : ans)
        cout << x << " ";
}
```

### Complexity

Time → **O(n)**
Space → **O(n)**

---

# 2. Better Approach

## Idea

Use **two pointers** to place positive and negative numbers directly.

Even index → positive
Odd index → negative

---

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> rearrangeBetter(vector<int>& arr)
{
    int n = arr.size();
    vector<int> result(n);

    int posIndex = 0;
    int negIndex = 1;

    for(int x : arr)
    {
        if(x > 0)
        {
            result[posIndex] = x;
            posIndex += 2;
        }
        else
        {
            result[negIndex] = x;
            negIndex += 2;
        }
    }

    return result;
}

int main()
{
    vector<int> arr = {3,1,-2,-5,2,-4};

    vector<int> ans = rearrangeBetter(arr);

    for(int x : ans)
        cout << x << " ";
}
```

---

# Complexity

Time → **O(n)**
Space → **O(n)**

---

# Visualization

Initial:

```
3 1 -2 -5 2 -4
```

Positive numbers:

```
3 1 2
```

Negative numbers:

```
-2 -5 -4
```

Rearranged:

```
3 -2 1 -5 2 -4
```

---

# Interview Notes

Important conditions usually given:

| Condition                     | Solution            |
| ----------------------------- | ------------------- |
| Equal positives and negatives | Alternate placement |
| Start with positive           | Positive at index 0 |
| Start with negative           | Swap positions      |

---
