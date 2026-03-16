# Week 1 – Debugging Question 5

## Challenge Name

Debug the Contest Score Update System

---

# Description

During a programming contest, each participant starts with an initial score. After completing a round, each participant receives **bonus points based on their performance**.

A function is used to update each participant’s score by adding their respective bonus points.

However, the provided implementation contains bugs related to **function parameter handling, loop boundaries, and array indexing**, which causes the program to produce incorrect results.

Your task is to **debug the code so that the score updates correctly modify the original scores**.

---

# Problem Statement

You are given the initial scores of **n participants** in a programming contest.

After a round, each participant receives **a different bonus score**. The program attempts to update each participant’s score by adding the corresponding bonus value.

However, the implementation contains logical mistakes related to:

* Pass by value vs pass by reference
* Incorrect loop boundaries
* Array indexing mistakes

Participants must **debug the program so that the final scores are updated correctly**.

---

# Input Format

The first line contains an integer:

```text id="mpk3x6"
n
```

representing the number of participants.

The second line contains **n space-separated integers** representing the initial scores.

The third line contains **n space-separated integers** representing the bonus points for each participant.

---

# Constraints

* (1 \le n \le 10^5)
* (0 \le score[i] \le 10^9)
* (0 \le bonus[i] \le 10^9)

---

# Output Format

Print the **updated scores after adding the respective bonus values**.

All values must be printed in **a single line separated by spaces**.

---

# Sample Test Case

### Input

```text id="o4uw7e"
4
10 20 30 40
1 2 3 4
```

### Output

```text id="vgn45y"
11 22 33 44
```

Explanation:

```text id="fcms1k"
10 + 1 = 11
20 + 2 = 22
30 + 3 = 33
40 + 4 = 44
```

---

# Additional Test Cases

### Test Case 1

Input

```text id="47uyco"
3
5 10 15
10 20 30
```

Output

```text id="93zd3r"
15 30 45
```

---

### Test Case 2

Input

```text id="37rxm4"
5
1 1 1 1 1
2 3 4 5 6
```

Output

```text id="b4bbep"
3 4 5 6 7
```

---

### Test Case 3

Input

```text id="z3ugky"
1
100
50
```

Output

```text id="09azdf"
150
```

---

### Test Case 4

Input

```text id="nvug1c"
4
0 10 20 30
10 10 10 10
```

Output

```text id="9gphfc"
10 20 30 40
```

---

# Edge Test Case (Large Values)

### Input

```text id="0duzt4"
3
1000000000 1000000000 1000000000
1000000000 1000000000 1000000000
```

### Output

```text id="ha13s3"
2000000000 2000000000 2000000000
```

---

# Tags

C++, Functions, Arrays, Debugging

---

# Faulty Code (Participants Must Debug)

**Modify this code so that the scores update correctly.**

```cpp id="z6j6cw"
#include <iostream>
#include <vector>
using namespace std;

// Function to add bonus points
void addBonus(int score, int bonus) {
    score = score + bonus;   // BUG 1: score passed by value
}

int main() {

    int n;
    cin >> n;

    vector<int> scores(n);
    vector<int> bonus(n);

    // BUG 2: Incorrect indexing while reading scores
    for(int i = 1; i <= n; i++) {
        cin >> scores[i];
    }

    // BUG 3: Incorrect indexing while reading bonuses
    for(int i = 1; i <= n; i++) {
        cin >> bonus[i];
    }

    // BUG 4: Incorrect loop boundary
    for(int i = 0; i <= n; i++) {
        addBonus(scores[i], bonus[i]);
    }

    // Print updated scores
    for(int i = 0; i < n; i++) {
        cout << scores[i] << " ";
    }

    return 0;
}
```

---

# Correct Implementation (For Organizers)

```cpp id="d2x9gj"
#include <iostream>
#include <vector>
using namespace std;

// Pass score by reference so original value updates
void addBonus(long long &score, long long bonus) {
    score += bonus;
}

int main() {

    int n;
    cin >> n;

    vector<long long> scores(n);
    vector<long long> bonus(n);

    for(int i = 0; i < n; i++) {
        cin >> scores[i];
    }

    for(int i = 0; i < n; i++) {
        cin >> bonus[i];
    }

    for(int i = 0; i < n; i++) {
        addBonus(scores[i], bonus[i]);
    }

    for(int i = 0; i < n; i++) {
        cout << scores[i] << " ";
    }

    return 0;
}
```


