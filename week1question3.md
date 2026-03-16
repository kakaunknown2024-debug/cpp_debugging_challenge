# Week 1 – Debugging Question 3

## Challenge Name

Debug the Prefix Sum Array

---

## Description

Debug the given C++ program that attempts to compute the **prefix sum array** of a list of integers.

The implementation contains logical mistakes related to **array indexing, variable initialization, loop boundaries, and integer overflow**, which lead to incorrect results for several test cases.

Your task is to **identify and fix the bugs in the given code so that the prefix sum array is computed correctly for all test cases**.

---

# Problem Statement

You are given an array containing **n integers**.

The program is intended to compute the **prefix sum array**, where each element represents the sum of all elements from the beginning of the array up to that position.

Formally:

[
prefix[i] = arr[0] + arr[1] + ... + arr[i]
]

However, the provided implementation contains bugs that result in incorrect prefix sums for certain cases.

Participants must **debug the code and ensure that the prefix sum array is generated correctly**.

Some test cases may fail due to:

* Incorrect array indexing
* Uninitialized variables
* Incorrect loop boundaries
* **Integer overflow when the sum exceeds the range of `int`**

---

# Input Format

The first line contains an integer:

```text
n
```

The second line contains **n space-separated integers** representing the array.

---

# Constraints

* (1 \le n \le 10^5)
* (-10^9 \le arr[i] \le 10^9)

---

# Output Format

Print the **prefix sum array**.

All values should be printed in **a single line separated by spaces**.

---

# Sample Test Case

### Input

```text
5
1 2 3 4 5
```

### Output

```text
1 3 6 10 15
```

---

# Additional Test Cases

### Test Case 1

Input

```text
4
5 5 5 5
```

Output

```text
5 10 15 20
```

---

### Test Case 2

Input

```text
3
10 20 30
```

Output

```text
10 30 60
```

---

### Test Case 3

Input

```text
1
7
```

Output

```text
7
```

---

### Test Case 4

Input

```text
5
2 -1 3 -2 4
```

Output

```text
2 1 4 2 6
```

---

# Edge Test Cases

These test cases help detect logical mistakes and datatype issues.

### Test Case 5 – Large Values (May Fail if `int` is used for sum)

Input

```text
3
1000000000 1000000000 1000000000
```

Expected Output

```text
1000000000 2000000000 3000000000
```

Explanation:
The final prefix sum exceeds the range of a **32-bit integer**, so the program must handle the sum using **`long long`**.

---

### Test Case 6 – Mixed Large Values

Input

```text
4
1000000000 -1000000000 1000000000 1000000000
```

Expected Output

```text
1000000000 0 1000000000 2000000000
```

---

# Tags

C++, Arrays, Prefix Sum, Debugging

---

# Faulty Code (Participants Must Debug)

**Modify this code to fix the bugs and correctly compute the prefix sum array.**

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {

    int n;
    cin >> n;

    vector<int> arr(n);
    vector<int> prefix(n);

    // BUG 1: Incorrect indexing while reading input
    for(int i = 1; i <= n; i++) {
        cin >> arr[i];
    }

    // BUG 2: Variable not initialized
    int sum;

    // BUG 3: Possible integer overflow when sum becomes large
    for(int i = 0; i < n; i++) {
        sum += arr[i];
        prefix[i] = sum;
    }

    // BUG 4: Incorrect loop boundary
    for(int i = 0; i <= n; i++) {
        cout << prefix[i] << " ";
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

    int n;
    cin >> n;

    vector<long long> arr(n);
    vector<long long> prefix(n);

    for(int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    long long sum = 0;

    for(int i = 0; i < n; i++) {
        sum += arr[i];
        prefix[i] = sum;
    }

    for(int i = 0; i < n; i++) {
        cout << prefix[i] << " ";
    }

    return 0;
}
```

---



---
