# Basic Maths Concepts (DSA)

## 1️. Digit Concept

### Separating the Last Digit

* Last digit of a number: `N % 10`
* Remove last digit: `N = N / 10`

### Generic Pseudocode

```
while (N > 0) {
    lastDigit = N % 10;
    N = N / 10;
}
```

---

## 2️. Count Digits in a Number

### Idea

Keep dividing the number by 10 and count how many times it happens.

### Pseudocode

```
count = 0
while (N > 0) {
    N = N / 10
    count++
}
print(count)
```

### Time Complexity

* **O(log₁₀ N)**

---

## 3️. Reverse a Number

### Logic

* Extract last digit
* Shift existing reversed number left
* Add extracted digit

### Pseudocode

```
revNum = 0
while (N > 0) {
    lastDigit = N % 10
    N = N / 10
    revNum = (revNum * 10) + lastDigit
}
```

Source Code

#include <bits/stdc++.h>
using namespace std;


int main()
{

    int n ; 

    cin >> n;

    int rev = 0 , last = 0;

    while(n>0)
    {
        last = n%10;
        n = n/10;
        rev = (rev * 10) + last;
    }

    cout << "Reversed number = "<< rev ;

    return 0;

}

---

## 4️. Check Palindrome Number

A number is a **palindrome** if it reads the same forward and backward.

### Steps

1. Reverse the number
2. Compare with original number

### Pseudocode

```
original = N
revNum = 0

while (N > 0) {
    lastDigit = N % 10
    N = N / 10
    revNum = (revNum * 10) + lastDigit
}

if (revNum == original)
    print("Palindrome")
else
    print("Not Palindrome")
```

Source Code 

#include <bits/stdc++.h>
using namespace std;


int main()
{

    int n ; 

    cin >> n;

    int copy = n;

    int rev = 0;  int last ;

    while(n>0)
    {
        last = n % 10;
        n = n/10;
        rev = (rev * 10) + last;
    }

    if(rev == copy)
    {
        cout << "The number " << copy << " is pallindrome";
    }
    else
    {
        cout << " The number " << copy <<" is not pallindrome";
    }

    return 0;

}

---

## 5️. Armstrong Number

### Definition

A number is an **Armstrong number** if:

> Sum of cubes of its digits = the number itself

Example:

```
371 → 3³ + 7³ + 1³ = 371
```

### Pseudocode

```
dup = N
sum = 0

while (N > 0) {
    lastDigit = N % 10
    sum = sum + (lastDigit * lastDigit * lastDigit)
    N = N / 10
}

if (sum == dup)
    print("Armstrong")
else
    print("Not Armstrong")
```
Source Code 

#include <bits/stdc++.h>
using namespace std;


int main()
{

    int n ; 

    cin >> n;

    int check = 0; int last = 0;

    while(n>0)
    {
        last = n%10;
        n = n/10;
        check = check + (last*last*last);
    }

    cout << check;

    return 0;

}

---

## 6️. Print All Divisors (Brute Force)

### Idea

Check all numbers from `1` to `N`.

### Pseudocode

```
for (i = 1; i <= N; i++) {
    if (N % i == 0)
        print(i)
}
```

### Time Complexity

* **O(N)**

---

## 7️. Check Prime Number (Basic Method)

### Definition

A **prime number** has exactly **2 divisors**: `1` and itself.

### Pseudocode

```
count = 0

for (i = 1; i <= N; i++) {
    if (N % i == 0)
        count++
}

if (count == 2)
    print("Prime")
else
    print("Not Prime")
```

Source Code 

#include <bits/stdc++.h>
using namespace std;


int main()
{

    int n ; 

    cin >> n;

    for(int i = 2; i<n ; i++)
    {
        if(n%i == 0)
        {
            cout << n << " is not prime";
            exit(0);
        }
        else
        {
            cout << n << " is prime";
            exit(0);
        }
    }

    return 0;

}

---

## 8️. Find Factors (Optimized Method)

### Optimization Insight

Divisors occur in **pairs**.
So we only loop till `√N`.

### Pseudocode

```
for (i = 1; i * i <= N; i++) {
    if (N % i == 0) {
        print(i)
        if (N / i != i)
            print(N / i)
    }
}
```

### Time Complexity

* O(√N)

---

## Key Takeaways

* `% 10` → extract digit
* `/ 10` → remove digit
* Most number problems run in **O(log N)**
* Always try to **optimize from O(N) to O(√N)** when possible

