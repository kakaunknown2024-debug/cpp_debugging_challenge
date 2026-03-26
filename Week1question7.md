# 🔁 Fix the Reverse Array

## 📝 Description  
Debug the given C++ program that attempts to reverse an array. The code contains several logical and indexing errors that lead to incorrect results for some test cases.

Your task is to identify the bugs and modify the provided code so that all test cases pass successfully.

---

## 📌 Problem Statement  

You are given an array containing `n` integers.

The program is supposed to reverse the array.

Reversing means:
```
1 2 3 4 5 → 5 4 3 2 1
```

However, the provided implementation contains bugs.

Participants must debug the existing code and fix it so that the program produces correct output for all test cases.

---

## 📥 Input Format  

- The first line contains an integer `n` representing the number of elements in the array.  
- The second line contains `n` space-separated integers representing the array elements.  

---

## 📊 Constraints  

```
1 ≤ n ≤ 10^5  
-10^9 ≤ arr[i] ≤ 10^9  
```

---

## 📤 Output Format  

Print the reversed array after fixing the code.

All elements should be printed in a single line separated by spaces.

---

## 🧪 Sample Test Case  

### Input
```
5
1 2 3 4 5
```

### Output
```
5 4 3 2 1
```

---

## 🔍 Additional Test Cases  

### Test Case 1  
**Input**
```
4
10 20 30 40
```
**Output**
```
40 30 20 10
```

---

### Test Case 2  
**Input**
```
1
100
```
**Output**
```
100
```

---

### Test Case 3  
**Input**
```
6
1 1 1 1 1 1
```
**Output**
```
1 1 1 1 1 1
```

---

### Test Case 4  
**Input**
```
3
-1 -2 -3
```
**Output**
```
-3 -2 -1
```

---

### Test Case 5 (Minimum Size)  
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

### Test Case 6 (Two Elements)  
**Input**
```
2
10 20
```
**Output**
```
20 10
```

---

### Test Case 7 (All Negative Numbers)  
**Input**
```
5
-1 -2 -3 -4 -5
```
**Output**
```
-5 -4 -3 -2 -1
```

---

### Test Case 8 (Mixed Values)  
**Input**
```
6
0 -1 5 -3 2 8
```
**Output**
```
8 2 -3 5 -1 0
```

---

### Test Case 9 (Large Values)  
**Input**
```
5
1000000000 -1000000000 999999999 -999999999 0
```
**Output**
```
0 -999999999 999999999 -1000000000 1000000000
```

---

### Test Case 10 (Palindrome Case)  
**Input**
```
5
1 2 3 2 1
```
**Output**
```
1 2 3 2 1
```

---

### Test Case 11 (General Case)  
**Input**
```
10
1 2 3 4 5 6 7 8 9 10
```
**Output**
```
10 9 8 7 6 5 4 3 2 1
```

---

## 🏷️ Tags  
`C++`, `Arrays`, `Debugging`

---

## 🐞 Faulty Code (Participants Must Debug)

Modify this code to fix the bugs and produce the correct reversed array.

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {

    int n;
    cin >> n;

    vector<int> arr(n);

    // BUG: Incorrect indexing while reading input
    for(int i = 1; i <= n; i++) {
        cin >> arr[i];
    }

    // BUG: Wrong swapping logic and loop condition
    for(int i = 0; i <= n/2; i++) {
        swap(arr[i], arr[n - i]);
    }

    // BUG: Incorrect loop boundary while printing
    for(int i = 0; i <= n; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

---

## ✅ Correct Implementation (For Organizers)

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {

    int n;
    cin >> n;

    vector<int> arr(n);

    for(int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    for(int i = 0; i < n / 2; i++) {
        swap(arr[i], arr[n - i - 1]);
    }

    for(int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }

    return 0;
}
```

---

## 📝 Note for Participants  

- You are expected to debug the existing program.  
- Try to modify the minimum number of lines to fix the logic.  
- Do not rewrite the entire program unless necessary.  
