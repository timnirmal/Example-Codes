# My Code

## Without Colors

```cpp
/*
 0 - Path
 1 - Wall
 A - Starting Point
 B - Finish Point

 The generated puzzle must be saved to a text file

 //For Solution
 Path should replace with // and saved to another text file.
*/
#include<iostream>
#include<stdlib.h>
#include <algorithm>
#include "windows.h"

using namespace std;

const int width = 21;
const int height = 21;

int random[4] = {1,2,3,4};
int maze[width][height];

void recursion(int r, int c){
    // 4 random directions
    random_shuffle(&random[0], &random[4]);
    // Examine each direction
    for (int i = 0; i < 4; i++) {

        switch(random[i]){
            case 1: // Up
                //　Whether 2 cells up is out or not
                if (r - 2 <= 0)
                    continue;
                if (maze[r - 2][c] != 0) {
                    maze[r-2][c] = 0;
                    maze[r-1][c] = 0;
                    recursion(r - 2, c);
                }
                break;
            case 2: // Right
                // Whether 2 cells to the right is out or not
                if (c + 2 >= width - 1)
                    continue;
                if (maze[r][c + 2] != 0) {
                    maze[r][c + 2] = 0;
                    maze[r][c + 1] = 0;
                    recursion(r, c + 2);
                }
                break;
            case 3: // Down
                // Whether 2 cells down is out or not
                if (r + 2 >= height - 1)
                    continue;
                if (maze[r + 2][c] != 0) {
                    maze[r+2][c] = 0;
                    maze[r+1][c] = 0;
                    recursion(r + 2, c);
                }
                break;
            case 4: // Left
                // Whether 2 cells to the left is out or not
                if (c - 2 <= 0)
                    continue;
                if (maze[r][c - 2] != 0) {
                    maze[r][c - 2] = 0;
                    maze[r][c - 1] = 0;
                    recursion(r, c - 2);
                }
                break;
        }

        for(int i=0; i<width;i++){
            for(int j =0; j<height;j++){
                cout<< maze[i][j]<<" ";
            }
            cout<<endl;
        }
        system("cls");
    }
}

int main(){



    for(int i =0; i<width;i++){
        for(int j =0; j<height;j++){
            maze[i][j]=1;
        }
    }

    maze[1][1]=0;

    recursion(0,0);



}
```

## With 2 Colors

{% tabs %}
{% tab title="C++" %}
```cpp
/*
 0 - Path
 1 - Wall
 A - Starting Point
 B - Finish Point

 The generated puzzle must be saved to a text file

 //For Solution
 Path should replace with // and saved to another text file.
*/
#include<iostream>
#include<stdlib.h>
#include <algorithm>
#include "windows.h"

using namespace std;

const int width = 20;
const int height = 30;

int random[4] = {1,2,3,4};
int maze[width][height];

void Print_Maze(int delay){
        for(int i=0; i<width;i++){
            for(int j =0; j<height;j++){
                if(maze[i][j]==0){
                    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_RED);
                    cout<< maze[i][j]<<" ";
                }
                else{
                    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_GREEN);
                    cout<< maze[i][j]<<" ";
                }
            }
            cout<<endl;
        }
        Sleep(delay);

}

void recursion(int r, int c){

    // 4 random directions
    random_shuffle(&random[0], &random[4]);
    // Examine each direction
    for (int i = 0; i < 4; i++) {

        switch(random[i]){
            case 1: // Up
                //　Whether 2 cells up is out or not
                if (r - 2 <= 0)
                    continue;
                if (maze[r - 2][c] != 0) {
                    maze[r-2][c] = 0;
                    maze[r-1][c] = 0;
                    recursion(r - 2, c);
                }
                break;
            case 2: // Right
                // Whether 2 cells to the right is out or not
                if (c + 2 >= width - 1)
                    continue;
                if (maze[r][c + 2] != 0) {
                    maze[r][c + 2] = 0;
                    maze[r][c + 1] = 0;
                    recursion(r, c + 2);
                }
                break;
            case 3: // Down
                // Whether 2 cells down is out or not
                if (r + 2 >= height - 1)
                    continue;
                if (maze[r + 2][c] != 0) {
                    maze[r+2][c] = 0;
                    maze[r+1][c] = 0;
                    recursion(r + 2, c);
                }
                break;
            case 4: // Left
                // Whether 2 cells to the left is out or not
                if (c - 2 <= 0)
                    continue;
                if (maze[r][c - 2] != 0) {
                    maze[r][c - 2] = 0;
                    maze[r][c - 1] = 0;
                    recursion(r, c - 2);
                }
                break;
        }

       Print_Maze(1000);
        system("cls");

    }
}

int main(){

    for(int i =0; i<width;i++){
        for(int j =0; j<height;j++){
            maze[i][j]=1;
        }
    }

    maze[1][1]=0;

    recursion(1,1);

    Print_Maze(0);
}
```
{% endtab %}

