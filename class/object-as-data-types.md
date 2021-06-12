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

Structre using classes + Default construcotor



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
    Distance(float ft=0, float in=0){
        feet =ft;
        inch=in;
    };
    Distance Diff_calc(Distance d1, Distance d2);
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

Distance Distance ::Diff_calc(Distance d1, Distance d2) {
    //Convert both feet and inches to inches
    float d1_inches = d1.feet*12.f + d1.inch;
    float d2_inches = d2.feet * 12.f + d2.inch;

    //Only take absolute value
    float diff = abs(d1_inches - d2_inches);
    //Next we need to convert these into feet and inches.
    int ft = diff / 12;
    float in = diff - ft * 12.0;
    return Distance(ft,in);
}

Distance Diff_cal(float d1, float d2){
    //Only take absolute value
    float diff = abs(d1 - d2);
    //Next we need to convert these into feet and inches.
    int ft = diff / 12;
    float in = diff - ft * 12.0;
    return Distance(ft,in);
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

