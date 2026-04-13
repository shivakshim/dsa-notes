
[[🌸 Backtracking Patterns – The 3 Queens 👑👑👑]]
## 🌟 **Core Pattern Idea**

> **“A function calls itself on a smaller subproblem until it hits a base case — then all the results bubble back up.”**

It’s literally like zooming into a problem until it can’t get any smaller, and then reconstructing the answer while zooming back out.

Think of it as:

- 🫧 **Going down** → breaking the problem
- 💥 **Coming back up** → combining results

The magic?  
The **base case** saves you from infinite doom.

#### 🏁 **Mental Tagline**

> **“Break it down, hit base case, build it back.”**  

---

## 🧠 **Recognition Cues**

If the problem says things like:

- “solve smaller version of same problem”
- “repeat structure”
- “divide until trivial”
- “tree-like exploration”
- “all possibilities”
- “compute using previous sub-results”
- “definition refers to itself”

→ 🚨 **That’s a Recursion pattern.**

Also look for:

✅ input shrinking each step  
✅ natural “stop condition”  
✅ symmetry or repeated structure  
✅ branching choices

---

## 🧩 **Algorithm Intuition**

- Generate all subsets → recursion
- Generate all permutations → recursion
- Generate all binary strings → recursion
- Count ways to reach n using steps 1/2/3 → recursion
- Form all valid parentheses → recursion
- Build a number digit-by-digit → recursion

Over time, your brain goes:

> “Oh, this is a decision-per-index problem → recursion tree → count.”
>  If the solution is literally “for every position, try all allowed options”,  that is ALWAYS recursion/backtracking.

---

## ⚙️ **Time & Space Complexity**

|Aspect|Complexity|
|---|---|
|Time|depends on branching (often O(2ⁿ), O(n), or O(log n))|
|Space|O(height of recursion stack)|
|Tail recursion|can optimize space|

---

## 🚫 When NOT to Use Recursion

Avoid recursion if:

❌ input size is huge (stack overflow risk)  
❌ iteration is simpler and faster  
❌ branching explodes combinatorially and DP is needed  
❌ problem requires explicit loops for performance

---

## 🔑 Classic Recursion Templates

### ✅ **Template 1 — Linear Recursion**
(used for strings, arrays, digits)
```cpp
void solve(int index) {
    // Base case
    if (index == n) {
        // do something
        return;
    }
    // Recursive call
    solve(index + 1);
}
```

### ✅ **Template 2 — Two-Way / Branching Recursion**
(used for choices, include/exclude)
```cpp
void solve(int index) {
    if (index == n) {
        // reached a leaf outcome
        return;
    }
    // Option 1
    solve(index + 1);
    // Option 2
    solve(index + 1);
}
```

### ✅ **Template 3 — Divide & Conquer**
(used for trees, mergesort, power)
```cpp
int solve(Node* root) {
    if (root == NULL) return 0;
    int left = solve(root->left);
    int right = solve(root->right);
    return combine(left, right);
}
```


---

# 🧩 Recursion & Backtracking – FAANG+/Tier-1+ Master List (Tagged)


## 🌱 1️⃣Recursion Fundamentals (NOT backtracking)

