# Untitled



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

