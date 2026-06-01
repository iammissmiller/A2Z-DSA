# Koko Eating Bananas

## Problem

Koko has `n` piles of bananas.

```cpp
piles[i] = number of bananas in ith pile
```

She can eat at a speed of `k` bananas/hour.

Rules:

* In one hour, she chooses one pile.
* Eats at most `k` bananas from that pile.
* If pile has fewer than `k`, she eats all of them.
* She wants to finish all bananas within `h` hours.

Find the **minimum eating speed `k`**.

---

## Example

```cpp
piles = [3,6,7,11]
h = 8

Answer = 4
```

Why?

```cpp
k = 4

Pile 3  -> 1 hour
Pile 6  -> 2 hours
Pile 7  -> 2 hours
Pile 11 -> 3 hours

Total = 8 hours
```

---

# Brute Force Solution

## Idea

Try every possible eating speed from:

```cpp
1 to max(piles)
```

For each speed, calculate total hours required.

First speed that satisfies:

```cpp
totalHours <= h
```

is the answer.

---

## Helper Function

```cpp
long long calculateHours(vector<int>& piles, int k) {

    long long hours = 0;

    for(int bananas : piles) {

        hours += ceil((double)bananas / k);
    }

    return hours;
}
```

---

## Code

```cpp
int minEatingSpeed(vector<int>& piles, int h) {

    int maxi = *max_element(piles.begin(), piles.end());

    for(int k = 1; k <= maxi; k++) {

        long long hours = calculateHours(piles, k);

        if(hours <= h)
            return k;
    }

    return -1;
}
```

---

## Time Complexity

```cpp
O(maxPile * n)
```

Very slow when pile values are large.

---

## Space Complexity

```cpp
O(1)
```

---

# Better Solution

No meaningful intermediate solution.

This is a classic Binary Search on Answers problem.

---

# Optimal Solution — Binary Search

## Key Observation

Suppose:

```cpp
k = 4
```

takes:

```cpp
8 hours
```

Then:

```cpp
k = 5
k = 6
k = 7
...
```

will also finish within 8 hours or less.

Meaning:

```cpp
Speed     Valid?

1         No
2         No
3         No
4         Yes
5         Yes
6         Yes
...
```

This is a:

```cpp
Monotonic Pattern
```

Perfect for Binary Search.

---

# Search Space

Minimum possible speed:

```cpp
1
```

Maximum possible speed:

```cpp
max(piles)
```

Because eating faster than the largest pile makes no difference.

---

# Helper Function

Instead of:

```cpp
ceil((double)bananas / k)
```

Use:

```cpp
(bananas + k - 1) / k
```

to avoid floating point operations.

---

## Helper Code

```cpp
long long calculateHours(vector<int>& piles, int k) {

    long long hours = 0;

    for(int bananas : piles) {

        hours += (bananas + k - 1) / k;
    }

    return hours;
}
```

---

# Binary Search Logic

## If

```cpp
hours <= h
```

then:

```cpp
k is a valid answer
```

But we want minimum speed.

Search left.

```cpp
high = mid - 1
```

---

## If

```cpp
hours > h
```

then:

```cpp
speed too slow
```

Search right.

```cpp
low = mid + 1
```

---

# Optimal Code

```cpp
class Solution {
public:

    long long calculateHours(vector<int>& piles, int k) {

        long long hours = 0;

        for(int bananas : piles) {

            hours += (bananas + k - 1) / k;
        }

        return hours;
    }

    int minEatingSpeed(vector<int>& piles, int h) {

        int low = 1;
        int high = *max_element(piles.begin(), piles.end());

        int ans = high;

        while(low <= high) {

            int mid = low + (high - low) / 2;

            long long hours = calculateHours(piles, mid);

            if(hours <= h) {

                ans = mid;
                high = mid - 1;
            }

            else {

                low = mid + 1;
            }
        }

        return ans;
    }
};
```

---

## Time Complexity

Finding max:

```cpp
O(n)
```

Binary Search:

```cpp
O(log(maxPile))
```

Each step:

```cpp
O(n)
```

Total:

```cpp
O(n × log(maxPile))
```

---

## Space Complexity

```cpp
O(1)
```

---

# Dry Run

```cpp
piles = [3,6,7,11]
h = 8
```

Search Space:

```cpp
low = 1
high = 11
```

---

## Step 1

```cpp
mid = 6
```

Hours:

```cpp
3 -> 1
6 -> 1
7 -> 2
11 -> 2

Total = 6
```

Valid.

Try smaller speed.

```cpp
high = 5
```

---

## Step 2

```cpp
mid = 3
```

Hours:

```cpp
3 -> 1
6 -> 2
7 -> 3
11 -> 4

Total = 10
```

Too slow.

```cpp
low = 4
```

---

## Step 3

```cpp
mid = 4
```

Hours:

```cpp
1 + 2 + 2 + 3 = 8
```

Valid.

```cpp
high = 3
```

Loop ends.

Answer:

```cpp
4
```

---

# Important Points

```cpp
1. This is Binary Search on Answers.

2. Search space:
   1 to max(piles)

3. Hours decrease as speed increases.

4. Monotonic behaviour makes Binary Search possible.

5. Use:
   (a + b - 1) / b

   instead of ceil(a/b)
```

---
