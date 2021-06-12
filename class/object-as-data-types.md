# Object as Data Types

Class to getData, setData and showData using Distance.

```cpp
#include <iostream>
#include <cmath>

using namespace std;

class Distance {
private:
    float feet;
    float inch;
public:
    void setData(float ft, float in);
    void getData();
    void showData();
};

void Distance::setData(float ft, float in) {
    feet = ft;
    inch = in;
}

void Distance :: getData(){
    cout<<"Enter Feet : ";
    cin>>feet;
    cout<<"Enter inches : ";
    cin>>inch;
}

void Distance ::showData() {
    cout<<feet<<" "<<inch;
}

int main() {
    Distance d1;
    d1.setData(10.08,5.52 );
    Distance d2;
    d2.getData();

    d1.showData();
    cout<<endl;
    d2.showData();
    return 0;
}
```

