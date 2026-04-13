
## 📌 Core Pattern – Bit Manipulation / Bitmask

Work with **individual bits** or **small sets represented as bits** to solve problems efficiently.  
Key operations include **XOR, AND, OR, shift, toggling bits, counting bits**, and **bitmasking subsets**.  
Linear-time (O(n)) solutions are often possible by **exploiting XOR properties or masks**.

When solving problems:

1. Identify if elements can be represented as **bits** (0/1, parity, sets).
2. Use **XOR** to find single/missing/duplicate numbers:
    - XOR cancels duplicates → `x ^ x = 0`
    - XOR preserves single unique number → `x ^ 0 = x`
3. Use **bitmask** to represent sets/subsets (usually <= 20 elements):
    - Each bit = presence/absence of element
    - Iterate subsets via `(mask)` or `(mask & (mask-1))`
4. Use **bit tricks** for counting, lowest set bit, or power-of-2 checks.
5. Optional: For DP problems, **use masks as state** to encode which elements are used.

|Operation / Trick|Usage|
|---|---|
|XOR (`^`)|Find unique number / cancel duplicates|
|AND (`&`)|Clear lowest set bit → `x & (x-1)`; check power-of-2 → `(x & (x-1)) == 0`|
|OR (`|`)|
|Left Shift (`<<`)|Multiply by 2, set bit position|
|Right Shift (`>>`)|Divide by 2, check bit position|
|Bitmask|Represent subsets / used elements|
|Popcount / __builtin_popcount|Count number of 1s in a number|
|x & -x|Extract lowest set bit|

## 🎯 Cue (When to Apply)

- “Single number appears once, others twice / thrice” → XOR
- “Missing or duplicate number in array” → XOR or sum trick
- “Subsets / combinations / unique chars” → Bitmask
- “Even/odd parity / toggle states” → Mask + XOR
- “Count bits, check power of 2, extract lowest set bit” → Classic bit tricks
- “DP with subsets (Partition / N Queens / Unique Concatenation)” → Masked DP

---

## ⚙️ Templates

### 1) XOR Single Number
```cpp
int singleNumber(vector<int>& nums) {
    int ans = 0;
    for (int x : nums) ans ^= x;
    return ans;
}
```


## 2) Count Bits (Popcount / Kernighan)
```cpp
int countBits(int x) {
    int count = 0;
    while (x) {
        x &= (x - 1); // remove lowest set bit
        count++;
    }
    return count;
}
```

## 3) Iterate All Subsets Using Bitmask

```cpp
int n = nums.size();
for (int mask = 0; mask < (1 << n); mask++) {
    vector<int> subset;
    for (int i = 0; i < n; i++) {
        if (mask & (1 << i)) subset.push_back(nums[i]);
    }
    // process subset
}
```


## 4) Masked DP (Partition / K Equal Sum Subsets)
```cpp
// dp[mask] = true if subset represented by mask is valid
vector<bool> dp(1 << n, false);
dp[0] = true; // empty set
for (int mask = 1; mask < (1 << n); mask++) {
    for (int i = 0; i < n; i++) {
        if (mask & (1 << i)) {
            int prev = mask ^ (1 << i);
            if (dp[prev]) {
                dp[mask] = true; // or apply sum checks
            }
        }
    }
}
```


---

## ⚠️ Misses / Edge Cases

- XOR: watch out for multiple numbers appearing more than twice → need mod-3 trick (LC 137)
- Bitmask DP: make sure mask size ≤ 20–22 to avoid memory blow-up
- Prefix XOR / parity problems: track first occurrence of mask to compute substring length
- Always check **overflow for shifts** in languages like Java / C++
- Be careful with signed numbers when using `x & -x`


---

## ⚙️Bit Manipulation + Bitmask  — CATEGORIES + VARIANTS


### 1️⃣ XOR Basics
- [x] [136. Single Number](https://leetcode.com/problems/single-number/)
- [ ] [137. Single Number II](https://leetcode.com/problems/single-number-ii/)
- [x] [268. Missing Number](https://leetcode.com/problems/missing-number/)
- [ ] [287. Find the Duplicate Number (XOR version)](https://leetcode.com/problems/find-the-duplicate-number/)

### 2️⃣ Bit Masking Core
- [ ] [78. Subsets (Bitmask Method)](https://leetcode.com/problems/subsets/)
- [ ] [78. Power Set — Custom Bitmask Version](https://leetcode.com/problems/subsets/)
- [ ] [338. Counting Bits](https://leetcode.com/problems/counting-bits/)

### 3️⃣ Classic Bit Tricks
- [ ] [191. Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/)
- [ ] [190. Reverse Bits](https://leetcode.com/problems/reverse-bits/)
- [ ] [Rightmost Set Bit Extraction — GFG](https://www.geeksforgeeks.org/find-rightmost-set-bit/)

### 4️⃣ Masked DP
- [ ] [698. Partition to K Equal Sum Subsets (Bitmask DP)](https://leetcode.com/problems/partition-to-k-equal-sum-subsets/)

### 5️⃣ Advanced Bitmask Combo
- [ ] [1239. Maximum Length of Concatenated String With Unique Characters](https://leetcode.com/problems/maximum-length-of-a-concatenated-string-with-unique-characters/)

### 6️⃣ FAANG Parity / Prefix Mask Problems
- [ ] [1371. Find the Longest Substring Containing Vowels in Even Counts](https://leetcode.com/problems/find-the-longest-substring-containing-vowels-in-even-counts/)
- [ ] [1542. Longest Awesome Substring](https://leetcode.com/problems/longest-awesome-substring/)
- [ ] [1915. Number of Wonderful Substrings](https://leetcode.com/problems/number-of-wonderful-substrings/)

---

# 💼 Bit Manipulation + Bitmask Master Checklist

## ✅ Must-Do
- [ ] [136. Single Number](https://leetcode.com/problems/single-number/)
- [ ] [137. Single Number II](https://leetcode.com/problems/single-number-ii/)
- [ ] [268. Missing Number](https://leetcode.com/problems/missing-number/)
- [ ] [287. Find the Duplicate Number (XOR version)](https://leetcode.com/problems/find-the-duplicate-number/)
- [ ] [78. Subsets (Bitmask Method)](https://leetcode.com/problems/subsets/)
- [ ] Power Set — Custom Bitmask Version (write your own)
- [ ] [338. Counting Bits](https://leetcode.com/problems/counting-bits/)
- [ ] [191. Number of 1 Bits / Hamming Weight](https://leetcode.com/problems/number-of-1-bits/)
- [ ] [190. Reverse Bits](https://leetcode.com/problems/reverse-bits/)
- [ ] Rightmost Set Bit Extraction — GFG (https://www.geeksforgeeks.org/find-rightmost-set-bit/)
- [ ] [698. Partition to K Equal Sum Subsets (Bitmask DP)](https://leetcode.com/problems/partition-to-k-equal-sum-subsets/)
- [ ] [1239. Maximum Length of Concatenated String With Unique Characters](https://leetcode.com/problems/maximum-length-of-a-concatenated-string-with-unique-characters/)

## 💡 Optional / Bonus
- [ ] [1371. Longest Substring Containing Vowels in Even Counts](https://leetcode.com/problems/find-the-longest-substring-containing-vowels-in-even-counts/)
- [ ] [1542. Longest Awesome Substring](https://leetcode.com/problems/longest-awesome-substring/)
- [ ] [1915. Number of Wonderful Substrings](https://leetcode.com/problems/number-of-wonderful-substrings/)
