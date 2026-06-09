# Find Nth Root of a Number

## Problem

Given:

* a number `m`
* an integer `n`

Find:

```text
x such that x^n = m
```

If no integer nth root exists, return `-1`.

---

## Example 1

```cpp
n = 3
m = 27

Answer = 3
```

Because:

```cpp
3^3 = 27
```

---

## Example 2

```cpp
n = 4
m = 69

Answer = -1
```

Because no integer exists such that:

```cpp
x^4 = 69
```

---

# Brute Force Solution

## Idea

Try every number from `1` to `m`.

For each number:

```cpp
check if i^n == m
```

---

## Code

```cpp
long long power(int base, int exp) {

    long long ans = 1;

    for(int i = 0; i < exp; i++) {
        ans *= base;
    }

    return ans;
}

int nthRoot(int n, int m) {

    for(int i = 1; i <= m; i++) {

        long long val = power(i, n);

        if(val == m)
            return i;

        if(val > m)
            break;
    }

    return -1;
}
```

---

## Time Complexity

```cpp
O(m * n)
```

## Space Complexity

```cpp
O(1)
```

---

# Better Solution

## Idea

Use Binary Search on the answer space.

Possible roots lie between:

```cpp
1 to m
```

---

# Optimal Solution — Binary Search

## Key Observation

If:

```cpp
mid^n == m
```

then:

```cpp
mid is the answer
```

---

## If:

```cpp
mid^n < m
```

root lies on RIGHT side.

---

## If:

```cpp
mid^n > m
```

root lies on LEFT side.

---

# Important Optimization

While calculating:

```cpp
mid^n
```

stop early if value becomes greater than `m`.

This prevents overflow and saves time.

---

# Helper Function

## Returns

```cpp
0 -> mid^n < m
1 -> mid^n == m
2 -> mid^n > m
```

---

## Helper Code

```cpp
int check(int mid, int n, int m) {

    long long ans = 1;

    for(int i = 0; i < n; i++) {

        ans *= mid;

        if(ans > m)
            return 2;
    }

    if(ans == m)
        return 1;

    return 0;
}
```

---

# Optimal Code

```cpp
int check(int mid, int n, int m) {

    long long ans = 1;

    for(int i = 0; i < n; i++) {

        ans *= mid;

        if(ans > m)
            return 2;
    }

    if(ans == m)
        return 1;

    return 0;
}

int nthRoot(int n, int m) {

    int low = 1;
    int high = m;

    while(low <= high) {

        int mid = low + (high - low) / 2;

        int result = check(mid, n, m);

        // exact root found
        if(result == 1)
            return mid;

        // mid^n < m
        else if(result == 0)
            low = mid + 1;

        // mid^n > m
        else
            high = mid - 1;
    }

    return -1;
}
```

---

## Time Complexity

Binary search:

```cpp
O(log m)
```

For each binary search step:

```cpp
power calculation takes O(n)
```

Total:

```cpp
O(n * log m)
```

---

## Space Complexity

```cpp
O(1)
```

---

# Dry Run

```cpp
n = 3
m = 27
```

---

## Step 1

```cpp
low = 1
high = 27

mid = 14
```

```cpp
14^3 > 27
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
7^3 > 27
```

Move left.

---

## Step 3

```cpp
mid = 3
```

```cpp
3^3 = 27
```

Answer found:

```cpp
3
```

---

# Important Points

```cpp
1. Binary Search on Answer Space

2. Possible answers lie from 1 to m

3. Stop multiplication early if value exceeds m

4. Avoid overflow using long long
```
