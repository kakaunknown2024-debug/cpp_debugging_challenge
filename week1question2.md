# Week 1 – Debugging Question 2

## Challenge Name

Debug the Spiral Matrix Traversal

---

## Description

Debug the given C++ program that attempts to print the elements of a matrix in **spiral order**.

The current implementation contains logical errors related to **loop boundaries, indexing, and traversal conditions**, which leads to incorrect outputs for several test cases.

Your task is to **identify and fix the bugs in the given code so that the matrix elements are printed in the correct spiral order**.

---

# Problem Statement

You are given a matrix of size **n × m** containing integers.

The program is intended to print the elements of the matrix in **spiral order**, starting from the top-left corner and moving in a clockwise direction.

The spiral traversal order is:

1. Traverse the **top row**
2. Traverse the **right column**
3. Traverse the **bottom row**
4. Traverse the **left column**

This process continues until all elements of the matrix have been printed.

However, the provided implementation contains several bugs that cause incorrect traversal.

Participants must **debug the code and ensure that the matrix elements are printed correctly in spiral order**.

---

# Input Format

The first line contains two integers:

```
n m
```

* **n** → number of rows
* **m** → number of columns

The next **n lines** contain **m space-separated integers** representing the matrix.

---

# Constraints

* (1 \le n,m \le 500)
* (-10^9 \le matrix[i][j] \le 10^9)

---

# Output Format

Print the elements of the matrix in **spiral order**.

All elements must be printed **in a single line separated by spaces**.

---

# Sample Test Case

### Input

```text
3 3
1 2 3
4 5 6
7 8 9
```

### Output

```text
1 2 3 6 9 8 7 4 5
```

---

# Additional Test Cases

### Test Case 1

Input

```text
2 2
1 2
3 4
```

Output

```text
1 2 4 3
```

---

### Test Case 2

Input

```text
3 4
1 2 3 4
5 6 7 8
9 10 11 12
```

Output

```text
1 2 3 4 8 12 11 10 9 5 6 7
```

---

### Test Case 3

Input

```text
4 4
1 2 3 4
5 6 7 8
9 10 11 12
13 14 15 16
```

Output

```text
1 2 3 4 8 12 16 15 14 13 9 5 6 7 11 10
```

---

### Test Case 4

Input

```text
1 5
1 2 3 4 5
```

Output

```text
1 2 3 4 5
```

---

### Test Case 5

Input

```text
5 1
1
2
3
4
5
```

Output

```text
1 2 3 4 5
```

---

# Tags

C++, Arrays, Matrix, Debugging

---

# Faulty Code (Participants Must Debug)

**Modify this code to fix the bugs and correctly print the spiral traversal of the matrix.**

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {

    int n, m;
    cin >> n >> m;

    vector<vector<int>> matrix(n, vector<int>(m));

    for(int i = 0; i < n; i++)
        for(int j = 0; j < m; j++)
            cin >> matrix[i][j];

    int top = 0;
    int bottom = n;
    int left = 0;
    int right = m;

    while(top <= bottom && left <= right) {

        // Traverse top row
        for(int i = left; i <= right; i++)
            cout << matrix[top][i] << " ";
        top++;

        // Traverse right column
        for(int i = top; i <= bottom; i++)
            cout << matrix[i][right] << " ";
        right--;

        // Traverse bottom row
        for(int i = right; i >= left; i--)
            cout << matrix[bottom][i] << " ";
        bottom--;

        // Traverse left column
        for(int i = bottom; i >= top; i--)
            cout << matrix[i][left] << " ";
        left++;
    }

    return 0;
}
```

---

# Correct Implementation (For Organizers)

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {

    int n, m;
    cin >> n >> m;

    vector<vector<int>> matrix(n, vector<int>(m));

    for(int i = 0; i < n; i++)
        for(int j = 0; j < m; j++)
            cin >> matrix[i][j];

    int top = 0;
    int bottom = n - 1;
    int left = 0;
    int right = m - 1;

    while(top <= bottom && left <= right) {

        for(int i = left; i <= right; i++)
            cout << matrix[top][i] << " ";
        top++;

        for(int i = top; i <= bottom; i++)
            cout << matrix[i][right] << " ";
        right--;

        if(top <= bottom) {
            for(int i = right; i >= left; i--)
                cout << matrix[bottom][i] << " ";
            bottom--;
        }

        if(left <= right) {
            for(int i = bottom; i >= top; i--)
                cout << matrix[i][left] << " ";
            left++;
        }
    }

    return 0;
}
```

---

# Note for Participants

* You are expected to **debug the existing program**.
* Modify only the necessary parts of the code.
* Ensure the solution works for **all test cases including edge cases**.

---
