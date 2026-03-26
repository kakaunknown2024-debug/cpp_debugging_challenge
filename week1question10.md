# 🔤 Fix the Palindrome String Check

## 📝 Description  
Debug the given C++ program that attempts to check whether a string is a palindrome. The program should ignore cases and non-alphanumeric characters, but the current implementation contains several logical errors.

Your task is to identify the bugs and modify the provided code so that all test cases pass successfully.

---

## 📌 Problem Statement  

You are given a string `s`.

The program is supposed to check whether the string is a **palindrome**, considering only alphanumeric characters and ignoring cases.

### Rules:
- Ignore all non-alphanumeric characters  
- Treat uppercase and lowercase letters as the same  

### Example:
```
Input:  "A man, a plan, a canal: Panama"
Output: YES
```

```
Input:  "race a car"
Output: NO
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

Print:
- `YES` if the string is a palindrome  
- `NO` otherwise  

---

## 🧪 Sample Test Case  

### Input
```
A man, a plan, a canal: Panama
```

### Output
```
YES
```

---

## 🔍 Additional Test Cases  

### Test Case 1 (Simple Palindrome)  
**Input**
```
racecar
```
**Output**
```
YES
```

---

### Test Case 2 (Not a Palindrome)  
**Input**
```
hello
```
**Output**
```
NO
```

---

### Test Case 3 (Mixed Case)  
**Input**
```
Madam
```
**Output**
```
YES
```

---

### Test Case 4 (Only Special Characters)  
**Input**
```
!!!@@@
```
**Output**
```
YES
```

---

### Test Case 5 (Numbers Included)  
**Input**
```
1a2
```
**Output**
```
NO
```

---

### Test Case 6 (Single Character)  
**Input**
```
z
```
**Output**
```
YES
```

---

### Test Case 7 (Empty After Filtering)  
**Input**
```
.,,
```
**Output**
```
YES
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

bool isPalindrome(string s) {

    int i = 0;
    int j = s.length() - 1;

    while(i < j) {

        // BUG: Incorrect check for alphanumeric
        if(!isalnum(s[i])) i++;
        if(!isalnum(s[j])) j--;

        // BUG: Missing continue → causes wrong comparison
        // BUG: Case not handled

        if(s[i] != s[j]) {
            return false;
        }

        i++;
        j--;
    }

    return true;
}

int main() {

    string s;
    getline(cin, s);

    if(isPalindrome(s)) {
        cout << "YES";
    } else {
        cout << "NO";
    }

    return 0;
}
```

---

## ✅ Correct Implementation (For Organizers)

```cpp
#include <iostream>
#include <string>
#include <cctype>
using namespace std;

bool isPalindrome(string s) {

    int i = 0;
    int j = s.length() - 1;

    while(i < j) {

        while(i < j && !isalnum(s[i])) i++;
        while(i < j && !isalnum(s[j])) j--;

        if(tolower(s[i]) != tolower(s[j])) {
            return false;
        }

        i++;
        j--;
    }

    return true;
}

int main() {

    string s;
    getline(cin, s);

    if(isPalindrome(s)) {
        cout << "YES";
    } else {
        cout << "NO";
    }

    return 0;
}
```



## 🚀 Takeaway

> Debugging is not just fixing syntax—it’s about understanding logic, edge cases, and flow.
