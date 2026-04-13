
## 🧠 What is Prefix Sum?

Prefix Sum is a technique to **precompute cumulative sums** so that **range sum queries (i to j)** can be answered in constant time.
-We pre-create a Prefix array whose i stores the sum till i'th element of array.

- `prefix[i] = sum of array[0...i]`

- For **range [L, R]**:  
  `sum = prefix[R] - prefix[L-1]` (handle L = 0 separately!)
   -for L=0 → Just return `prefix[R]`
   
- ⚡**Note : When asked to find length of subarray in prefix sum problems,**
	 💡*length = right - left    i.e.  length =  i - prefixmap[presum-k]* , because :
> At left, we don’t store “from left,” we store “ahead of left” (the prefix sum before left). That’s why no `+1` is needed later.

---
## ⚙️ How to Build It

```cpp
  int prefix[n];  //prefix size = n
  prefix[0] = ar[0]; //initializing first element
  for (int i = 1; i < n; i++) {
    prefix[i] = prefix[i - 1] + ar[i];  //populate prefix
  }
```

```java
int[] prefix = new int[n];
prefix[0] = arr[0];
for (int i = 1; i < n; i++) {
    prefix[i] = prefix[i - 1] + arr[i];
}
```

> For **mutable arrays**, use Segment Trees(Fenwick) or Binary Indexed Trees instead.

---
#### 🔍 Keywords in Questions

- “Sum of subarrays”
- “Find number of subarrays with sum K/divisible by K”
- “Range sum from i to j multiple times”
- “Find total of all i to j”
- “Sliding window sum but non-fixed size”
- “Preprocess the array for fast queries”

---
#### 🚫 Common Mistakes

- Forgetting to handle `L = 0`
- Confusing prefix sum with sliding window
- Using prefix sum directly to count subarrays (need a map!)
- Integer overflow (use `long` if needed)
- Off-by-one errors in 2D prefix sum

---
#### 📍 Edge Cases

- All elements = 0 → multiple valid subarrays
- Negative numbers present → sliding window fails, prefix works
- Query from 0 to R? → Just return `prefix[R]`
- initialize map for 0 condition.

---
#### 🤯 Advanced Tricks

- **Modulo prefix sum** → `sum % k` (great for divisible subarrays)
- **Prefix XOR** → `xor[L...R] = prefix[R] ^ prefix[L-1]`

---
#### 🧼 Final TL;DR

If the question screams:
- "Multiple queries for range sums"
- "Count subarrays with sum / divisible by k"
- "Cumulative info from left to right"
**📢 Think: PREFIX SUM!**

---
## 📊 Prefix Sum Master Sheet - Imp Variations

#### 1. Basic 1D Prefix Sum : 
**Idea:** Precompute cumulative sums to answer range sum queries in O(1).
**Recognition Cues:**
- Multiple queries asking sum in a subarray.
- "Sum from i to j" repeatedly.
- Precomputation is allowed.

**Must-Do Qs:**
- [x] [LeetCode 303 – Range Sum Query Immutable](https://leetcode.com/problems/range-sum-query-immutable/)
- [x] [LeetCode 724 – Find Pivot Index](https://leetcode.com/problems/find-pivot-index/)

#### 2. Prefix Sum + HashMap (Subarray Sum Problems) : 
**Idea:** Track frequencies of prefix sums to detect subarrays with a certain sum.
**Note** : Always initialize map for sum = k by mp[0]=1;
**Recognition Cues:**
- "Count subarrays" or "Find subarray with sum = K".
- Works with negatives (sliding window fails here).
- Need O(n) solution.

**Must-Do Qs:**
- [x] [LeetCode 560 – Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)
- [x] [Leetcode 325 - Maximum Size Subarray Sum = k](https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/description/)
- [x] [LeetCode 1248 – Count Number of Nice Subarrays](https://leetcode.com/problems/count-number-of-nice-subarrays/)
- [x] [LeetCode 974 – Subarray Sums Divisible by K](https://leetcode.com/problems/subarray-sums-divisible-by-k/)
- [x] [LeetCode 525 - Contiguous Array](https://leetcode.com/problems/contiguous-array/)

#### 3. Prefix Sum with Modulo / Remainder Trick : 
**Idea:** Store prefixSum % k in map to find divisible sum subarrays.
**Note** : Always initialize map for rem = 0;
**Recognition Cues:**
- "Divisible by K" or "Modulo K".
- Avoids overflow in large sums.

**Must-Do Qs:**
- [x] [LeetCode 974 – Subarray Sums Divisible by K](https://leetcode.com/problems/subarray-sums-divisible-by-k/)
- [x] [LeetCode 523 – Continuous Subarray Sum](https://leetcode.com/problems/continuous-subarray-sum/)

#### 4. Prefix XOR : [[👾Prefix XOR Crash-course| XOR Crash-course]]
**Idea:** Same as prefix sum but with XOR instead of +.
**Recognition Cues:**
- XOR instead of sum.
- Properties: `a ^ a = 0`, `a ^ 0 = a`.
- Subarray XOR = prefixXor[j] ^ prefixXor[i-1].

**Must-Do Qs:**
- [x] [LeetCode 1442 – Count Triplets That Can Form Two Arrays of Equal XOR](https://leetcode.com/problems/count-triplets-that-can-form-two-arrays-of-equal-xor/)
- [x] [LeetCode 1310 – XOR Queries of a Subarray](https://leetcode.com/problems/xor-queries-of-a-subarray/)

#### 5. 2D Prefix Sum : 
**Idea:** Precompute sums for 2D matrix to answer submatrix sum queries fast.
**Recognition Cues:**
- Matrix sum queries.
- "Sum of rectangle from (r1,c1) to (r2,c2)".

**Must-Do Qs:**
- [x] [LeetCode 304 – Range Sum Query 2D Immutable](https://leetcode.com/problems/range-sum-query-2d-immutable/)
- [x] [LeetCode 1314 – Matrix Block Sum](https://leetcode.com/problems/matrix-block-sum/)

#### 6. Difference Array (Prefix Sum Inverse) : 
**Idea:** Use difference array for range updates, then prefix sum to get final array.
**Recognition Cues:**
- Multiple range updates.
- O(1) update, O(n) finalize.

**Must-Do Qs:**
- [x] [LeetCode 370 – Range Addition](https://leetcode.com/problems/range-addition/)    Solution: [[370. Range Addition|Click here]]
- [x] [LeetCode 1094 – Car Pooling](https://leetcode.com/problems/car-pooling/)   Solution : [[1094. Car Pooling|Click here]]
- [x] [LeetCode 2536 – Increment Submatrices by 1](https://leetcode.com/problems/increment-submatrices-by-one/)   Solution : [[2536. Increment Submatrices by One|Click here]]

## 💡 Tips:
- Always initialize map with `{0: 1}` for subarray count problems.
- Works with negatives; sliding window does not.
- For mod problems, handle negative mods with `(x % k + k) % k`.

#### ✅IMP Questions -[[DSA PATTERNS GUIDE/All DSA Patterns/Prefix Sum/📑Problem Set|📑Problem Set]]


