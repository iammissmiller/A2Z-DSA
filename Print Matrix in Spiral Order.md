# Print Matrix in Spiral Order

## Problem

Print all elements of a matrix in **spiral order**.

### Example

```
Input:
1  2  3  4
5  6  7  8
9 10 11 12

Output:
1 2 3 4 8 12 11 10 9 5 6 7
```

---

# Idea (Boundary Traversal)

We maintain 4 boundaries:

```
top
bottom
left
right
```

Steps:

1. left → right (top row)
2. top → bottom (right column)
3. right → left (bottom row)
4. bottom → top (left column)

Repeat until boundaries cross.

---

# Optimal C++ Code

```cpp
#include <bits/stdc++.h>
using namespace std;

vector<int> spiralOrder(vector<vector<int>>& matrix)
{
    int n = matrix.size();
    int m = matrix[0].size();

    int top = 0;
    int bottom = n - 1;
    int left = 0;
    int right = m - 1;

    vector<int> ans;

    while(top <= bottom && left <= right)
    {
        // left -> right
        for(int i = left; i <= right; i++)
            ans.push_back(matrix[top][i]);
        top++;

        // top -> bottom
        for(int i = top; i <= bottom; i++)
            ans.push_back(matrix[i][right]);
        right--;

        // right -> left
        if(top <= bottom)
        {
            for(int i = right; i >= left; i--)
                ans.push_back(matrix[bottom][i]);
            bottom--;
        }

        // bottom -> top
        if(left <= right)
        {
            for(int i = bottom; i >= top; i--)
                ans.push_back(matrix[i][left]);
            left++;
        }
    }

    return ans;
}

int main()
{
    vector<vector<int>> matrix =
    {
        {1,2,3,4},
        {5,6,7,8},
        {9,10,11,12}
    };

    vector<int> ans = spiralOrder(matrix);

    for(int x : ans)
        cout << x << " ";
}
```

---

# Complexity

Time → **O(n × m)**
Space → **O(1)** (excluding output)

---

# Visualization

Matrix:

```
1  2  3  4
5  6  7  8
9 10 11 12
```

Spiral traversal:

```
→ → → →
        ↓
        ↓
← ← ←
↑
```

Order:

```
1 2 3 4 8 12 11 10 9 5 6 7
```

---

# Interview Tip

If interviewer says:

```
print matrix spiral
```

Think:

```
top, bottom, left, right boundaries
```

---
