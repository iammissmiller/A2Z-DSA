# C++ basics One shot 

1. **Skeleton/Basic Structure of C++ program**

#include <iostream>
using namespace std;

int main()
{
    cout << "Hello, World!" << endl << "Hello Miller" << endl;
    return 0;
}


## \n is faster than endl; still in college and everywhere we use endl more often , why ???


2. **Basic input/output **

#include <iostream>
using namespace std;

int main()
{
    int x,y;
    cin>>x>>y;
    cout << "The value of x is " << x << " and y is " << y ;
    return 0;
}

/////complete the function printNumber which takes an integer input from the user and prints it on the screen
#include <iostream>
using namespace std;

int printNumber(int x)
{
    cin >> x ;
    cout << x ;

}

int main()
{

int x;

int y;

printNumber(x);

cout << endl;

printNumber(y);

return 0;

}


## include <bits/stdc++.h> : It includes all the libraries there are in c++ . It takes a bit more time but thats okay .

2. **Data Types**

## int - 4 bytes - range = -2,147,483,648 to 2,147,483,647

## long

## long long

## float - 4 byte

## double - 8 byte

## string :
getline(cin , s) : It also reads spaces in the input till the line breaks only , it is something cin doesnt offers it only reads untill the space .

## char



3. **if-else Statement**


//
#include <iostream>
using namespace std;

int main()
{
 int marks;

    cin >> marks;

    if(marks >= 90)
    {
        cout << "Grade A";
    }
    else if(marks >= 70)
    {
        cout << "Grade B";
    }
    else if(marks >= 50)
    {
        cout << "Grade C";
    }
    else if(marks >= 35)
    {
        cout << "Grade D";
    }
    else
    {
        cout << "Fail";
    }

    return 0;
}


4. **switch case**

#include <bits/stdc++.h>
using namespace std;


int main()
{

int day;

cin >> day;

switch(day) {

    case 1 : 
    cout << "Monday";
    break;

    case 2 : 
    cout << "tuesday";
    break;

    case 3 : 
    cout << "wednesday";
    break;

    case 4 : 
    cout << "thursday";
    break;

    case 5 : 
    cout << "friday";
    break;

    case 6 : 
    cout << "saturday";
    break;

    case 7 : 
    cout << "sunday";
    break;

    default : 
    cout << "not valid";

}

return 0;

}


5. **Arrays**

## Basic Knowledge of 1-d array
## They would teach 2-d array better in future lectures
## STL C++ Video will teach about built in array functions and alo too

6. **Strings**

## Basic knowledge pf string/array of char

7. **Functions**

## Functions are a set of code which performs something for you.

## Functions are used to modularize code.

## Functions are used to increase readability.

## Functions are used to use same code multiple time.

## Protoype of Functions

    //writing a function
    return_type function_name(parameter 1 , parameter 2)
    {
       //statements
    }


### Pass by Value Funtions

* It uses the value (kinda like a copy) of the parameter which is mostly like a copy of that value not the actual value so usually the desired change doesnt happens to 
the variable which most of the time causes few issues.

### Pass by Reference Function

* Using address of the parameter.
* By using a &(ampersand) operator.
* Since it is using the address of the parameter it is working with the original data and any operation done in this function will tamper the original data.
