# Minimum Days to Make M Bouquets

## Problem

You are given:

* `bloomDay[i]` = day on which the ith flower blooms
* `m` = number of bouquets needed
* `k` = flowers required per bouquet

Rules:

* Flowers used in a bouquet must be **adjacent**
* One flower can be used in only one bouquet

Find the **minimum number of days** needed to make `m` bouquets.

If impossible, return `-1`.

---

## Example

```cpp
bloomDay = [1,10,3,10,2]
m = 3
k = 1

Answer = 3
```

Explanation:

Day 3:

```cpp
[1,10,3,10,2]
 B     B     B
```

We can make 3 bouquets.

---

# Brute Force Solution

## Idea

Try every day from:

```cpp
min(bloomDay) to max(bloomDay)
```

For each day, check if it is possible to make `m` bouquets.

Return the first valid day.

---

## Helper Function

```cpp
bool canMakeBouquets(vector<int>& bloomDay, int day, int m, int k) {

    int flowers = 0;
    int bouquets = 0;

    for(int bloom : bloomDay) {

        if(bloom <= day) {

            flowers++;

            if(flowers == k) {
                bouquets++;
                flowers = 0;
            }
        }
        else {
            flowers = 0;
        }
    }

    return bouquets >= m;
}
```

---

## Code

```cpp
int minDays(vector<int>& bloomDay, int m, int k) {

    long long totalFlowers = 1LL * m * k;

    if(totalFlowers > bloomDay.size())
        return -1;

    int low = *min_element(bloomDay.begin(), bloomDay.end());
    int high = *max_element(bloomDay.begin(), bloomDay.end());

    for(int day = low; day <= high; day++) {

        if(canMakeBouquets(bloomDay, day, m, k))
            return day;
    }

    return -1;
}
```

---

## Time Complexity

```cpp
O((maxDay - minDay) * n)
```

## Space Complexity

```cpp
O(1)
```

---

# Better Solution

No meaningful intermediate solution exists.

This is a Binary Search on Answers problem.

---

# Optimal Solution — Binary Search

## Key Observation

Suppose:

```cpp
Day = 8
```

is sufficient to make `m` bouquets.

Then:

```cpp
Day = 9
Day = 10
Day = 11
...
```

will also be sufficient.

Meaning:

```cpp
Day 1  -> No
Day 2  -> No
Day 3  -> No
Day 4  -> Yes
Day 5  -> Yes
Day 6  -> Yes
...
```

This is a monotonic pattern.

Therefore Binary Search can be applied.

---

# Search Space

Minimum possible answer:

```cpp
min(bloomDay)
```

Maximum possible answer:

```cpp
max(bloomDay)
```

---

# Helper Function

## Idea

For a given day:

* Count consecutive bloomed flowers
* Whenever count reaches `k`

  * form one bouquet
  * reset count

---

## Code

```cpp
bool canMakeBouquets(vector<int>& bloomDay, int day, int m, int k) {

    int flowers = 0;
    int bouquets = 0;

    for(int bloom : bloomDay) {

        if(bloom <= day) {

            flowers++;

            if(flowers == k) {

                bouquets++;
                flowers = 0;
            }
        }
        else {

            flowers = 0;
        }
    }

    return bouquets >= m;
}
```

---

# Optimal Code

```cpp
class Solution {
public:

    bool canMakeBouquets(vector<int>& bloomDay,
                         int day,
                         int m,
                         int k) {

        int flowers = 0;
        int bouquets = 0;

        for(int bloom : bloomDay) {

            if(bloom <= day) {

                flowers++;

                if(flowers == k) {
                    bouquets++;
                    flowers = 0;
                }
            }
            else {

                flowers = 0;
            }
        }

        return bouquets >= m;
    }

    int minDays(vector<int>& bloomDay, int m, int k) {

        long long totalFlowers = 1LL * m * k;

        if(totalFlowers > bloomDay.size())
            return -1;

        int low = *min_element(bloomDay.begin(),
                               bloomDay.end());

        int high = *max_element(bloomDay.begin(),
                                bloomDay.end());

        int ans = high;

        while(low <= high) {

            int mid = low + (high - low) / 2;

            if(canMakeBouquets(bloomDay, mid, m, k)) {

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

Finding min and max:

```cpp
O(n)
```

Binary Search:

```cpp
O(log(maxDay - minDay))
```

Each step:

```cpp
O(n)
```

Total:

```cpp
O(n × log(maxDay))
```

---

## Space Complexity

```cpp
O(1)
```

---

# Dry Run

```cpp
bloomDay = [1,10,3,10,2]
m = 3
k = 1
```

Search Space:

```cpp
low = 1
high = 10
```

### mid = 5

Bloomed flowers:

```cpp
1,3,2
```

Bouquets:

```cpp
3
```

Valid.

```cpp
high = 4
```

---

### mid = 2

Bouquets:

```cpp
2
```

Not enough.

```cpp
low = 3
```

---

### mid = 3

Bouquets:

```cpp
3
```

Valid.

```cpp
high = 2
```

Loop ends.

Answer:

```cpp
3
```

---

# Important Points

```cpp
1. This is Binary Search on Answers.

2. Search Space:
   min(bloomDay) to max(bloomDay)

3. If a day works,
   all larger days also work.

4. Check impossibility first:
   m * k > n
```

---

# Common Mistakes

### Forgetting impossible case

Wrong:

```cpp
No check for m*k > n
```

Correct:

```cpp
if(1LL * m * k > bloomDay.size())
    return -1;
```

---

### Using non-adjacent flowers

Bouquets require:

```cpp
adjacent flowers only
```

Reset count whenever an unbloomed flower is encountered.

---
