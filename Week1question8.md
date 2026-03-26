# 🔄 Fix the Matrix Rotation (90 Degrees)

## 📝 Description  
Debug the given C++ program that attempts to rotate a matrix by 90 degrees clockwise. The code contains several logical and indexing errors that lead to incorrect results for some test cases.

Your task is to identify the bugs and modify the provided code so that all test cases pass successfully.

---

## 📌 Problem Statement  

You are given an `n x n` matrix.

The program is supposed to rotate the matrix by **90 degrees clockwise**.

### Rotation Rule:
```
Original:
1 2 3
4 5 6
7 8 9

Rotated:
7 4 1
8 5 2
9 6 3
```

However, the provided implementation contains bugs.

Participants must debug the existing code and fix it so that the program produces correct output for all test cases.

---

## 📥 Input Format  

- The first line contains an integer `n` representing the size of the matrix.  
- The next `n` lines each contain `n` space-separated integers representing the matrix.  

---

## 📊 Constraints  

```
1 ≤ n ≤ 500  
-10^9 ≤ matrix[i][j] ≤ 10^9  
```

---

## 📤 Output Format  

Print the rotated matrix after fixing the code.

Each row should be printed on a new line with space-separated elements.

---

## 🧪 Sample Test Case  

### Input
```
3
1 2 3
4 5 6
7 8 9
```

### Output
```
7 4 1
8 5 2
9 6 3
```

---

## 🔍 Additional Test Cases  

### Test Case 1 (n = 1)  
**Input**
```
1
5
```
**Output**
```
5
```

---

### Test Case 2 (2x2 Matrix)  
**Input**
```
2
1 2
3 4
```
**Output**
```
3 1
4 2
```

---

### Test Case 3 (All Same Values)  
**Input**
```
3
1 1 1
1 1 1
1 1 1
```
**Output**
```
1 1 1
1 1 1
1 1 1
```

---

### Test Case 4 (Negative Values)  
**Input**
```
2
-1 -2
-3 -4
```
**Output**
```
-3 -1
-4 -2
```

---

### Test Case 5 (Large Values)  
**Input**
```
2
1000000000 -1000000000
999999999 -999999999
```
**Output**
```
999999999 1000000000
-999999999 -1000000000
```

---

## 🏷️ Tags  
`C++`, `Matrix`, `Debugging`

---

## 🐞 Faulty Code (Participants Must Debug)

Modify this code to fix the bugs and produce the correct rotated matrix.

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {

    int n;
    cin >> n;

    vector<vector<int>> matrix(n, vector<int>(n));

    // BUG: Incorrect indexing while reading input
    for(int i = 1; i <= n; i++) {
        for(int j = 1; j <= n; j++) {
            cin >> matrix[i][j];
        }
    }

    // BUG: Incorrect transpose logic
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            swap(matrix[i][j], matrix[j][i]);
        }
    }

    // BUG: Incorrect reversal (should reverse rows, not entire matrix)
    reverse(matrix.begin(), matrix.end());

    // BUG: Incorrect printing loop
    for(int i = 0; i <= n; i++) {
        for(int j = 0; j <= n; j++) {
            cout << matrix[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```

---

## ✅ Correct Implementation (For Organizers)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {

    int n;
    cin >> n;

    vector<vector<int>> matrix(n, vector<int>(n));

    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            cin >> matrix[i][j];
        }
    }

    // Step 1: Transpose
    for(int i = 0; i < n; i++) {
        for(int j = i; j < n; j++) {
            swap(matrix[i][j], matrix[j][i]);
        }
    }

    // Step 2: Reverse each row
    for(int i = 0; i < n; i++) {
        reverse(matrix[i].begin(), matrix[i].end());
    }

    // Print result
    for(int i = 0; i < n; i++) {
        for(int j = 0; j < n; j++) {
            cout << matrix[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```

---

## 📝 Note for Participants  

- You are expected to debug the existing program.  
- Try to modify the minimum number of lines to fix the logic.  
- Do not rewrite the entire program unless necessary.  
