# Time Complexity

## What is Time Complexity ???

* Wrong thinking =  Time taken to run the - its not what time complexity actually means because different devices takes different time to run the code thats a variable thing 
dependent on the device.

* What it actually is = Rate at which the time taken increases with respectto the input size .

* It is not measured in seconds or minutes.


## Big-Oh Notation (  O() )

* Big O notation is a mathematical concept that describes the **upper bound** of an algorithm's efficiency, or how its performance (time or space) scales as the input size grows. 

* It focuses on the worst-case scenario.

* Avoid constants they do not matter for Big-Oh.

* EXAMPLE 1 : 

code:

for(i = 1; i<= N ; i++)
{
cout << i;
}


Analysis : 

1. Loop runs from 1 to N --> executes N times .
2. Each Iterations performs constant time work

therefore,
time complexity = O(N)

* For any algorithm , there are three types of cases : 

--> Best Case
--> Average Case
--> Worst case

* EXAMPLE 2 :

code :

if(marks < 25 )
{
  cout << "Grade D"
}
else if(marks < 45 )
{
  cout << "Grade C"
}
else if(marks < 65 )
{
  cout << "Grade B"
}
else
{
  cout << "Grade A"
}

ANALYSIS :

1. Best Case 

--> Best case happens when the first condotion matches.

example - marks < 25 is true then we enter the forst if. we only check only one condition , then we execute the cout . Best case time complexity = O(2).

2. Worst Case

--> Worst case happens when none of the eearlier conditions matches , and only the last condition runs.


steps checked :

1. marks < 25 - false
2. marks < 45 - false
3. marks < 65 - false
4. else executes

Worst case = O(4).



## Types of Notations 

* Big-Oh - Worst Case - Upper Bound

* Theta - Average Case

* Omega - Best Case - Lower Bound
