# Counter

setCounter value, increase value, show value, run number of times added

```cpp
#include <iostream>
#include <cmath>
#include <sstream>
#include <string>

using namespace std;

class Counter{
private:
    int count;
public:
    Counter() : count(0){} //Constructor
    void setCount(int c);
    void incCount();
    int show();
    void times(int t);
    //Still working on this part.
    //void equation(string eq, int x);
};

void Counter::setCount(int c) {
    count=c;
}

void Counter::incCount() {
    count++;
}

int Counter:: show(){
    return count;
}

void Counter:: times(int t){
    for(int i=0; i<t; i++){
        incCount();
    }
}
//Still working on this part
/*
void Counter::equation(string eq, int x) {
    int thing = stoi("23233");
    while (true){
        for(int i=0;i<x;){
            cout<<i<<endl;
            int thing = 0;//stoi(eq);
            i=i+thing;
        }
        break;
    }
}
*/
int main(){
    Counter c1,c2;
    c1.incCount();

    c2.times(3);

    cout<<c1.show();
    cout<<endl<<c2.show()<<endl<<endl;

    //Still working on this part.
    // c1.equation("i+2", 10);
    return 0;
}
```

