## 🔹 What is Two Pointers?

Two Pointers = using two indices to scan through an array/string (sometimes different arrays) to reduce brute-force O(n²) → O(n).  
They either **move towards each other**, **move in same direction**, or **define a sliding window**.  

---
## 🔹 Why/When to Use

- Array or string is **sorted** (or can be sorted).
- We want to find **pairs, triplets, subarrays, substrings(sliding window)**.
- Helps in problems with **constraints on sums, lengths, or windows**.
- Avoids nested loops.
- Solve in place , O(1) space -> no extra space.

---

## 🔹 Edge Cases & Pitfalls

- **Duplicates**: need to skip carefully (esp. in 3-Sum).
- **Empty/Single arrays**: while loop conditions (`l < r` vs `l <= r`).
- **Unsorted input**: may need sorting first; otherwise HashMap might be better.
- **Negatives in sliding window**: window method fails → use prefix sum or hashmap.
- **Modulo / large inputs**: careful with overflow when summing.

---

## 🔹 When NOT To Use Two Pointers

- If array is **not sorted** and sorting changes the answer.
- If condition is **non-monotonic** (e.g., subarray sum = K with negatives).
- If you need **all subarrays** instead of one longest/shortest.

---


## 🔹 Keywords to Recognize Two Pointers in Questions

- "Sorted array" + "find pair/triplet"
- "Substring/subarray longest/shortest" Sliding window
- "Palindrome check"
- "Merge/intersection of arrays"
- "Cycle detection"
- "Container/water trapping"

---

## 🔹 Core Variations of Two Pointers

### 1. **Converging Pointers (Start–End)**
- One pointer at start, one at end, moving inward.  
- Typical use: **pairs/triplets** with sum, palindrome checks.  
- There are **two categories of Converging two-pointer problems**:
1. **Order-dependent (width matters)** → Don't sort ,Why? Because width (`j - i`) is tied to original indices.
2. **Value-dependent (sum/diff matters)** → Sort first,  Why? Because sorting helps you move pointers based on sum comparison.
    
- ✅ Must-do:
  - [x] LC 167. Two Sum II (sorted)    Solution : ***[[LC 167. Two Sum II (sorted)|Click here]]
  - [x] LC 15. 3Sum    Solution : ***[[LC 15. 3Sum|Click here]]
  - [x] LC 16. 3-Sum Closest   Solution : ***[[LC 16. 3Sum Closest|Click here]]
  - [x] LC 11. Container with most water   Solution : ***[[LC 11. Container with most water|Click here]]
  - [x] LC 42. Trapping Rain Water   Solution : [[DSA PATTERNS GUIDE/All DSA Patterns/Two Pointers/LC 42. Trapping Rain Water|Solution]]
  - [x] LC 125. Valid Palindrome

---

### 2. **Sliding Window (Both Forward)**
- Right expands window, left shrinks when constraint breaks.  
- Used for **subarray problems**.  
- ✅ Must-do:
  - [ ] LC 3. Longest Substring Without Repeating Characters
  - [ ] LC 76. Minimum Window Substring
  - [ ] LC 713. Subarray Product < K
  - [ ] LC 209. Longest Subarray with Sum ≤ K

---

### 3. **Same Array, Staggered Pointers**

- Both pointers move forward but not at the same pace. [[🔀Staggered vs Fast & Slow Pointers]]
- 
- For remove duplicates, remove element, move zeros, return new length → the core is the same:  
  **Two indices: one scans(faster), one writes(slower). If condition passes, copy + advance write.**
- ✅ Must-do:
  - [x] LC 26. Remove duplicates from sorted array     Solution : ***[[LC 26. Remove Duplicates from Sorted Array|Click here]]
  - [x] LC 88. Merge Sorted Arrays in-place   Solution : ***[[LC 88. Merge Sorted Array | Click here]]
  - [x] LC 27. Remove Element   Solution : [[LC 27. Remove Element|Click here]]

---

### 4. **Different Arrays (Cross Pointers)**
- One pointer in each array, move whichever pointer gives advantage.  
- ✅ Must-do:
  - [x] LC 349. Intersection of Two Sorted Arrays    Solution : ***[[LC 349. Intersection of Two Arrays|Click here]]
  - [x] LC 350. Intersection of Two Sorted Arrays II     Solution : ***[[LC 349. Intersection of Two Arrays|Click here]]
  - [x] Smallest Common Number in 3 Arrays      Solution : ***[[GFG Common in 3 Sorted Arrays|Click here]]  
  - [x] [**LC 160 – Intersection of Two Linked Lists**](https://leetcode.com/problems/intersection-of-two-linked-lists/)   Solution : ***[[LC 160. Intersection of Two Linked Lists|Click here]]
    
---

### 5. **Two Pointers + Sorting**
- Sort first, then use pointers to reduce search space.  
- ✅ Must-do:
  - [x] 2-Sum / 3-Sum / 4-Sum
  - [x] LC 532. K-diff Pairs in an Array (Minimum Difference Pair)    Solution : ***[[LC 532. K-diff Pairs in an Array (Minimum Difference Pair)|Click here]]

---

### 6. **Two Pointers + Prefix/Greedy**
- Works when array is sorted & cumulative properties matter.  
- ✅ Must-do:
  - [x] LC 452. Minimum Number of Arrows to Burst Balloons   Solution : ***[[LC. 452. Minimum Number of Arrows to Burst Balloons|Click here]]
  - [x] LC 881. Boats to Save People  Solution : ***[[LC 881. Boats to Save People|Click here]]
  - [x] LC 986. Interval Problems (after sorting)   Solution : ***[[LC 986. Interval List Intersections|Click here]]
     ↪️ Pattern : [[🔀Two-pointer interval sweep]]
---

### 7. **Special Case: Fast & Slow Pointers**
- Pointers move at different speeds.  
- How is this different from Staggered pointers: [[🔀Staggered vs Fast & Slow Pointers]]
    -**If you're moving at different speeds to collide → cycle/meeting-type problems.**
- ✅ Must-do:
  - [x] LC 141. Linked List Cycle Detection  Solution : ***[[LC 141. Linked List Cycle]]
  - [x] LC 142. Find Start of Cycle   Solution : ***[[LC 142. Linked List Cycle II|Click here]]
  - [x] LC 202. Happy Number  :     Solution : ***[[202. Happy Number|Click here]]


---

## 🔹 Practice Set (Most Important)

- [x] LC 11. Container with most water
- [x] LC 15. 3Sum
- [x] LC 18. 4Sum       Solution : [[LC 18. 4Sum|Click here]]
- [x] LC 26. Remove duplicates from sorted array
- [x] LC 27. Remove Element   Solution : [[LC 27. Remove Element|Click here]]
- [x] LC 42. Trapping Rain Water
- [ ] LC 75. Sort Colors (Dutch flag)
- [x] LC 125. Valid Palindrome
- [x] LC 680. Valid Palindrome II (one removal allowed)   Solution : [[LC 680. Valid Palindrome II|Click here]]
- [x] LC 141. Linked list cycle
- [x] LC 283. Move Zeroes   Solution : [[LC 283. Move Zeroes|Click here]]
- [ ] LC 713. Subarray Product < K  after sliding window
- [x] LC 167. Two Sum II (sorted)
- [x] **LC 986. Interval List Intersections**
- [x] **LC 905. Sort Array by Parity**  Solution : [[LC 905. Sort Array By Parity|Click here]]
- [x] [**LC 160 – Intersection of Two Linked Lists**](https://leetcode.com/problems/intersection-of-two-linked-lists/)   Solution : ***[[LC 160. Intersection of Two Linked Lists|Click here]]
