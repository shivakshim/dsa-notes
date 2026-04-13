## 📌 Core Pattern  - Maximum subarray sum

Find the **maximum sum of a contiguous subarray** in an array in O(n) time.
It uses **dynamic programming (running sum + reset when negative)** to achieve O(n).
When scanning the array-
1. Keep a **running sum** (`currSum`).
2. If `currSum` becomes negative → reset it (start fresh).
    - Why? Because carrying a negative sum forward will only drag down future totals.
    - For every element - "Is sum till me less than me? then only take me."
3. Track the **maximum sum so far** (`maxSoFar`).

---

## 🎯 Cue (When to Apply)

- Array problems asking for **“maximum sum” / “largest subarray” / “best profit/score”**.
- If you see phrases like:
    - “contiguous subarray”
    - “maximum sum”
    - “profit calculation"
    - “subsequence (if contiguous)”
    - “circular subarray”
- Usually involves **integers (positive/negative mix)**.

---

## ⚙️ Code Template (Kadane’s Basic)

```cpp
int kadane(int[] nums) {   
  int maxSoFar = nums[0];   
  int currSum = nums[0];    
      for (int i = 1; i < nums.length; i++) {  
             currSum = Math.max(nums[i], currSum + nums[i]);    
             maxSoFar = Math.max(maxSoFar, currSum);   
           }   
        return maxSoFar;
    }
```


---

## ⚠️ Misses / Edge Cases

- **All negatives** → Kadane's still works, but you must initialize with `nums[0]`.
- **Empty array** → sometimes interviewers expect you to clarify.
- **Circular arrays** (wrap-around sums) → requires variant (see below).
- **Single element arrays** → just return that element.

---

## 🔑 Keywords in Question

- _“maximum sum subarray”
- _“largest contiguous subarray sum”
- _“best time / profit / score in interval”_
- _“wrap-around / circular array”_
- _“subarray with at least k length”_


---

## 🔀 Variants & Must-Do Questions

### 1️⃣ Classic Kadane (Max Subarray Sum)

- **Use case**: Largest sum of contiguous elements.
- **Cue**: “maximum subarray sum” directly.
- **Must-do**: 
- [x] [LC 53 – Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)

### 2️⃣ Circular Kadane

- **Use case**: Array is circular (wrap-around subarray).
- **Cue**: Mentions _“circular array”_, _“wrap around”_.
- **Approach**: `maxNormal = Kadane()`, `maxCircular = totalSum - minSubarraySum`. Answer = max(maxNormal, maxCircular).
- **Must-do**:
- [x] [LC 918 – Maximum Sum Circular Subarray](https://leetcode.com/problems/maximum-sum-circular-subarray/)    Solution : ***[[LC 918. Maximum Sum Circular Subarray|Click here]]

### 3️⃣ Maximum Product Subarray

- **Use case**: Instead of sum, maximize product (negatives flip signs).
- **Cue**: _“maximum product subarray”_.
- **Trick**: Track both max and min product at each step.
- **Must-do**:
- [x] [LC 152 – Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)   Solution : ***[[LC 152. Maximum Product Subarray|Click here]]

### 4️⃣ Maximum Absolute Subarray Sum

- **Use case**: Max of |subarray sum|.
- **Cue**: _“absolute”_, _“positive or negative large sum”_.
- **Approach**: max(Kadane), max(-Kadane).
- **Must-do**: 
- [x] [LC 1749 – Maximum Absolute Sum of Any Subarray](https://leetcode.com/problems/maximum-absolute-sum-of-any-subarray/)   Solution : ***[[LC 1749. Maximum Absolute Sum of Any Subarray|Click here]]

### 5️⃣ Split Array (Partition + Kadane)

- **Use case**: Split into k subarrays minimizing largest sum.
- **Cue**: _“split array”_, _“largest sum among subarrays”_.
- **Approach**: Binary search + greedy (Kadane inspired).
- **Must-do**: 
- [ ] [LC 410 – Split Array Largest Sum](https://leetcode.com/problems/split-array-largest-sum/)


### 6️⃣ 2D Kadane

- **Use case**: Find maxsubarray sum for a matrix.
- **Cue**: _“max matrix sum”_, _“largest matrix with sum = k”_, "*Max matrix sum <= k".
- **Approach**: fix rows + compress columns + Kadane's on 1d compressed array(for each row height).
#### 🧩 Rule of thumb
- **If problem only wants the _maximum sum_** → plain Kadane works.
- **If problem wants the _maximum sum ≤ K_** (an upper bound) → plain Kadane fails → you need prefix sums + binary search / set.

- [x] [GFG - Maximum sum rectangle in a 2D matrix](https://www.geeksforgeeks.org/dsa/maximum-sum-rectangle-in-a-2d-matrix-dp-27/)    Solution : ***[[GFG Maximum sum Rectangle|Click here]]
- [x] [LC 363 – Max Sum of Rectangle No Larger Than K (2D Kadane)](https://leetcode.com/problems/max-sum-of-rectangle-no-larger-than-k/)    Solution : ***[[LC 363. Max Sum of Rectangle No Larger Than K|Click here]]
- [x] [GFG - Largest rectangular sub-matrix whose sum is 0](https://www.geeksforgeeks.org/dsa/largest-rectangular-sub-matrix-whose-sum-0/)     Solution : ***[[GFG Largest rectangular sub-matrix whose sum is 0|Click here]]

---

## 💼 Master List of Questions (All Variants)

- [x] [LC 53 – Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)
- [x] [LC 918 – Maximum Sum Circular Subarray](https://leetcode.com/problems/maximum-sum-circular-subarray/)
- [x] [LC 152 – Maximum Product Subarray](https://leetcode.com/problems/maximum-product-subarray/)
- [x] [LC 1749 – Maximum Absolute Sum of Any Subarray](https://leetcode.com/problems/maximum-absolute-sum-of-any-subarray/)
- [x] [LC 2321 - Maximum Score Of Spliced Array](https://leetcode.com/problems/maximum-score-of-spliced-array/)
- [x] [GFG - Maximum sum rectangle in a 2D matrix](https://www.geeksforgeeks.org/dsa/maximum-sum-rectangle-in-a-2d-matrix-dp-27/)
- [x] [LC 363 – Max Sum of Rectangle No Larger Than K (2D Kadane)](https://leetcode.com/problems/max-sum-of-rectangle-no-larger-than-k/)
- [x] [GFG - Largest rectangular sub-matrix whose sum is 0](https://www.geeksforgeeks.org/dsa/largest-rectangular-sub-matrix-whose-sum-0/)
- [ ] [LC 410 – Split Array Largest Sum](https://leetcode.com/problems/split-array-largest-sum/)    -binary search + greedy



---

## 🧠 Extra Insights

- Kadane is basically **1D DP on prefix sums**.
- For **2D problems (matrices)** → apply Kadane's on compressed rows.
- For **products** → track both max and min.
- Always clarify **“contiguous”** vs **“non-contiguous”** (they love this trick in interviews).
