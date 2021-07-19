# Recursive

### Count number of time a char present in string

• Write a recursive function to count the number of times a character appears in a string • Parameters:

* ch: character to be searched for and counted
* inputStr: the string to be searched
* pos: the starting position for the search

```cpp
#include <iostream>

using namespace std;


int frequency(char ch, string inputStr, int pos) {
    if (pos == inputStr.length()) {
        return 0;
    } else {
        if (inputStr[pos] == ch) {
            return 1 + frequency(ch, inputStr, pos + 1);
        } else {
            return frequency(ch, inputStr, pos + 1);
        }
    }
}

int main() {
//    - ch: character to be searched for and counted
//    - inputStr: the string to be searched
//    - pos: the starting position for the search


    cout << frequency('i', "thimira nirmal", 0);


    return 0;
}
```

### Factorial Recursive

```cpp
#include <iostream>

using namespace std;

double factorial(double num) {
    if (num==0) {
        return 1;
    } else {
        return num * factorial(num-1);
    }
}

int main() {
    cout << factorial(10);
    
    return 0;
}
```

### Great Common Divisor \(GCD\)

#### Euler's Algorithm

```cpp
#include <iostream>

using namespace std;

int gcd(int x, int y){
    cout<<"y = "<<y<<"\tx%y = "<<x%y<<endl;
    if(x%y == 0)
        return y;
    else
        return gcd(y, x%y);
}

int main() {
    cout << gcd(160,10);
    return 0;
}

//y = 160 x%y = 96
//y = 96  x%y = 64
//y = 64  x%y = 32
//y = 32  x%y = 0
//32
```

Fibonacci Series

```cpp
//Recursive
int fib(int n){
    if(n<=0)
        return 0;
    else if(n==1)
        return 1;
    else
        return fib(n-1) + fib(n-2);
}

//Iterative method is faster
int fib(int n){
    if(n<=1)
        return n;
    else{
        int n1=1, n2=0, fib;
        for (int i = 2; i <= n; i++) {
            fib = n2+n1;
            n2 = n1;
            n1 = fib;
        }
    return fib;
    }
}
```

Coin Change

```cpp
#include <iostream>

using namespace std;

//Coin array [1,2,5,10] , 8 , array size
int change(int coins[], int amount, int hCoinIdx){
    while (coins[hCoinIdx]>amount) {
        hCoinIdx--;
    }
    if(amount==0||hCoinIdx==0){
        return 1;
    }
    int numWays = 0;
    int numCoins = 0;
    while (numCoins <= amount/coins[hCoinIdx]) {
        int amntRem = amount - numCoins*coins[hCoinIdx];
        numWays = numWays + change(coins, amntRem, hCoinIdx-1);
        numCoins++;
    }
    return numWays;
}

int main() {

int coins[4]={1,2,5,10};

    cout<<change(coins,18,4);

    return 0;
}
```