{% tab title="Modifed Not worked" %}
```cpp
/*
 0 - Path
 1 - Wall
 A - Starting Point
 B - Finish Point

 The generated puzzle must be saved to a text file

 //For Solution
 Path should replace with // and saved to another text file.
*/
#include<iostream>
#include<stdlib.h>
#include <algorithm>
#include "windows.h"

using namespace std;

const int width = 10;
const int height = 10;

bool d = 0;  //Normal

int random[4] = {1,2,3,4};
int maze[width][height];

void Print_Maze(int delay){
    for(int i=0; i<height;i++){
        for(int j =0; j<width;j++){
            if(maze[i][j]==0){
                SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_RED);
                cout<< maze[i][j]<<" ";
            }
            else{
                SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_GREEN);
                cout<< maze[i][j]<<" ";
            }
        }
        cout<<endl;
    }
    Sleep(delay);

}

void recursion(int r, int c){
    // 4 random directions
    random_shuffle(&random[0], &random[4]);
    // Examine each direction
    for (int i = 0; i < 4; i++) {
        switch(random[i]){
            case 1: // Up
                //　Whether 2 cells up is out or not
                if (r - 2 <= 0)
                    continue;
                if (maze[r - 2][c] != 0) {
                    maze[r-2][c] = 0;
                    maze[r-1][c] = 0;
                    recursion(r - 2, c);
                }
                break;
            case 2: // Right
                // Whether 2 cells to the right is out or not

            /*    if (c + 2 == width){
                    d=1;
                }*/

                if (c + 2 > width -1)
                    continue;
                if (maze[r][c + 1] != 0 && c+2 == width) {
                    maze[r][c + 1] = 0;
                    recursion(r, c + 1);
                    break;
                }
                if (maze[r][c + 2] != 0) {
                    maze[r][c + 2] = 0;
                    maze[r][c + 1] = 0;
                    recursion(r, c + 2);
                }

            /*    if (maze[r][c + 2] != 0 && d==1) {
                    //maze[r][c + 2] = 0;
                    maze[r][c + 1] = 0;
                    recursion(r, c + 1);
                }*/

                break;

            case 3: // Down
                // Whether 2 cells down is out or not
                if (r + 2 > height - 1)
                    continue;
                if (maze[r+1][c] != 0 && r+2 == height) {
                    maze[r+1][c] = 0;
                    recursion(r+1, c);
                    break;
                }
                if (maze[r + 2][c] != 0) {
                    maze[r+2][c] = 0;
                    maze[r+1][c] = 0;
                    recursion(r + 2, c);
                }
                break;

            case 4: // Left
                // Whether 2 cells to the left is out or not
                if (c - 2 <= 0)
                    continue;
                if (maze[r][c - 2] != 0) {
                    maze[r][c - 2] = 0;
                    maze[r][c - 1] = 0;
                    recursion(r, c - 2);
                }
                break;
        }

      // Print_Maze(5000);
   // system("cls");

    }
}

int main(){

    for(int i =0; i<width;i++){
        for(int j =0; j<height;j++){
            maze[i][j]=1;
        }
    }

    maze[1][1]=0;

    recursion(1,1);

    Print_Maze(0);
}
```
{% endtab %}

