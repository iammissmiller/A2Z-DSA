# Longest Subarray with Given Sum K (Positive Numbers)

## Problem

Given an array of **positive integers** and a number **K**, find the **length of the longest subarray** whose sum equals **K**.

### Example

```
Input:
arr = [1, 2, 1, 1, 1, 3, 2]
K = 3

Output:
3

Explanation:
Subarray = [1,1,1]
Length = 3
```

---

# 1. Brute Force Approach

## Idea

Check all possible subarrays and calculate sum.

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int longestSubarrayBrute(vector<int>& arr, int K) {

    int n = arr.size();
    int maxLen = 0;

    for(int i = 0; i < n; i++) {

        int sum = 0;

        for(int j = i; j < n; j++) {

            sum += arr[j];

            if(sum == K) {
                maxLen = max(maxLen, j - i + 1);
            }
        }
    }

    return maxLen;
}

int main() {

    vector<int> arr = {1,2,1,1,1,3,2};
    int K = 3;

    cout << longestSubarrayBrute(arr,K);
}
```

### Complexity

Time = **O(n²)**
Space = **O(1)**

---

# 2. Better Approach (Improved Brute)

## Idea

Stop early if sum exceeds K (because numbers are positive).

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int longestSubarrayBetter(vector<int>& arr, int K) {

    int n = arr.size();
    int maxLen = 0;

    for(int i = 0; i < n; i++) {

        int sum = 0;

        for(int j = i; j < n; j++) {

            sum += arr[j];

            if(sum == K) {
                maxLen = max(maxLen, j - i + 1);
            }

            if(sum > K)
                break;
        }
    }

    return maxLen;
}

int main() {

    vector<int> arr = {1,2,1,1,1,3,2};
    int K = 3;

    cout << longestSubarrayBetter(arr,K);
}
```

### Complexity

Time ≈ **O(n²)** (better in practice)
Space = **O(1)**

---

# 3. Optimal Approach (Sliding Window) ⭐ Most Important

## Idea

Since numbers are **positive**, we use **two pointers**.

### Steps

1. Expand window → increase sum
2. If sum > K → shrink window
3. If sum == K → update max length

---

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

int longestSubarrayOptimal(vector<int>& arr, int K) {

    int left = 0;
    int right = 0;
    int sum = 0;
    int maxLen = 0;

    while(right < arr.size()) {

        sum += arr[right];

        while(sum > K) {
            sum -= arr[left];
            left++;
        }

        if(sum == K) {
            maxLen = max(maxLen, right - left + 1);
        }

        right++;
    }

    return maxLen;
}

int main() {

    vector<int> arr = {1,2,1,1,1,3,2};
    int K = 3;

    cout << longestSubarrayOptimal(arr,K);
}
```

---

# Complexity (Optimal)

Time → **O(n)**
Space → **O(1)**

---

# Dry Run

Array:

```
1 2 1 1 1 3 2
K = 3
```

Window Movement:

| Window | Sum | Length |
| ------ | --- | ------ |
| 1,2    | 3   | 2      |
| 2,1    | 3   | 2      |
| 1,1,1  | 3   | 3 ✅    |

Answer = **3**

---

### Important Rule

| Array Type            | Best Method    |
| --------------------- | -------------- |
| Only positives        | Sliding Window |
| Positives + Negatives | HashMap        |


