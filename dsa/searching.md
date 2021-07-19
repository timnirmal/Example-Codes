# Searching

Linear Search

```cpp
#include <iostream>
using namespace std;

//Array [1,2,5,10] , arr size , value to be searched
int Linear_Search(int arr[], int arrSize, int val){
    int position = -1;
    int i=1;
    for (int j = 0; j < arrSize; j++) {
        if (arr[i] == val) {
            position = i;
            cout << i << endl;
            return i;
        }
        i++;
    }
    if(position==-1){
        cout<<"Value not present";
        return 0;
    }
}

int main() {

    int arr[4]={1,2,5,10};

    Linear_Search(arr,4,15);

    return 0;
}
```

Binary Search

{% tabs %}
{% tab title="Linear" %}
```cpp
#include <iostream>
using namespace std;

//Array [1,2,5,10] , arr size , value to be searched
int Linear_Search(int arr[], int arrSize, int val){
    int position = -1;
    int i=1;
    for (int j = 0; j < arrSize; j++) {
        if (arr[i] == val) {
            position = i;
            cout << i << endl;
            return i;
        }
        i++;
    }
    if(position==-1){
        cout<<"Value not present";
        return 0;
    }
}

int main() {

    int arr[4]={1,2,5,10};

    Linear_Search(arr,4,15);

    return 0;
}
```
{% endtab %}

{% tab title="Binary Itarative" %}
```cpp

int Binary_Search(int arr[], int lowerBound, int upperBound, int val){
    int mid = -1;

    while (lowerBound <= upperBound) {
        int mid = lowerBound + (upperBound - lowerBound) / 2;

        // Check if x is present at mid
        if (arr[mid] == val) {
        return mid;
    }
        // If x greater, ignore left half
        if (arr[mid] < val) {
            lowerBound = mid + 1;
        }
            // If x is smaller, ignore right half
        else{
            upperBound = mid - 1;}
    }

    if(mid==-1){
        cout<<"No value found";
        return 0;
    }
}

```
{% endtab %}

{% tab title="Recursive" %}
```cpp
// C++ program to implement recursive Binary Search
#include <bits/stdc++.h>
using namespace std;

// A recursive binary search function. It returns
// location of x in given array arr[l..r] is present,
// otherwise -1
int binarySearch(int arr[], int l, int r, int x)
{
	if (r >= l) {
		int mid = l + (r - l) / 2;

		// If the element is present at the middle
		// itself
		if (arr[mid] == x)
			return mid;

		// If element is smaller than mid, then
		// it can only be present in left subarray
		if (arr[mid] > x)
			return binarySearch(arr, l, mid - 1, x);

		// Else the element can only be present
		// in right subarray
		return binarySearch(arr, mid + 1, r, x);
	}

	// We reach here when element is not
	// present in array
	return -1;
}

int main(void)
{
	int arr[] = { 2, 3, 4, 10, 40 };
	int x = 10;
	int n = sizeof(arr) / sizeof(arr[0]);
	int result = binarySearch(arr, 0, n - 1, x);
	(result == -1) ? cout << "Element is not present in array"
				: cout << "Element is present at index " << result;
	return 0;
}

```
{% endtab %}

{% tab title="Interpolation" %}
```cpp

int Interpolation_Search(int arr[], int lowerBound, int upperBound, int val){
    int mid = -1;

    while (lowerBound <= upperBound) {
        int mid = lowerBound + ((upperBound - lowerBound) *(val - arr[lowerBound])/(arr[upperBound]-arr[lowerBound]));

        // Check if x is present at mid
        if (arr[mid] == val) {
            return mid;
        }
        // If x greater, ignore left half
        if (arr[mid] < val) {
            lowerBound = mid + 1;
        }
            // If x is smaller, ignore right half
        else{
            upperBound = mid - 1;}
    }

    if(mid==-1){
        cout<<"No value found";
        return 0;
    }
}

```
{% endtab %}

{% tab title="Jump" %}
```cpp

int Jump_Search(int arr[], int x, int n)
{
    // Finding block size to be jumped
    int step = sqrt(n);

    // Finding the block where element is present (if it is present)
    int prev = 0;
    while (arr[min(step, n)-1] < x)
    {
        prev = step;
        step += sqrt(n);
        if (prev >= n)
            return -1;
    }

    // Doing a linear search for x in block //beginning with prev.
    while (arr[prev] < x)
    {
        prev++;

        // If we reached next block or end of array, element is not present.
        if (prev == min(step, n))
            return -1;
    }
    // If element is found
    if (arr[prev] == x)
        return prev;

    return -1;
}

int main() {

    int arr[] = { 2, 3, 4, 10, 40 };
    int n = sizeof(arr) / sizeof(arr[0]);
    cout<<Linear_Search(arr,n,40);
    cout<<Binary_Search(arr,0,n-1,40);
    cout<<Interpolation_Search(arr, 0, n - 1, 40);
    cout<<Jump_Search(arr, 40, n);

    return 0;
}
```
{% endtab %}

{% tab title="All" %}
```

```
{% endtab %}
{% endtabs %}

Interpolation Search

