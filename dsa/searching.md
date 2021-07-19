# Searching

Linear Search

```cpp
#include <iostream>
using namespace std;

//Array [1,2,5,10] , arr size , value to be searched
void Linear_Search(int arr[], int arrSize, int val){
    int position = -1;
    int i=1;
    for (int j = 0; j < arrSize; j++) {
        if (arr[i] == val) {
            position = i;
            cout << i << endl;
            return;
        }
        i++;
    }
    if(position==-1){
        cout<<"Value not present";
        return;
    }
}

int main() {

    int arr[4]={1,2,5,10};

    Linear_Search(arr,4,15);

    return 0;
}
```

