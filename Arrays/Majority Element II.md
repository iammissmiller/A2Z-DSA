 # Majority Element II 
## Problem

Find all elements that appear **more than ⌊ n/3 ⌋ times**.

* Array size = n
* Answer can contain **at most 2 elements**

---

# Approach 1 — Brute Force (Check Each Element)

## Idea

For each element:

* Count frequency
* If > n/3 → add to answer
* Avoid duplicates

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> majorityElementBrute(vector<int>& arr)
{
    int n = arr.size();
    vector<int> ans;

    for(int i = 0; i < n; i++)
    {
        int count = 0;

        // avoid duplicates
        bool already = false;
        for(int x : ans)
        {
            if(x == arr[i])
            {
                already = true;
                break;
            }
        }

        if(already) continue;

        for(int j = 0; j < n; j++)
        {
            if(arr[j] == arr[i])
                count++;
        }

        if(count > n/3)
            ans.push_back(arr[i]);
    }

    return ans;
}

int main()
{
    vector<int> arr = {1,1,1,3,3,2,2,2};

    vector<int> ans = majorityElementBrute(arr);

    for(int x : ans)
        cout << x << " ";
}
```

### Complexity

Time → **O(n²)**
Space → **O(1)**

---

# Approach 2 — Better (HashMap)

## Idea

Count frequency using map.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> majorityElementBetter(vector<int>& arr)
{
    int n = arr.size();
    unordered_map<int,int> mp;

    for(int x : arr)
    {
        mp[x]++;
    }

    vector<int> ans;

    for(auto it : mp)
    {
        if(it.second > n/3)
            ans.push_back(it.first);
    }

    return ans;
}

int main()
{
    vector<int> arr = {1,1,1,3,3,2,2,2};

    vector<int> ans = majorityElementBetter(arr);

    for(int x : ans)
        cout << x << " ";
}
```

### Complexity

Time → **O(n)**
Space → **O(n)**

---

# Approach 3 — Optimal (Boyer Moore Voting Algorithm) ⭐

## Key Observation

For **n/3**, at most **2 elements** can exist.

So we track:

```
candidate1
candidate2
count1
count2
```

---

## Step 1 — Find Candidates

Rules:

* if equal → increase count
* if count 0 → replace candidate
* else → decrease both

---

## Step 2 — Verify Candidates

Because voting only gives **possible candidates**.

---

# Optimal Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> majorityElementOptimal(vector<int>& arr)
{
    int count1 = 0, count2 = 0;
    int candidate1 = 0, candidate2 = 0;

    // Step 1: find candidates
    for(int x : arr)
    {
        if(x == candidate1)
            count1++;

        else if(x == candidate2)
            count2++;

        else if(count1 == 0)
        {
            candidate1 = x;
            count1 = 1;
        }

        else if(count2 == 0)
        {
            candidate2 = x;
            count2 = 1;
        }

        else
        {
            count1--;
            count2--;
        }
    }

    // Step 2: verify
    count1 = 0;
    count2 = 0;

    for(int x : arr)
    {
        if(x == candidate1) count1++;
        else if(x == candidate2) count2++;
    }

    vector<int> ans;
    int n = arr.size();

    if(count1 > n/3) ans.push_back(candidate1);
    if(count2 > n/3) ans.push_back(candidate2);

    return ans;
}

int main()
{
    vector<int> arr = {1,1,1,3,3,2,2,2};

    vector<int> ans = majorityElementOptimal(arr);

    for(int x : ans)
        cout << x << " ";
}
```

---

# Complexity

Time → **O(n)**
Space → **O(1)**

---

# Dry Run

```
arr = [1,1,1,3,3,2,2,2]
n = 8
n/3 = 2
```

Voting phase:

| element | c1 | cnt1 | c2 | cnt2 |
| ------- | -- | ---- | -- | ---- |
| 1       | 1  | 1    |    |      |
| 1       | 1  | 2    |    |      |
| 1       | 1  | 3    |    |      |
| 3       | 1  | 3    | 3  | 1    |
| 3       | 1  | 3    | 3  | 2    |
| 2       | 1  | 2    | 3  | 1    |
| 2       | 1  | 1    | 3  | 0    |
| 2       | 1  | 1    | 2  | 1    |

Candidates:

```
1 and 2
```

Verify:

```
1 → 3 times
2 → 3 times
```

Answer:

```
[1,2]
```

---

# Final Comparison

| Approach    | Time  | Space  |
| ----------- | ----- | ------ |
| Brute       | O(n²) | O(1)   |
| HashMap     | O(n)  | O(n)   |
| Boyer-Moore | O(n)  | O(1)   |

---

# Pattern to Remember

| Majority | Max elements |
| -------- | ------------ |
| > n/2    | 1            |
| > n/3    | 2            |
| > n/k    | k-1          |