{% tab title="Final" %}
```cpp
/*
 0 - Path
 1 - Wall
 A - Starting Point
 B - Finish Point

 The generated puzzle must be saved to a text file

 //For Solution
 Path should replace with // and saved to another text file.
*/
#include<iostream>
#include<stdlib.h>
#include <algorithm>
#include "windows.h"

using namespace std;

const int width = 21;
const int height = 21;

int random[4] = {1,2,3,4};
int maze[width][height];

void Print_Maze(int delay){
    for(int i=0; i<width;i++){
        for(int j =0; j<height;j++){
            if(maze[i][j]==0){
                SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_RED);
                cout<< maze[i][j]<<" ";
            }
            else{
                SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_GREEN);
                cout<< maze[i][j]<<" ";
            }
        }
        cout<<endl;
    }
    Sleep(delay);

}

void recursion(int x, int y){

    // 4 random directions
    random_shuffle(&random[0], &random[4]);
    // Examine each direction
    for (int i = 0; i < 4; i++) {

        switch(random[i]){
            case 1: // Up
                //　Whether 2 cells up is out or not
                if (x - 2 <= 0)
                    continue;
                if (maze[x - 2][y] != 0) {
                    maze[x - 2][y] = 0;
                    maze[x - 1][y] = 0;
                    recursion(x - 2, y);
                }
                break;
            case 2: // Right
                // Whether 2 cells to the right is out or not
                if (y + 2 >= width - 1)
                    continue;
                if (maze[x][y + 2] != 0) {
                    maze[x][y + 2] = 0;
                    maze[x][y + 1] = 0;
                    recursion(x, y + 2);
                }
                break;
            case 3: // Down
                // Whether 2 cells down is out or not
                if (x + 2 >= height - 1)
                    continue;
                if (maze[x + 2][y] != 0) {
                    maze[x + 2][y] = 0;
                    maze[x + 1][y] = 0;
                    recursion(x + 2, y);
                }
                break;
            case 4: // Left
                // Whether 2 cells to the left is out or not
                if (y - 2 <= 0)
                    continue;
                if (maze[x][y - 2] != 0) {
                    maze[x][y - 2] = 0;
                    maze[x][y - 1] = 0;
                    recursion(x, y - 2);
                }
                break;
        }

        //Print_Maze(1000);
        //system("cls");

    }
}

int main(){

    for(int i =0; i<width;i++){
        for(int j =0; j<height;j++){
            maze[i][j]=1;
        }
    }

    maze[1][1]=0;

    recursion(1,1);

    Print_Maze(0);
}

```
{% endtab %}

{% tab title="Final 2" %}
```cpp
/*
 0 - Path
 1 - Wall
 A - Starting Point
 B - Finish Point

 The generated puzzle must be saved to a text file

 //For Solution
 Path should replace with // and saved to another text file.
*/
#include<iostream>
#include<stdlib.h>
#include <algorithm>
#include "windows.h"

using namespace std;

const int width = 21;
const int height = 21;

int random[4] = {1,2,3,4};
int maze[width][height];

int mark_x =0, mark_y=0;

void Print_Maze(int delay){
    for(int i=0; i<width;i++){
        for(int j =0; j<height;j++){
            if(maze[i][j]==0){
                SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_RED);
                cout<< maze[i][j]<<" ";
            }
            else{
                SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_GREEN);
                cout<< maze[i][j]<<" ";
            }
        }
        cout<<endl;
    }
    Sleep(delay);

}

void recursion(int x, int y){

    // 4 random directions
    random_shuffle(&random[0], &random[4]);
    // Examine each direction
    for (int i = 0; i < 4; i++) {

        switch(random[i]){
            case 1: // Up
                //　Whether 2 cells up is out or not
                if (x - 2 <= 0)
                    continue;
                if (maze[x - 2][y] != 0) {
                    maze[x - 2][y] = 0;
                    maze[x - 1][y] = 0;
                    mark_x = x - 2;
                    mark_y = y;
                    recursion(x - 2, y);
                }
                break;
            case 2: // Right
                // Whether 2 cells to the right is out or not
                if (y + 2 >= width - 1)
                    continue;
                if (maze[x][y + 2] != 0) {
                    maze[x][y + 2] = 0;
                    maze[x][y + 1] = 0;
                    mark_x = x;
                    mark_y = y + 2;
                    recursion(x, y + 2);
                }
                break;
            case 3: // Down
                // Whether 2 cells down is out or not
                if (x + 2 >= height - 1)
                    continue;
                if (maze[x + 2][y] != 0) {
                    maze[x + 2][y] = 0;
                    maze[x + 1][y] = 0;
                    mark_x = x + 2;
                    mark_y = y;
                    recursion(x + 2, y);
                }
                break;
            case 4: // Left
                // Whether 2 cells to the left is out or not
                if (y - 2 <= 0)
                    continue;
                if (maze[x][y - 2] != 0) {
                    maze[x][y - 2] = 0;
                    maze[x][y - 1] = 0;
                    mark_x = x;
                    mark_y = y - 2;
                    recursion(x, y - 2);
                }
                break;
        }


        //Print_Maze(1000);
        //system("cls");

    }
}

int main(){

    for(int i =0; i<width;i++){
        for(int j =0; j<height;j++){
            maze[i][j]=1;
        }
    }

    maze[1][5]=2;

    recursion(1,5);
    maze[1][5]=2;
    maze[mark_x][mark_y] = 5;
    Print_Maze(0);
}

```
{% endtab %}
{% endtabs %}

