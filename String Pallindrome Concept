#include <bits/stdc++.h>
using namespace std;

bool ispallindrome(int i , string &s )
{
    if(i >= s.length()/2) return true;

    if(s[i]!= s[s.length()-i-1]) return false;

    return ispallindrome(i+1,s);
}

int main()
{

    string s ;

    cin >> s;

    cout << ispallindrome(0,s) ;
    
    return 0;
}
