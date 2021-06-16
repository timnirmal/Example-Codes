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