## With Colors \(Blue\)

```cpp
/*
 0 - Path
 1 - Wall
 A - Starting Point
 B - Finish Point

 The generated puzzle must be saved to a text file

 //For Solution
 Path should replace with // and saved to another text file.
*/
#include<iostream>
#include<stdlib.h>
#include <algorithm>
#include "windows.h"

using namespace std;

const int width = 20;
const int height = 40;

int random[4] = {1, 2, 3, 4};
int maze[width][height];

void recursion(int r, int c) {

    // 4 random directions
    random_shuffle(&random[0], &random[4]);
    // Examine each direction
    for (int i = 0; i < 4; i++) {

        switch (random[i]) {
            case 1: // Up
                //　Whether 2 cells up is out or not
                if (r - 2 <= 0)
                    continue;
                if (maze[r - 2][c] != 0) {

                    if (maze[r - 2][c] == 0) {
                        maze[r - 2][c] = 4;
                    } else {
                        maze[r - 2][c] = 0;
                    }

                    if (maze[r - 1][c] == 0) {
                        maze[r - 1][c] = 4;
                    } else {
                        maze[r - 1][c] = 0;
                    }

                    recursion(r - 2, c);
                }
                break;
            case 2: // Right
                // Whether 2 cells to the right is out or not
                if (c + 2 >= width - 1)
                    continue;
                if (maze[r][c + 2] != 0) {

                    if (maze[r][c + 2] == 0) {
                        maze[r][c + 2] = 4;
                    } 
                    else{ 
                        maze[r][c + 2] = 0; 
                    }

                    if (maze[r][c + 1] == 0) {
                        maze[r][c + 1] = 4;
                    }
                    else{
                        maze[r][c + 1] = 0; 
                    }

                    recursion(r, c + 2);
                }
                break;
            case 3: // Down
                // Whether 2 cells down is out or not
                if (r + 2 >= height - 1)
                    continue;
                if (maze[r + 2][c] != 0) {
                    if (maze[r + 2][c] == 0) {
                        maze[r + 2][c] = 4;
                    } else {
                        maze[r + 2][c] = 0;
                    }

                    if (maze[r + 1][c] == 0) {
                        maze[r + 1][c] = 4;
                    } else {
                        maze[r + 1][c] = 0;
                    }
                    recursion(r + 2, c);
                }
                break;
            case 4: // Left
                // Whether 2 cells to the left is out or not
                if (c - 2 <= 0)
                    continue;
                if (maze[r][c - 2] != 0) {
                    if (maze[r][c-2] == 0) {
                        maze[r][c - 2] = 4;
                    }
                    else{ 
                        maze[r][c - 2] = 0;
                    }

                    if (maze[r][c-1] == 0) {
                        maze[r][c - 1] = 4;
                    } else { maze[r][c - 1] = 0; }

                    recursion(r, c - 2);
                }
                break;
        }

  /*      for(int i=0; i<width;i++){
            for(int j =0; j<height;j++){
                if(maze[i][j]==0){
                    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_RED);
                    cout<< maze[i][j]<<" ";
                }
                else if(maze[i][j]==4){
                    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_BLUE);
                    cout<< maze[i][j]<<" ";
                }
                else{
                    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_GREEN);
                    cout<< maze[i][j]<<" ";
                }
            }
            cout<<endl;
        }
        Sleep(100);
        system("cls");*/
    }
}

int main() {


    for (int i = 0; i < width; i++) {
        for (int j = 0; j < height; j++) {
            maze[i][j] = 1;
        }
    }

    maze[1][1] = 0;

    recursion(1, 1);

    for (int i = 0; i < width; i++) {
        for (int j = 0; j < height; j++) {
            if (maze[i][j] == 0) {
                SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_RED);
                cout << maze[i][j] << " ";
            } else if (maze[i][j] == 4) {
                SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_BLUE);
                cout << maze[i][j] << " ";
            } else {
                SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_GREEN);
                cout << maze[i][j] << " ";
            }
        }
        cout << endl;
    }
}
```

