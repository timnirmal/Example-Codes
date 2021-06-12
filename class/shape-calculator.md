# Shape Calculator

Rectangle

```cpp
#include <iostream>

using namespace std;

class Rectangle {
private:
    double width;
    double height;
public:
    void setData(double w, double h){
        width = w;
        height = h;
    }
    void showData(){
        cout<<"\nWidth = "<<width<<"\nHeight = "<<height<<endl;
    }
    double Area(){
        return width*height;
    }
    double Perimeter(){
        return 2*(width+height);
    }
};

int main() {
    Rectangle r1;
    r1.setData(5,10);

    r1.showData();
    cout << r1.Area()<<endl;
    cout << r1.Perimeter();

    return 0;
}
```

