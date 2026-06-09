# Merge Overlapping Subintervals

## Problem

Given a list of intervals, merge all **overlapping subintervals** and return the resulting intervals.

---

### Example

```
Input:
[ [1,3], [2,6], [8,10], [15,18] ]

Output:
[ [1,6], [8,10], [15,18] ]
```

---

# Key Idea

Two intervals overlap if:

```
current.start <= previous.end
```

---

# 1. Brute Force Approach

## Idea

* Sort intervals
* For each interval, try merging with all next overlapping ones

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> mergeBrute(vector<vector<int>>& intervals)
{
    int n = intervals.size();
    vector<vector<int>> ans;

    sort(intervals.begin(), intervals.end());

    for(int i = 0; i < n; i++)
    {
        int start = intervals[i][0];
        int end = intervals[i][1];

        for(int j = i + 1; j < n; j++)
        {
            if(intervals[j][0] <= end)
            {
                end = max(end, intervals[j][1]);
            }
            else
            {
                break;
            }
        }

        ans.push_back({start, end});
    }

    return ans;
}
```

### Complexity

* Time → **O(n²)**
* Space → **O(n)**

---

# 2. Optimal Approach (Sorting + Greedy) ⭐

## Idea

* Sort intervals
* Maintain result vector
* Compare with last merged interval

---

## C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> mergeIntervals(vector<vector<int>>& intervals)
{
    vector<vector<int>> ans;

    sort(intervals.begin(), intervals.end());

    for(auto it : intervals)
    {
        if(ans.empty() || it[0] > ans.back()[1])
        {
            ans.push_back(it);
        }
        else
        {
            ans.back()[1] = max(ans.back()[1], it[1]);
        }
    }

    return ans;
}

int main()
{
    vector<vector<int>> intervals = {
        {1,3}, {2,6}, {8,10}, {15,18}
    };

    vector<vector<int>> ans = mergeIntervals(intervals);

    for(auto v : ans)
    {
        cout << "[" << v[0] << "," << v[1] << "] ";
    }
}
```

---

# Dry Run

Sorted:

```
[1,3] [2,6] [8,10] [15,18]
```

Steps:

```
[1,3] → start
[2,6] overlaps → merge → [1,6]
[8,10] → no overlap → add
[15,18] → no overlap → add
```

---

# Complexity (Optimal)

* Time → **O(n log n)** (sorting)
* Space → **O(n)**

---

# Interview Tips ⭐

If you hear:

```
merge intervals
meeting rooms
calendar scheduling
```

Think:

```
Sort + Greedy
```

---

# Common Mistakes

❌ Not sorting first
❌ Using wrong overlap condition
❌ Forgetting to update last interval

---

# Pattern

| Problem         | Approach        |
| --------------- | --------------- |
| Merge intervals | Sort + Greedy   |
| Insert interval | Same logic      |
| Meeting rooms   | Similar concept |

---
