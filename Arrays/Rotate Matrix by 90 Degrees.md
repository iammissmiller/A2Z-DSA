# Rotate Matrix by 90 Degrees

## Problem

Rotate a **square matrix (n × n)** by **90 degrees clockwise** (in-place).

---

### Example

Input:

```
1 2 3
4 5 6
7 8 9
```

Output (90° clockwise):

```
7 4 1
8 5 2
9 6 3
```

---

# 1. Brute Force Approach (Using Extra Matrix)

## Idea

Create a new matrix and place elements in rotated positions.

Formula:

```
rotated[j][n-1-i] = matrix[i][j]
```

### C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> rotateBrute(vector<vector<int>>& matrix)
{
    int n = matrix.size();

    vector<vector<int>> rotated(n, vector<int>(n));

    for(int i = 0; i < n; i++)
    {
        for(int j = 0; j < n; j++)
        {
            rotated[j][n-1-i] = matrix[i][j];
        }
    }

    return rotated;
}

int main()
{
    vector<vector<int>> matrix =
    {
        {1,2,3},
        {4,5,6},
        {7,8,9}
    };

    vector<vector<int>> ans = rotateBrute(matrix);

    for(auto row : ans)
    {
        for(int x : row)
            cout << x << " ";
        cout << endl;
    }
}
```

### Complexity

Time → **O(n²)**
Space → **O(n²)**

---

# 2. Optimal Approach (Transpose + Reverse) ⭐

## Idea

Rotate 90° clockwise =

1. **Transpose matrix**
2. **Reverse each row**

---

## Step 1: Transpose

Swap:

```
matrix[i][j] ↔ matrix[j][i]
```

```
1 2 3       1 4 7
4 5 6  →    2 5 8
7 8 9       3 6 9
```

---

## Step 2: Reverse each row

```
1 4 7      7 4 1
2 5 8  →   8 5 2
3 6 9      9 6 3
```

---

# Optimal C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

void rotateMatrix(vector<vector<int>>& matrix)
{
    int n = matrix.size();

    // transpose
    for(int i = 0; i < n; i++)
    {
        for(int j = i+1; j < n; j++)
        {
            swap(matrix[i][j], matrix[j][i]);
        }
    }

    // reverse each row
    for(int i = 0; i < n; i++)
    {
        reverse(matrix[i].begin(), matrix[i].end());
    }
}

int main()
{
    vector<vector<int>> matrix =
    {
        {1,2,3},
        {4,5,6},
        {7,8,9}
    };

    rotateMatrix(matrix);

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

Time → **O(n²)**
Space → **O(1)** (in-place)

---

# Interview Tip

If interviewer says:

```
Rotate matrix by 90 degrees
```

Think:

```
Transpose + Reverse rows
```

---

# Variations

### 90° Anti-clockwise

* Transpose
* Reverse **columns**

### 180° Rotation

* Reverse rows
* Reverse columns

---
