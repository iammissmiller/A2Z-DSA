# Difference Between Recursion And Backtracking

## Recursion

### Definition

**Recursion** is a technique where a **function calls itself** to solve a problem by breaking it into **smaller subproblems**.

### Key idea

> Solve → smaller version → smaller version → base case

### Characteristics

* Has **base case** (to stop)
* Uses **function call stack**
* Not all recursion involves undoing work
* Used for **divide & conquer**, repetitive problems

### Simple Example: Print numbers from 1 to N

void print(int n)
{
    if(n == 0)      // base case
        return;

    print(n - 1);   // recursive call
    cout << n << " ";
}

```

**How it works**

* `print(5)` → `print(4)` → `print(3)` → …
* Stops at base case
* Prints while returning from stack

### Common recursion problems

* Factorial
* Fibonacci
* Tree traversal
* Merge sort
* Tower of Hanoi

---

## 2. Backtracking

### Definition

**Backtracking** is a special form of recursion where we:

1. **Try a choice**
2. **Explore**
3. **Undo (backtrack)** if it leads to a wrong or incomplete solution

### Key idea

> Try → Fail? → Undo → Try next option

### Characteristics

* Always uses **recursion**
* Involves **decision making**
* Explicitly **removes previous choice**
* Searches for **all possible solutions**

---

### Example: Generate all binary strings of length 3

void generate(string s, int n)
{
    if(s.length() == n)
    {
        cout << s << endl;
        return;
    }

    generate(s + "0", n);   // choose 0
    generate(s + "1", n);   // choose 1
}

```

This is recursion, **but also backtracking**, because:

* We try a choice
* Explore it
* Return and try another choice

---

## 3. Relation Between Them

> **All backtracking uses recursion**
> **But not all recursion is backtracking**

---

## 4. One-line Exam Answer

* **Recursion** solves a problem by breaking it into smaller subproblems.
* **Backtracking** is a recursive technique that tries all possibilities and **undoes choices** when they fail.
