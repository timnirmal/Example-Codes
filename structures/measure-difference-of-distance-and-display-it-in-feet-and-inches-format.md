# Measure Difference of Distance and display it in feet and inches format

Two arguments to the function can be either two structures of type Distance or two variables of type float

```cpp
#include <iostream>
#include <cmath>

using namespace std;

struct Distance {
    float feet;
    float inch;
    Distance(float ft, float in){
        feet = ft;
        inch = in;
    }
};

Distance Diff_cal(Distance d1, Distance d2){
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

int main() {
    Distance d1(10.08129,5.526 );
    Distance d2(5.2873, 4.529845);
    Distance diff = Diff_cal(d1,d2);

    //Print values
    cout<<diff.feet<<" "<< diff.inch;

    cout<<endl;

    //when input is given by float directly.
    Distance diff2 = Diff_cal(125.5, 64.5);

    //Print values
    cout<<diff2.feet<<" "<< diff.inch;

    return 0;
}
```

