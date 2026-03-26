# 🔠 Fix the Longest Substring Without Repeating Characters

## 📝 Description  
Debug the given C++ program that attempts to find the length of the longest substring without repeating characters. The current implementation contains logical errors in handling duplicates and window movement.

Your task is to identify the bugs and modify the provided code so that all test cases pass successfully.

---

## 📌 Problem Statement  

You are given a string `s`.

The program is supposed to find the **length of the longest substring without repeating characters**.

### Example:
```
Input:  abcabcbb
Output: 3
Explanation: "abc" is the longest substring
```

However, the provided implementation contains bugs.

Participants must debug the existing code and fix it so that the program produces correct output for all test cases.

---

## 📥 Input Format  

- A single line containing the string `s`.

---

## 📊 Constraints  

```
1 ≤ length of s ≤ 10^5
```

---

## 📤 Output Format  

Print a single integer representing the length of the longest substring without repeating characters.

---

## 🧪 Sample Test Case  

### Input
```
abcabcbb
```

### Output
```
3
```

---

## 🔍 Additional Test Cases  

### Test Case 1 (All Unique Characters)  
**Input**
```
abcdef
```
**Output**
```
6
```

---

### Test Case 2 (All Same Characters)  
**Input**
```
aaaaaa
```
**Output**
```
1
```

---

### Test Case 3 (Mixed Repetition)  
**Input**
```
pwwkew
```
**Output**
```
3
```

---

### Test Case 4 (Single Character)  
**Input**
```
z
```
**Output**
```
1
```

---

### Test Case 5 (Two Characters Same)  
**Input**
```
bb
```
**Output**
```
1
```

---

### Test Case 6 (Spaces Included)  
**Input**
```
a b c a b
```
**Output**
```
3
```

---

### Test Case 7 (Special Characters)  
**Input**
```
!@#!!@#
```
**Output**
```
3
```

---

### Test Case 8 (Empty-like after repetition pattern)  
**Input**
```
abba
```
**Output**
```
2
```

---

### Test Case 9 (Long Repeating Pattern)  
**Input**
```
abcdeafghiajklmno
```
**Output**
```
10
```

---

### Test Case 10 (Edge Case - Max Constraint Pattern)  
**Input**
```
aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa
```
**Output**
```
1
```

---

## 🏷️ Tags  
`C++`, `Strings`, `Two Pointers`, `Debugging`

---

## 🐞 Faulty Code (Participants Must Debug)

Modify this code to fix the bugs and produce correct output.

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {

    string s;
    cin >> s;

    int n = s.length();
    int maxLen = 0;

    for(int i = 0; i < n; i++) {

        bool visited[256] = {false};

        int currLen = 0;

        for(int j = i; j < n; j++) {

            // BUG: Wrong condition (should break earlier)
            if(visited[s[j]] == true) {
                continue;
            }

            visited[s[j]] = true;
            currLen++;

            maxLen = max(maxLen, currLen);
        }
    }

    cout << maxLen;

    return 0;
}
```

---

## ✅ Correct Implementation (For Organizers)

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {

    string s;
    cin >> s;

    int n = s.length();
    int maxLen = 0;

    for(int i = 0; i < n; i++) {

        bool visited[256] = {false};

        int currLen = 0;

        for(int j = i; j < n; j++) {

            if(visited[s[j]]) {
                break;
            }

            visited[s[j]] = true;
            currLen++;

            maxLen = max(maxLen, currLen);
        }
    }

    cout << maxLen;

    return 0;
}
```

---

## 📝 Note for Participants  

- You are expected to debug the existing program.  
- Try to modify the minimum number of lines to fix the logic.  
- Do not rewrite the entire program unless necessary.  

---

## 🔥 Why This Problem is Final Boss

- Nested loop + logic  
- Duplicate handling tricky 😈  
- Boundary cases important  
- Easy to misunderstand logic  

---

## 🚀 Takeaway

> Correct handling of duplicates is the key to substring problems—one small mistake breaks everything.
