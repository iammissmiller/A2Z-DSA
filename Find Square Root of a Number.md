# Find Square Root of a Number

## Problem

Given a number `n`, find:

```cpp
floor(sqrt(n))
```

Meaning:

```cpp
largest integer whose square <= n
```

---

## Example 1

```cpp
n = 28

Answer = 5
```

Because:

```cpp
5 * 5 = 25
6 * 6 = 36
```

and:

```cpp
25 <= 28 < 36
```

---

## Example 2

```cpp
n = 36

Answer = 6
```

---

# Brute Force Solution

## Idea

Check every number from `1` onwards until:

```cpp
i * i > n
```

The previous number is the answer.

---

## Code

```cpp
int floorSqrt(int n) {

    int ans = 1;

    for(int i = 1; i <= n; i++) {

        long long square = 1LL * i * i;

        if(square <= n) {
            ans = i;
        }

        else {
            break;
        }
    }

    return ans;
}
```

---

## Time Complexity

```cpp
O(sqrt(n))
```

## Space Complexity

```cpp
O(1)
```

---

# Better Solution

## Idea

Use binary search on the answer space.

Possible square roots lie between:

```cpp
1 to n
```

---

# Optimal Solution — Binary Search

## Key Observation

If:

```cpp
mid * mid <= n
```

then:

```cpp
mid can be the answer
```

But maybe a larger valid answer exists.

So move right.

---

## Binary Search Logic

### Case 1

If:

```cpp
mid * mid <= n
```

store answer and move right:

```cpp
low = mid + 1
```

---

### Case 2

If:

```cpp
mid * mid > n
```

move left:

```cpp
high = mid - 1
```

---

## Optimal Code

```cpp
int floorSqrt(int n) {

    int low = 1;
    int high = n;

    int ans = 1;

    while(low <= high) {

        int mid = low + (high - low) / 2;

        long long square = 1LL * mid * mid;

        // valid answer
        if(square <= n) {

            ans = mid;

            low = mid + 1;
        }

        // too large
        else {
            high = mid - 1;
        }
    }

    return ans;
}
```

---

## Time Complexity

```cpp
O(log n)
```

## Space Complexity

```cpp
O(1)
```

---

# Dry Run

```cpp
n = 28
```

---

## Step 1

```cpp
low = 1
high = 28

mid = 14
```

```cpp
14 * 14 = 196 > 28
```

Move left:

```cpp
high = mid - 1
```

---

## Step 2

```cpp
mid = 7
```

```cpp
7 * 7 = 49 > 28
```

Move left.

---

## Step 3

```cpp
mid = 3
```

```cpp
3 * 3 = 9 <= 28
```

Valid answer.

```cpp
ans = 3
low = mid + 1
```

---

## Step 4

```cpp
mid = 5
```

```cpp
5 * 5 = 25 <= 28
```

Valid answer.

```cpp
ans = 5
```

Move right.

---

## Step 5

```cpp
mid = 6
```

```cpp
6 * 6 = 36 > 28
```

Move left.

Loop ends.

Final answer:

```cpp
5
```

---
