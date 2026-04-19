# 4 Sum Problem

## Problem

Given an array and a target **K**, find all **unique quadruplets**:

```
arr[i] + arr[j] + arr[k] + arr[l] = K
```

* All indices must be different
* No duplicate quadruplets

---

### Example

```
Input:
arr = [1,0,-1,0,-2,2]
target = 0

Output:
[-2,-1,1,2]
[-2,0,0,2]
[-1,0,0,1]
```

---

# 1. Brute Force Approach

## Idea

Try all 4 combinations.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> fourSumBrute(vector<int>& arr, int target)
{
    int n = arr.size();
    set<vector<int>> st;

    for(int i = 0; i < n; i++)
    {
        for(int j = i+1; j < n; j++)
        {
            for(int k = j+1; k < n; k++)
            {
                for(int l = k+1; l < n; l++)
                {
                    if(arr[i] + arr[j] + arr[k] + arr[l] == target)
                    {
                        vector<int> temp = {arr[i], arr[j], arr[k], arr[l]};
                        sort(temp.begin(), temp.end());
                        st.insert(temp);
                    }
                }
            }
        }
    }

    return vector<vector<int>>(st.begin(), st.end());
}
```

### Complexity

Time → **O(n⁴)**
Space → **O(no. of quadruplets)**

---

# 2. Better Approach (Hashing)

## Idea

Fix 2 elements and use a set for remaining two.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> fourSumBetter(vector<int>& arr, int target)
{
    int n = arr.size();
    set<vector<int>> st;

    for(int i = 0; i < n; i++)
    {
        for(int j = i+1; j < n; j++)
        {
            unordered_set<int> s;

            for(int k = j+1; k < n; k++)
            {
                int fourth = target - (arr[i] + arr[j] + arr[k]);

                if(s.find(fourth) != s.end())
                {
                    vector<int> temp = {arr[i], arr[j], arr[k], fourth};
                    sort(temp.begin(), temp.end());
                    st.insert(temp);
                }

                s.insert(arr[k]);
            }
        }
    }

    return vector<vector<int>>(st.begin(), st.end());
}
```

### Complexity

Time → **O(n³)**
Space → **O(n)**

---

# 3. Optimal Approach (Sorting + Two Pointers) ⭐

## Idea

1. Sort the array
2. Fix first two elements (`i`, `j`)
3. Use two pointers for remaining two

---

# Optimal C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> fourSum(vector<int>& arr, int target)
{
    int n = arr.size();
    vector<vector<int>> ans;

    sort(arr.begin(), arr.end());

    for(int i = 0; i < n; i++)
    {
        if(i > 0 && arr[i] == arr[i-1]) continue;

        for(int j = i+1; j < n; j++)
        {
            if(j > i+1 && arr[j] == arr[j-1]) continue;

            int left = j+1;
            int right = n-1;

            while(left < right)
            {
                long long sum = (long long)arr[i] + arr[j] + arr[left] + arr[right];

                if(sum == target)
                {
                    ans.push_back({arr[i], arr[j], arr[left], arr[right]});

                    left++;
                    right--;

                    while(left < right && arr[left] == arr[left-1]) left++;
                    while(left < right && arr[right] == arr[right+1]) right--;
                }
                else if(sum < target)
                    left++;
                else
                    right--;
            }
        }
    }

    return ans;
}

int main()
{
    vector<int> arr = {1,0,-1,0,-2,2};
    int target = 0;

    vector<vector<int>> ans = fourSum(arr, target);

    for(auto v : ans)
    {
        for(int x : v)
            cout << x << " ";
        cout << endl;
    }
}
```

---

# Complexity (Optimal)

Time → **O(n³)**
Space → **O(1)** (excluding output)

---

# Key Interview Points ⭐

### 3 Sum vs 4 Sum

| Problem | Approach             |
| ------- | -------------------- |
| 3 Sum   | Fix 1 + Two pointers |
| 4 Sum   | Fix 2 + Two pointers |

---

# Important Tricks

### 1. Avoid duplicates

```cpp
if(i > 0 && arr[i] == arr[i-1]) continue;
```

### 2. Use long long

```cpp
long long sum = ...
```

Prevents overflow.

---

# Pattern Recognition

If interviewer says:

```
Find k numbers whose sum = target
```

Think:

```
Sort + Fix (k-2) + Two pointers
```

---
