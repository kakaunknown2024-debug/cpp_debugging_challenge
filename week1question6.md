# Week 1 – Debugging Question 6

## Challenge Name

Debug the Longest Distinct Subarray

---

# Description

Debug the given C++ program that attempts to determine the **maximum length of a subarray containing only distinct elements**.

The implementation contains logical mistakes related to **nested loops, incorrect conditional checks, improper initialization, and loop boundaries**, which causes the program to produce incorrect results.

Your task is to **identify and fix the bugs so that the program correctly computes the length of the longest subarray with all distinct elements**.

---

# Problem Statement

You are given an array containing **n integers**.

A subarray is considered **distinct** if all elements in that subarray are unique.

The program attempts to compute the **maximum length of a contiguous subarray containing only distinct elements**.

However, the provided implementation contains logical errors related to:

* Nested loop traversal
* Incorrect element comparison
* Improper variable initialization
* Loop boundary conditions

Participants must **debug the code so that the correct maximum length is printed**.

---

# Input Format

The first line contains an integer:

```text id="krm24s"
n
```

The second line contains **n space-separated integers** representing the array.

---

# Constraints

* (1 \le n \le 10^4)
* (-10^9 \le arr[i] \le 10^9)

---

# Output Format

Print a single integer representing the **maximum length of a subarray containing distinct elements**.

---

# Sample Test Case

### Input

```text id="h89apm"
5
1 2 3 1 2
```

### Output

```text id="otknj4"
3
```

Explanation:

The longest distinct subarrays are:

```text id="s47zpv"
[1,2,3]
[2,3,1]
[3,1,2]
```

Each has length **3**.

---

# Additional Test Cases

### Test Case 1

Input

```text id="fr7yfb"
6
1 2 3 4 5 6
```

Output

```text id="t0t2ol"
6
```

---

### Test Case 2

Input

```text id="ci0qlp"
6
1 1 1 1 1 1
```

Output

```text id="hjj9dd"
1
```

---

### Test Case 3

Input

```text id="v0x1b8"
7
1 2 1 3 4 2 3
```

Output

```text id="8dks8f"
4
```

Explanation:

The longest distinct subarray is:

```text id="9g8b2a"
[1,3,4,2]
```

---

### Test Case 4

Input

```text id="d34lcy"
1
5
```

Output

```text id="xpjr2k"
1
```

---

### Test Case 5

Input

```text id="5u0sx2"
8
2 3 4 5 2 3 6 7
```

Output

```text id="vt35s1"
6
```

Explanation:

Longest distinct subarray:

```text id="rujky6"
[4,5,2,3,6,7]
```

---

# Edge Test Case

### Input

```text id="y4wsy1"
5
1000000000 -1000000000 0 1000000000 -1000000000
```

### Output

```text id="8w65q3"
3
```

---

# Tags

C++, Arrays, Debugging, Nested Loops

---

# Faulty Code (Participants Must Debug)

**Modify this code so that it correctly computes the length of the longest distinct subarray.**

```cpp id="a3z6au"
#include <iostream>
#include <vector>
using namespace std;

int main() {

    int n;
    cin >> n;

    vector<int> arr(n);

    // BUG 1: Incorrect input indexing
    for(int i = 1; i <= n; i++){
        cin >> arr[i];
    }

    int maxLen;   // BUG 2: variable not initialized

    for(int i = 0; i < n; i++){

        int count = 0;

        for(int j = i; j <= n; j++){   // BUG 3: incorrect loop boundary

            bool duplicate = false;

            for(int k = i; k < j; k++){

                // BUG 4: incorrect comparison
                if(arr[k] = arr[j]){
                    duplicate = true;
                }
            }

            if(duplicate == true)
                break;

            count++;

        }

        if(count > maxLen){
            maxLen = count;
        }
    }

    cout << maxLen;

    return 0;
}
```

---

# Correct Implementation (For Organizers)

```cpp id="x1jezi"
#include <iostream>
#include <vector>
using namespace std;

int main() {

    int n;
    cin >> n;

    vector<int> arr(n);

    for(int i = 0; i < n; i++){
        cin >> arr[i];
    }

    int maxLen = 0;

    for(int i = 0; i < n; i++){

        int count = 0;

        for(int j = i; j < n; j++){

            bool duplicate = false;

            for(int k = i; k < j; k++){

                if(arr[k] == arr[j]){
                    duplicate = true;
                    break;
                }
            }

            if(duplicate)
                break;

            count++;
        }

        if(count > maxLen){
            maxLen = count;
        }
    }

    cout << maxLen;

    return 0;
}
```


---
