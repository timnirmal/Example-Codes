# Untitled

{% embed url="https://www.programmersought.com/article/5951205870/" caption="" %}

```text
#include<iostream>
#include<stdlib.h>

using namespace std;
#define m 20
#define p 20

int maze[m + 2][p + 2];
int mark[m + 2][p + 2];

void setMaze() {//Set the maze shape and output
    fill(maze[0], maze[0] + (m + 2) * (p + 2), 1);
    fill(mark[0], mark[0] + (m + 2) * (p + 2), 0);
    maze[0][0] = 0;
    int i, j;
    for (j = 1; j < 13; j++)maze[1][j] = 0;
    for (i = 1; i < 10; i++)maze[i][13] = 0;
    for (j = 7; j < p + 2; j++)maze[10][j] = 0;
    for (j = 0; j < p + 2; j++) {
        for (i = 0; i < m + 2; i++)cout << maze[i][j] << " ";
        cout << endl;
    }
}

struct offsets {// coordinates
    int a, b;
};
enum directions {
    N, NE, E, SE, S, SW, W, NW
};

struct Items {// stack type
    int x, y, dir;

    Items(int a = 0, int b = 0, int c = 0) {
        x = a;
        y = b;
        dir = c;
    }

    void Print() {
        cout << "(" << x << "," << y << ")" << ends;
    }
};

template<class T>
class Stack {
private:
    int top, capacity;
public:
    T *stack; // store stack element array
    Stack(int stackCapacity = m * p);

    bool IsEmpty();

    T &Top();//return to the top element
    void Push(const T &item);//Stacked
    void Pop();//Delete the top element of the stack
    void Delete();
};

template<class T>
Stack<T>::Stack(int stackCpacity)// constructor
{
    capacity = stackCpacity;
    if (capacity < 1) throw "stack capackty must be > 0";
    stack = new T[capacity];
    top = -1;
}

template<class T>
inline bool Stack<T>::IsEmpty() {
    return top == -1;
}

template<class T>
inline T &Stack<T>::Top() {
    if (IsEmpty())throw "Stack is empty";
    return stack[top];
}

template<class T>
void Stack<T>::Push(const T &x) {
    stack[++top] = x;
}

template<class T>
void Stack<T>::Pop() {
    if (IsEmpty())throw "Stack is empty. Cannot delete.";
    stack[top--] = 0;
}

template<class T>
void Stack<T>::Delete() {
    if (stack)
        delete[]stack;
}

Items t(1, 1, N);//Initial position and orientation
Stack<Items> stack;

void path(Items temp) {
    static offsets move[8] = {-1, 0, -1, 1, 0, 1, 1, 1, 1, 0, 1, -1, 0, -1, -1, -1};
    int i = temp.x;
    int j = temp.y;
    int d = temp.dir;
    if (d > NW) {//currently a dead end
        stack.Pop();
        if (!stack.IsEmpty()) {
            temp = stack.Top();
            temp.dir++;
            path(temp);
        } else cout << "not find";
    }
    int g = i + move[d].a;
    int h = j + move[d].b;
    if ((g == m + 1) || (h == p + 1)) {// find the exit
        cout << "find" << endl;
        stack.Push(temp);
        while (!stack.IsEmpty()) {
            stack.Top().Print();
            stack.Pop();
        }
    } else if ((!maze[g][h]) && (!mark[g][h])) {//Currently not an exit, still able to continue
        stack.Push(temp); // path into the stack
        mark[g][h] = 1;
        temp.x = g;
        temp.y = h;
        temp.dir = N;
        path(temp);//recursively
    }
    else // need to change direction
    {
        temp.dir++;
        path(temp);//recursively
    }
}

int main() {
    setMaze();
    path(t);
}
```

C:\Users\timni\CLionProjects\untitled3\cmake-build-debug\untitled3.exe 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 0 0 0 0 0 0 0 0 0 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 0 1 1 1 1 1 1 1 1 1 1 1 find \(10,20\) \(10,19\) \(10,18\) \(10,17\) \(10,16\) \(10,15\) \(10,14\) \(9,13\) \(8,13\) \(7,13\) \(6,13\) \(5,13\) \(4,13\) \(3,13\) \(2,13\) \(1,13\) \( 1,12\) \(1,11\) \(1,10\) \(1,9\) \(1,8\) \(1,7\) \(1,6\) \(1,5\) \(1,4\) \(1,3\) \(1,2\) \(1,1\) Process finished with exit code 0

