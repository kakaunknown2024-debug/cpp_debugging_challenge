# Week 1 – Debugging Question 1

## Challenge Name

Fix the Array Rotation

---

## Description

Debug the given C++ program that attempts to rotate an array to the **right by `k` positions**.
The code contains several logical and indexing errors that lead to incorrect results for some test cases.

Your task is to **identify the bugs and modify the provided code so that all test cases pass successfully**.

---

# Problem Statement

You are given an array containing **n integers** and an integer **k**.

The program is supposed to **rotate the array to the right by `k` positions**.

Right rotation means elements shifted out from the end appear again at the beginning of the array.

For example:

Array: `1 2 3 4 5`
k = `2`

Rotated Array:

`4 5 1 2 3`

However, the provided implementation contains bugs.

Participants must **debug the existing code and fix it so that the program produces correct output for all test cases**.

---

# Input Format

The first line contains an integer **n** representing the number of elements in the array.

The second line contains **n space-separated integers** representing the array elements.

The third line contains an integer **k**, representing the number of right rotations.

---

# Constraints

1
≤
𝑛
≤
10
5
1≤n≤10
5

0
≤
𝑘
≤
10
5
0≤k≤10
5

−
10
9
≤
𝑎
𝑟
𝑟
[
𝑖
]
≤
10
9
−10
9
≤arr[i]≤10
9

---

# Output Format

Print the **rotated array** after fixing the code.

All elements should be printed in **a single line separated by spaces**.

---

# Sample Test Case

### Input

```text
5
1 2 3 4 5
2
```

### Output

```text
4 5 1 2 3
```

---

# Additional Test Cases

### Test Case 1

Input

```text
5
1 2 3 4 5
1
```

Output

```text
5 1 2 3 4
```

---

### Test Case 2

Input

```text
6
10 20 30 40 50 60
3
```

Output

```text
40 50 60 10 20 30
```

---

### Test Case 3

Input

```text
4
1 2 3 4
0
```

Output

```text
1 2 3 4
```

---

### Test Case 4

Input

```text
1
100
10
```

Output

```text
100
```

---

### Test Case 5

Input

```text
7
5 6 7 8 9 10 11
2
```

Output

```text
10 11 5 6 7 8 9
```

---

# Tags

C++, Arrays, Debugging

---

# Faulty Code (Participants Must Debug)

**Modify this code to fix the bugs and produce the correct rotated array.**

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

    int k;
    cin >> k;

    vector<int> result(n);

    // BUG: Incorrect rotation logic
    for(int i = 0; i < n; i++) {
        int newIndex = (i + k) % n;
        result[i] = arr[newIndex];
    }

    // BUG: Incorrect loop boundary while printing
    for(int i = 0; i <= n; i++) {
        cout << result[i] << " ";
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

    vector<int> arr(n);

    for(int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    int k;
    cin >> k;

    k = k % n;

    vector<int> result(n);

    for(int i = 0; i < n; i++) {
        int newIndex = (i + k) % n;
        result[newIndex] = arr[i];
    }

    for(int i = 0; i < n; i++) {
        cout << result[i] << " ";
    }

    return 0;
}
```

---

# Note for Participants

* You are expected to **debug the existing program**.
* Try to **modify the minimum number of lines** to fix the logic.
* Do not rewrite the entire program unless necessary.

---
