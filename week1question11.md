# 🔢 Fix the Frequency Counter

## 📝 Description  
Debug the given C++ program that attempts to count the frequency of each element in an array. The program uses nested loops, but the current implementation contains logical errors that lead to incorrect counts.

Your task is to identify the bugs and modify the provided code so that all test cases pass successfully.

---

## 📌 Problem Statement  

You are given an array containing `n` integers.

The program is supposed to print the **frequency of each distinct element** in the array.

### Rules:
- Print each element only once  
- Print elements in the order of their **first occurrence**  
- Output format:  
```
element frequency
```

---

## 📥 Input Format  

- The first line contains an integer `n`  
- The second line contains `n` space-separated integers  

---

## 📊 Constraints  

```
1 ≤ n ≤ 10^4  
-10^9 ≤ arr[i] ≤ 10^9  
```

---

## 📤 Output Format  

Print each distinct element and its frequency on a new line.

---

## 🧪 Sample Test Case  

### Input
```
7
1 2 2 3 1 4 2
```

### Output
```
1 2
2 3
3 1
4 1
```

---

## 🔍 Additional Test Cases  

### Test Case 1 (All Same Elements)  
**Input**
```
5
1 1 1 1 1
```
**Output**
```
1 5
```

---

### Test Case 2 (All Unique Elements)  
**Input**
```
4
5 6 7 8
```
**Output**
```
5 1
6 1
7 1
8 1
```

---

### Test Case 3 (Negative Numbers)  
**Input**
```
6
-1 -2 -1 -2 -3 -1
```
**Output**
```
-1 3
-2 2
-3 1
```

---

### Test Case 4 (Single Element)  
**Input**
```
1
100
```
**Output**
```
100 1
```

---

### Test Case 5 (Mixed Values)  
**Input**
```
8
0 -1 0 2 -1 2 2 0
```
**Output**
```
0 3
-1 2
2 3
```

---

## 🏷️ Tags  
`C++`, `Arrays`, `Nested Loops`, `Debugging`

---

## 🐞 Faulty Code (Participants Must Debug)

Modify this code to fix the bugs and produce correct frequencies.

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {

    int n;
    cin >> n;

    vector<int> arr(n);

    // BUG: Incorrect input indexing
    for(int i = 1; i <= n; i++) {
        cin >> arr[i];
    }

    // BUG: Frequency logic incorrect
    for(int i = 0; i < n; i++) {

        int count = 0;

        for(int j = 0; j < n; j++) {
            if(arr[i] == arr[j]) {
                count++;
            }
        }

        // BUG: Prints duplicates multiple times
        cout << arr[i] << " " << count << endl;
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

    for(int i = 0; i < n; i++) {

        bool visited = false;

        // Check if already counted
        for(int k = 0; k < i; k++) {
            if(arr[k] == arr[i]) {
                visited = true;
                break;
            }
        }

        if(visited) continue;

        int count = 0;

        for(int j = 0; j < n; j++) {
            if(arr[i] == arr[j]) {
                count++;
            }
        }

        cout << arr[i] << " " << count << endl;
    }

    return 0;
}
```


## 🚀 Takeaway

> Nested loops require careful thinking—especially when avoiding duplicate processing.