- [x] **[LC 509 – Fibonacci Number](https://leetcode.com/problems/fibonacci-number/)**
- [ ] **Factorial (Classic Math)**  
- [x] **[LC 50 – Pow(x, n)](https://leetcode.com/problems/powx-n/)**                                                   [[LC 50. Pow(x, n)|💡Click here]]
- [x] **[LC 206 – Reverse Linked List (Recursive)](https://leetcode.com/problems/reverse-linked-list/)**
- [x] [Recursive atoi](https://www.geeksforgeeks.org/write-your-own-atoi/)                                                        [[LC 8. String to Integer (atoi)|💡Click here]]
- [x] [Count Good Numbers – LC 1922](https://leetcode.com/problems/count-good-numbers/)                          [[LC 1922. Count Good Numbers|💡Click here]]
- [x] [Sort a Stack Using Recursion](https://www.geeksforgeeks.org/sort-a-stack-using-recursion/)                                [[GFG. Sort stack using Recursion|💡Click here]]
- [x] [Reverse a Stack Using Recursion](https://www.geeksforgeeks.org/reverse-a-stack-using-recursion/)  (similar to sort stack)

---

## 🔢 2️⃣Subsequences Pattern  
[[🌸 Backtracking Patterns – The 3 Queens 👑👑👑]]
(⚠️ These are recursion with **subset/decision branching**.  
Some are true backtracking, some aren’t — I marked the backtracking ones.)

- [x] [Subsets– LC 78](https://leetcode.com/problems/subsets/)
- [x] [Generate All Binary Strings of Size N](https://www.geeksforgeeks.org/generate-binary-strings-without-consecutive-1s/)                  [[GFG. Generate all binary Strings without Consecutive 1's|💡Click here]]
- [ ] Subset sum 1
- [x] [Count Subsequences With Sum K](https://www.geeksforgeeks.org/count-of-subsets-with-sum-equal-to-x/)
- [x] [Check if Subsequence With Sum K Exists](https://www.geeksforgeeks.org/subset-sum-problem-dp-25/)

### 🐍 3️⃣BackTracking

- [x] [Combination Sum – LC 39](https://leetcode.com/problems/combination-sum/)                                  [[LC 39. Combination Sum|💡Click here]]
- [x] [Combination Sum II – LC 40](https://leetcode.com/problems/combination-sum-ii/) 
- [x] [Combination Sum III – LC 216](https://leetcode.com/problems/combination-sum-iii/)
- [x] [Subset Sum II – LC 90](https://leetcode.com/problems/subsets-ii/) 
- [x] [Letter Combinations of a Phone Number – LC 17](https://leetcode.com/problems/letter-combinations-of-a-phone-number/) 
- [x] [Generate Parentheses – LC 22](https://leetcode.com/problems/generate-parentheses/)                         [[LC 22. Generate Parentheses|💡Click here]]

---

## 🔥 4️⃣Hard Backtracking / Advanced  
(ALL of these are **pure backtracking**, classic DFS + undo moves.)

- [x] [Palindrome Partitioning – LC 131](https://leetcode.com/problems/palindrome-partitioning/)                    [[LC 131. Palindrome Partitioning|💡Click here]]
- [x] [Word Search – LC 79](https://leetcode.com/problems/word-search/) 
- [x] [N-Queens – LC 51](https://leetcode.com/problems/n-queens/) 
- [x] [Rat in a Maze](https://www.geeksforgeeks.org/rat-in-a-maze-backtracking-2/)
- [x] [Word Break – LC 139](https://leetcode.com/problems/word-break/)  
  (*Note: Usually DP, **but** can be done with backtracking → prune*)  
- [ ] [M Coloring Problem](https://www.geeksforgeeks.org/m-coloring-problem-backtracking-5/)   ----> solve with graphs
- [x] [Sudoku Solver – LC 37](https://leetcode.com/problems/sudoku-solver/) 
- [ ] [Expression Add Operators – LC 282](https://leetcode.com/problems/expression-add-operators/) 






- [x] [Word Search – LC 79](https://leetcode.com/problems/word-search/)
- [x] [Number of Islands – LC 200](https://leetcode.com/problems/number-of-islands/)
- [ ] [Max Area of Island – LC 695](https://leetcode.com/problems/max-area-of-island/)
- [ ] [Flood Fill – LC 733](https://leetcode.com/problems/flood-fill/)
- [ ] [Surrounded Regions – LC 130](https://leetcode.com/problems/surrounded-regions/)
- [ ] [Rotting Oranges – LC 994](https://leetcode.com/problems/rotting-oranges/)
- [ ] [Word Search II – LC 212](https://leetcode.com/problems/word-search-ii/)
- [ ] [Walls and Gates – LC 286](https://leetcode.com/problems/walls-and-gates/)
- [ ] [Shortest Path in Binary Matrix – LC 1091](https://leetcode.com/problems/shortest-path-in-binary-matrix/)
- [ ] [Pacific Atlantic Water Flow – LC 417](https://leetcode.com/problems/pacific-atlanti)
