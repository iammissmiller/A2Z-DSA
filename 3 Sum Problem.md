# 3 Sum Problem

## Problem

Given an array, find all **unique triplets** such that:

```
arr[i] + arr[j] + arr[k] = 0
```

* Indices must be different
* No duplicate triplets allowed

---

### Example

```
Input:
arr = [-1,0,1,2,-1,-4]

Output:
[-1,-1,2]
[-1,0,1]
```

---

# 1. Brute Force Approach

## Idea

Check all possible triplets.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> threeSumBrute(vector<int>& arr)
{
    int n = arr.size();
    set<vector<int>> st;

    for(int i = 0; i < n; i++)
    {
        for(int j = i+1; j < n; j++)
        {
            for(int k = j+1; k < n; k++)
            {
                if(arr[i] + arr[j] + arr[k] == 0)
                {
                    vector<int> temp = {arr[i], arr[j], arr[k]};
                    sort(temp.begin(), temp.end());
                    st.insert(temp);
                }
            }
        }
    }

    return vector<vector<int>>(st.begin(), st.end());
}

int main()
{
    vector<int> arr = {-1,0,1,2,-1,-4};

    vector<vector<int>> ans = threeSumBrute(arr);

    for(auto v : ans)
    {
        for(int x : v) cout << x << " ";
        cout << endl;
    }
}
```

### Complexity

Time → **O(n³)**
Space → **O(no. of triplets)**

---

# 2. Better Approach (Hashing)

## Idea

Fix one element and use a set for remaining two.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> threeSumBetter(vector<int>& arr)
{
    int n = arr.size();
    set<vector<int>> st;

    for(int i = 0; i < n; i++)
    {
        unordered_set<int> s;

        for(int j = i+1; j < n; j++)
        {
            int third = -(arr[i] + arr[j]);

            if(s.find(third) != s.end())
            {
                vector<int> temp = {arr[i], arr[j], third};
                sort(temp.begin(), temp.end());
                st.insert(temp);
            }

            s.insert(arr[j]);
        }
    }

    return vector<vector<int>>(st.begin(), st.end());
}
```

### Complexity

Time → **O(n²)**
Space → **O(n)**

---

# 3. Optimal Approach (Sorting + Two Pointers) ⭐

## Idea

1. Sort the array
2. Fix one element
3. Use two pointers to find remaining two

---

### Steps

* Fix `i`
* left = i+1
* right = n-1
* Move pointers based on sum

---

# Optimal C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> threeSum(vector<int>& arr)
{
    int n = arr.size();
    vector<vector<int>> ans;

    sort(arr.begin(), arr.end());

    for(int i = 0; i < n; i++)
    {
        if(i > 0 && arr[i] == arr[i-1])
            continue;

        int left = i+1;
        int right = n-1;

        while(left < right)
        {
            int sum = arr[i] + arr[left] + arr[right];

            if(sum == 0)
            {
                ans.push_back({arr[i], arr[left], arr[right]});

                left++;
                right--;

                while(left < right && arr[left] == arr[left-1]) left++;
                while(left < right && arr[right] == arr[right+1]) right--;
            }
            else if(sum < 0)
                left++;
            else
                right--;
        }
    }

    return ans;
}

int main()
{
    vector<int> arr = {-1,0,1,2,-1,-4};

    vector<vector<int>> ans = threeSum(arr);

    for(auto v : ans)
    {
        for(int x : v) cout << x << " ";
        cout << endl;
    }
}
```

---

# Complexity (Optimal)

Time → **O(n²)**
Space → **O(1)** (excluding output)

---

# Dry Run

Sorted:

```
[-4,-1,-1,0,1,2]
```

Triplets:

```
[-1,-1,2]
[-1,0,1]
```

---

# Interview Pattern

If question says:

```
Find triplets / 3 numbers / sum = target
```

Think:

```
Sorting + Two Pointers
```

---
