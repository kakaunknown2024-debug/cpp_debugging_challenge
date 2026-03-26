# 📈 Fix the Maximum Subarray Sum

## 📝 Description  
Debug the given C++ program that attempts to find the maximum subarray sum using Kadane’s Algorithm. The code contains several logical errors that lead to incorrect results for some test cases.

Your task is to identify the bugs and modify the provided code so that all test cases pass successfully.

---

## 📌 Problem Statement  

You are given an array containing `n` integers.

The program is supposed to find the **maximum sum of a contiguous subarray**.

### Example:
```
Array: -2 1 -3 4 -1 2 1 -5 4

Maximum Subarray:
4 -1 2 1

Sum = 6
```

However, the provided implementation contains bugs.

Participants must debug the existing code and fix it so that the program produces correct output for all test cases.

---

## 📥 Input Format  

- The first line contains an integer `n` representing the number of elements.  
- The second line contains `n` space-separated integers.  

---

## 📊 Constraints  

```
1 ≤ n ≤ 10^5  
-10^9 ≤ arr[i] ≤ 10^9  
```

---

## 📤 Output Format  

Print a single integer representing the **maximum subarray sum**.

---

## 🧪 Sample Test Case  

### Input
```
9
-2 1 -3 4 -1 2 1 -5 4
```

### Output
```
6
```

---

## 🔍 Additional Test Cases  

### Test Case 1 (All Positive)  
**Input**
```
5
1 2 3 4 5
```
**Output**
```
15
```

---

### Test Case 2 (All Negative)  
**Input**
```
4
-1 -2 -3 -4
```
**Output**
```
-1
```

---

### Test Case 3 (Single Element)  
**Input**
```
1
10
```
**Output**
```
10
```

---

### Test Case 4 (Mixed Values)  
**Input**
```
6
-2 1 -3 4 -1 2
```
**Output**
```
5
```

---

### Test Case 5 (Zero Included)  
**Input**
```
5
-1 0 -2 0 -3
```
**Output**
```
0
```

---

### Test Case 6 (Large Values)  
**Input**
```
3
1000000000 -1 1000000000
```
**Output**
```
1999999999
```

---

## 🏷️ Tags  
`C++`, `Arrays`, `Dynamic Programming`, `Debugging`

---

## 🐞 Faulty Code (Participants Must Debug)

Modify this code to fix the bugs and produce the correct maximum subarray sum.

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {

    int n;
    cin >> n;

    vector<int> arr(n);

    // BUG: Incorrect indexing
    for(int i = 1; i <= n; i++) {
        cin >> arr[i];
    }

    int maxSum = 0;
    int currSum = 0;

    for(int i = 0; i < n; i++) {
        currSum += arr[i];

        // BUG: Incorrect update order
        if(currSum < 0) {
            currSum = 0;
        }

        maxSum = max(maxSum, currSum);
    }

    cout << maxSum;

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

    int maxSum = arr[0];
    int currSum = arr[0];

    for(int i = 1; i < n; i++) {
        currSum = max(arr[i], currSum + arr[i]);
        maxSum = max(maxSum, currSum);
    }

    cout << maxSum;

    return 0;
}
```

## 🚀 Takeaway

> Kadane’s Algorithm is not just about summing—it’s about deciding whether to continue or restart the subarray.
