# Week 1 – Debugging Question 4

## Challenge Name

Debug the Pair Sum Finder

---

# Description

Debug the given C++ program that attempts to determine whether **two distinct elements in an array sum to a given target value `k`**.

The provided implementation contains several logical mistakes related to:

* Loop boundaries
* Incorrect conditional checks
* Improper initialization
* Handling of duplicate elements
* Incorrect early termination

Because of these issues, the program produces incorrect results for several test cases.

Your task is to **identify and fix the bugs so that the program correctly determines whether such a pair exists**.

---

# Problem Statement

You are given an array containing **n integers** and a target integer **k**.

The program attempts to determine whether **there exists a pair of distinct indices `i` and `j` such that**:

[
arr[i] + arr[j] = k
]

However, the provided implementation contains logical bugs that cause incorrect outputs.

Participants must **debug the code and ensure that the program works correctly for all inputs including edge cases**.

If a valid pair exists, print:

```text id="s4pg4y"
YES
```

Otherwise print:

```text id="g5xsl7"
NO
```

---

# Input Format

The first line contains two integers:

```text id="awpwzi"
n k
```

* **n** → number of elements in the array
* **k** → target sum

The second line contains **n space-separated integers** representing the array.

---

# Constraints

* (1 \le n \le 10^5)
* (-10^9 \le arr[i] \le 10^9)
* (-10^9 \le k \le 10^9)

---

# Output Format

Print:

* **YES** if there exists a pair whose sum equals **k**
* **NO** otherwise

---

# Sample Test Case

### Input

```text id="18dudq"
5 9
2 7 11 15 3
```

### Output

```text id="y2g88h"
YES
```

Explanation:
`2 + 7 = 9`

---

# Additional Test Cases

### Test Case 1

Input

```text id="o7y7k0"
4 10
1 2 3 4
```

Output

```text id="slheos"
NO
```

---

### Test Case 2

Input

```text id="9cm01b"
6 8
1 3 5 3 6 2
```

Output

```text id="7s0ge4"
YES
```

Explanation:
`5 + 3 = 8`

---

### Test Case 3

Input

```text id="mhrb20"
3 4
2 2 2
```

Output

```text id="h0qtgc"
YES
```

Explanation:
Two different indices can form the pair.

---

### Test Case 4

Input

```text id="jszlf6"
5 0
-1 1 2 -2 3
```

Output

```text id="sg0ghm"
YES
```

Explanation:
`-1 + 1 = 0`

---

### Test Case 5

Input

```text id="00de1f"
1 5
5
```

Output

```text id="a4m8zi"
NO
```

---

# Edge Case Test (Large Values)

### Input

```text id="zjpnqd"
4 2000000000
1000000000 1000000000 -1000000000 5
```

### Output

```text id="h2h8ab"
YES
```

Explanation:
`1000000000 + 1000000000 = 2000000000`

---

# Tags

C++, Arrays, Debugging, Loops

---

# Faulty Code (Participants Must Debug)

**Modify this code to fix the bugs and correctly determine whether a pair with sum `k` exists.**

```cpp id="t3lpyf"
#include <iostream>
#include <vector>
using namespace std;

int main() {

    int n, k;
    cin >> n >> k;

    vector<int> arr(n);

    // BUG 1: Incorrect indexing while reading input
    for(int i = 1; i <= n; i++){
        cin >> arr[i];
    }

    bool found = false;

    // BUG 2: Loop boundary errors
    for(int i = 0; i <= n; i++){

        for(int j = i; j < n; j++){

            // BUG 3: Same element used twice
            if(arr[i] + arr[j] == k){
                found = true;
            }

            // BUG 4: Incorrect break condition
            if(found = true)
                break;
        }
    }

    // BUG 5: Incorrect condition while printing result
    if(found == false)
        cout << "YES";
    else
        cout << "NO";

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

    int n;
    long long k;
    cin >> n >> k;

    vector<long long> arr(n);

    for(int i = 0; i < n; i++){
        cin >> arr[i];
    }

    bool found = false;

    for(int i = 0; i < n; i++){

        for(int j = i + 1; j < n; j++){

            if(arr[i] + arr[j] == k){
                found = true;
                break;
            }
        }

        if(found)
            break;
    }

    if(found)
        cout << "YES";
    else
        cout << "NO";

    return 0;
}
```

---

# Note for Participants

* You are expected to **debug the provided program**.
* Modify only the necessary parts of the code.
* Ensure that the program works correctly for **all edge cases**.

---
