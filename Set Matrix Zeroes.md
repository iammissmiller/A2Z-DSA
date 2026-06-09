# Set Matrix Zeroes

## Problem

Given an **m × n matrix**, if an element is **0**, set its **entire row and column to 0**.

The change must affect the whole row and column.

---

### Example

Input:

```
1 1 1
1 0 1
1 1 1
```

Output:

```
1 0 1
0 0 0
1 0 1
```

Explanation:

* Because position **(1,1) = 0**
* Entire **row 1** and **column 1** become zero.

---

# 1. Brute Force Approach

## Idea

Whenever a `0` is found:

* Mark its row and column with a special value (like `-1`)
* Later convert `-1` to `0`.

---

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

void setMatrixZeroesBrute(vector<vector<int>>& matrix)
{
    int m = matrix.size();
    int n = matrix[0].size();

    for(int i = 0; i < m; i++)
    {
        for(int j = 0; j < n; j++)
        {
            if(matrix[i][j] == 0)
            {
                for(int k = 0; k < n; k++)
                    if(matrix[i][k] != 0)
                        matrix[i][k] = -1;

                for(int k = 0; k < m; k++)
                    if(matrix[k][j] != 0)
                        matrix[k][j] = -1;
            }
        }
    }

    for(int i = 0; i < m; i++)
        for(int j = 0; j < n; j++)
            if(matrix[i][j] == -1)
                matrix[i][j] = 0;
}

int main()
{
    vector<vector<int>> matrix =
    {
        {1,1,1},
        {1,0,1},
        {1,1,1}
    };

    setMatrixZeroesBrute(matrix);

    for(auto row : matrix)
    {
        for(int x : row)
            cout << x << " ";
        cout << endl;
    }
}
```

### Complexity

Time → **O(n × m × (n+m))**
Space → **O(1)**

---

# 2. Better Approach (Using Extra Arrays)

## Idea

Use two arrays to mark rows and columns.

```
row[i] = 1 → row should be zero
col[j] = 1 → column should be zero
```

---

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

void setMatrixZeroesBetter(vector<vector<int>>& matrix)
{
    int m = matrix.size();
    int n = matrix[0].size();

    vector<int> row(m,0);
    vector<int> col(n,0);

    for(int i = 0; i < m; i++)
    {
        for(int j = 0; j < n; j++)
        {
            if(matrix[i][j] == 0)
            {
                row[i] = 1;
                col[j] = 1;
            }
        }
    }

    for(int i = 0; i < m; i++)
    {
        for(int j = 0; j < n; j++)
        {
            if(row[i] || col[j])
                matrix[i][j] = 0;
        }
    }
}

int main()
{
    vector<vector<int>> matrix =
    {
        {1,1,1},
        {1,0,1},
        {1,1,1}
    };

    setMatrixZeroesBetter(matrix);

    for(auto row : matrix)
    {
        for(int x : row)
            cout << x << " ";
        cout << endl;
    }
}
```

### Complexity

Time → **O(n × m)**
Space → **O(n + m)**

---

# 3. Optimal Approach (Constant Space) ⭐

## Idea

Use **first row and first column as markers**.

Steps:

1. Check if first column has zero.
2. Use first row and column to store markers.
3. Update the matrix accordingly.

---

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

void setZeroes(vector<vector<int>>& matrix)
{
    int m = matrix.size();
    int n = matrix[0].size();

    int col0 = 1;

    for(int i = 0; i < m; i++)
    {
        if(matrix[i][0] == 0)
            col0 = 0;

        for(int j = 1; j < n; j++)
        {
            if(matrix[i][j] == 0)
            {
                matrix[i][0] = 0;
                matrix[0][j] = 0;
            }
        }
    }

    for(int i = m-1; i >= 0; i--)
    {
        for(int j = n-1; j >= 1; j--)
        {
            if(matrix[i][0] == 0 || matrix[0][j] == 0)
                matrix[i][j] = 0;
        }

        if(col0 == 0)
            matrix[i][0] = 0;
    }
}

int main()
{
    vector<vector<int>> matrix =
    {
        {1,1,1},
        {1,0,1},
        {1,1,1}
    };

    setZeroes(matrix);

    for(auto row : matrix)
    {
        for(int x : row)
            cout << x << " ";
        cout << endl;
    }
}
```

---

# Complexity (Optimal)

Time → **O(n × m)**
Space → **O(1)**

---

# Interview Trick

If interviewer says:

```
Set matrix rows and columns to zero
```

Think:

```
Use first row and first column as markers
```

This is a **very famous matrix interview problem**.

---