## Just 

```cpp
#include <iostream>
#include<bits/stdc++.h>
#include <cstdio>
#include <string>
#include <fstream>
#include "windows.h"
#include "Stack.h"

using namespace std;
const int MAXSIZE = 100;
int maze[MAXSIZE][MAXSIZE];

vector < pair<int, int> >  path;//The dynamic array path is used to store the path
vector < pair<int, int> >  stackk;//The dynamic array path is used to store the path

bool flag = true;//Used for recursive end return
int dir[4][2] = {//Direction array
        {- 1, 0},   //Up
        {1, 0},     //Down
        {0, - 1},   //Left
        {0, 1}      //Right
};


void print_maze(){
    cout<<endl<<endl;
    for(int i=0; i<10;i++){
        for(int j =0; j<10;j++){
            cout<<maze[i][j]<<" ";
        }
        cout<<endl;
    }
    cout<<endl<<endl;
}
void print_maze(int n){
    cout<<endl<<endl;
    for(int i=0; i<n;i++){
        for(int j =0; j<n;j++){
            cout<<maze[i][j]<<" ";
        }
        cout<<endl;
    }
    cout<<endl<<endl;
}

void DFS(int x, int y){
    cout<<"Yes";
    if(!flag) return;   //Function will be terminated if flag false (End found) (Not sure)

    if(maze[y][x] == 3){    //Found 3
        path.push_back(make_pair(y,x));
        flag = false;
        return;
    }
    if(maze[y][x] == 1) return;
    //The above judgment statement detects whether it reaches the end of the recursion

    maze[y][x] = 1;//Mark has been visited
    path.push_back(make_pair(y,x));//Add this vertex to the path
    for(int i = 0; i < 4 && flag; i++){//Continue recursive search in four directions
        DFS(y + dir[i][0], x + dir[i][1]);
    }
    if(flag) path.pop_back();//Exit the path if this vertex is not found
}

void DF_search(int x, int y){
    //cout<<"OK 200<<endl";
    if(!flag) return;
    if(maze[x][y]==3){
        cout<<"\nFound";
        cout<<" at "<<x<<" "<<y<<endl<<endl;
        return;
    }
    if(maze[y][x] == 1) return; //If visited or wall found

    maze[y][x] = 1;//Mark has been visited

    maze[y][x] = 1;//Mark has been visited

    //cout<<"hey";
    path.push_back(make_pair(x,y));//Add this vertex to the path
    stackk.push_back(make_pair(x,y));

    for(int i = 0; i < 4 && flag; i++){//Continue recursive search in four directions
        //cout<<"\nSending "<<x<<" in direction "<<dir[i][0]<<" and "<<y<<" in direction "<<dir[i][1];
        cout<<" (x,y) "<<x+dir[i][0]<<" "<<y+dir[i][1];
        DF_search(x + dir[i][0], y + dir[i][1]);
    }
    if(flag) stackk.pop_back();//Exit the path if this vertex is not found
}

void D_F_S(int x,int y){
    if(!flag) return;
    if(maze[y][x] == 3){
        path.push_back(make_pair(y,x));
        flag = false;
        return;
    }
    if(maze[y][x] == 1) return;
    //The above judgment statement detects whether it reaches the end of the recursion

    maze[y][x] = 1;//Mark has been visited
    path.push_back(make_pair(y,x));//Add this vertex to the path
    for(int i = 0; i < 4 && flag; i++){//Continue recursive search in four directions
        D_F_S(x + dir[i][0], y + dir[i][1]);
    }
    if(flag) path.pop_back();//Exit the path if this vertex is not found
}

int main(int argc, char const *argv[])
{
    int n, m;
    int x, y;

    int array[1000];
    int count = 0;

    ifstream file("C:\\Users\\timni\\CLionProjects\\untitled3\\Generated.txt");

    if(!file )
        cout<<"File not Found";
    while (!file.eof()) {
        file >> array[count];
        //Add the number to the end of the array
        count++;
    }

    int arr_size = sqrt(count);
    count = 0;
    for (int i = 0; i < arr_size; i++) {
        for (int j = 0; j < arr_size; j++) {
            maze[i][j] = array[count];
            if(array[count]==2){ //Set intial position
                cout<<endl<<i<<" "<<j<<" This is i j"<<endl;
                x = i;
                y= j;
            }
            count++;
        }
    }

    //Create copy of array
    int maze_copy[arr_size][arr_size];
    for (int i = 0; i < arr_size; i++) {
        for (int j = 0; j < arr_size; j++) {
            maze_copy[i][j] = maze[i][j];
        }
    }

    //Send intial position to stack
    //stackk.push_back(make_pair(x,y));
    //path.push_back(make_pair(x,y)); //mark as visited

    //DF_S{

    path.push_back( make_pair(x,y) );
    stackk.push_back( make_pair(x,y));

    //cout << path[0].first << " " << path[0].second << endl;
    //cout << path[0].first << " " << path[0].second << endl;
    //cout<<endl<<path.back().first<<" "<<path.back().second;

//Function
    int nLoopCount=0;

    while (true)
    {
        //if (maze[path.back().first][path.back().second] == 3) {   //termination condition
        if(nLoopCount==3){
            cout<<"\nFound";
            cout<<" at "<<x<<" "<<y<<endl<<endl;
            break;
        }
        //Functions here
        //Add adjecent items to stack
        //Need to calculate with directions
        //In here I assumed that there is wall around maze and enterece is made from there.
        cout<<"About to enter the directions.\n";
        for (int d=0; d<4; d++){
            //if(x+dir[d][0] == 0) {
            //cout<<"\nSending "<<x<<" in direction "<<dir[d][0]<<" and "<<y<<" in direction "<<dir[d][1];
            cout<<"Number from main : ";
            cout<<" (x,y) "<<x+dir[d][0]<<" "<<y+dir[d][1]<<endl;
            D_F_S(y + dir[d][0], x + dir[d][1]); //Send each value to Depth first search with direction
            //cout<<" (x,y) "<<x+dir[d][0]<<" "<<y+dir[d][1];
            //cout << "\nSend retunred";
            //}
        }
        //cout<<endl<<path.back().first<<" "<<path.back().second;
        nLoopCount++;

    }

    //cout<<"Not Found.\n";
    cout<< "Stoped at "<<x<<" "<<y<<endl<<endl;


    //Print the result
    printf("Steps: %d\n", path.size());
    printf("Path:\n");
    for (int i = 0; i < path.size(); i++) {
        printf("%d %d\n", path[i].first, path[i].second);
    }

    cout<<endl<<"Lets print the maze"<<endl;

    int cp=0;
    for (auto &i : path){
        maze_copy[i.first][i.second]=7;
    }

    cout<<endl<<endl;
    for(int i =0; i<arr_size;i++){
        for(int j =0; j<arr_size;j++){
            //cout<<path[i].first<<" "<<path[i].second<< " in "<<i<<" "<<j<<endl;
            if(maze_copy[i][j]==7){
                SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_RED);
                cout<<"# ";
            }
            else{
                SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_GREEN);
                cout<< maze_copy[i][j]<<" ";
            }
            cp++;
        }
        cout<<endl;
    }
    cout<<endl<<endl;
    for(int i =0; i<arr_size;i++){
        for(int j =0; j<arr_size;j++){
            //cout<<path[i].first<<" "<<path[i].second<< " in "<<i<<" "<<j<<endl;
            if(maze[i][j]==0){
                SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_RED);
                cout<<0<<" ";
            }
            else{
                SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), FOREGROUND_GREEN);
                cout<< maze[i][j]<<" ";
            }
            cp++;
        }
        cout<<endl;
    }

    Stack d1;
    d1.push(1);
    d1.push(2);

    cout<<d1.pop()<<endl;
    cout<<d1.peek();
    return 0;
}

//Use 2 2
//Take 4 directions select one & take others to array
//right cell dekak issarhin nathi cell ekak thynid balala

```

