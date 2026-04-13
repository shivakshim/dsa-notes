- [ ] [Maximum sum rectangle in a 2D matrix](https://www.geeksforgeeks.org/dsa/maximum-sum-rectangle-in-a-2d-matrix-dp-27/) 
- [ ] [Largest rectangular sub-matrix whose sum is 0](https://www.geeksforgeeks.org/dsa/largest-rectangular-sub-matrix-whose-sum-0/)  

- [ ] ### **Tier 1 – Core Kadane Variants (FAANG every time, must-do 4)**

1. LC 53 – **Maximum Subarray (Kadane OG)**
    
2. LC 918 – **Maximum Sum Circular Subarray**
    
3. LC 152 – **Maximum Product Subarray**
    
4. LC 560 – **Subarray Sum Equals K**
    

---

### **Tier 2 – Extended Musts (strong FAANG + MAANG, total = 10)**

5. LC 363 – **Max Sum of Rectangle ≤ K** (2D Kadane, Google/MS heavy)
    
6. LC 325 – **Maximum Size Subarray Sum = k** (variation of 560)
    
7. LC 862 – **Shortest Subarray with Sum ≥ K** (monotonic deque twist)
    
8. LC 974 – **Subarray Sums Divisible by K** (prefix hash, Amazon/Meta)
    
9. LC 523 – **Continuous Subarray Sum** (cycle logic, Netflix/Amazon)
    
10. LC 124 – **Binary Tree Max Path Sum** (tree version of Kadane, FAANG classic)
    

---

### **Tier 3 – Nice-to-Have / Sometimes Asked (rounds out to 14)**

11. LC 209 – **Minimum Size Subarray Sum** (sliding window alt)
    
12. LC 1590 – **Make Sum Divisible by P** (math + hashmap)
    
13. LC 918 alt → **min-subarray version** (just a twist but worth 1 min note)
    
14. Some **custom company twists** (like "max sum of subarray with at most M negatives" → Kadane + conditions).




---



## 🔥 Core Kadane Variations

1. **LC 53 – Maximum Subarray** (the OG Kadane)
    
    - Find max sum contiguous subarray.
        
    - **Most asked** (Amazon, Google, MS, FB, etc.)
        
2. **LC 918 – Maximum Sum Circular Subarray**
    
    - Like Kadane, but the array is circular.
        
    - Twist: either use normal Kadane or totalSum – minSubarray.
        
3. **LC 152 – Maximum Product Subarray**
    
    - Trick version: instead of sum, it’s product (need to track min + max).
        

---

## ⚡ Subarray With Constraints

4. **LC 209 – Minimum Size Subarray Sum**
    
    - Smallest length subarray with sum ≥ target. (Sliding window, but Kadane-flavored)
        
5. **LC 325 – Maximum Size Subarray Sum Equals k** (premium)
    
    - Find max length subarray whose sum = k (Kadane + hashmap).
        
6. **LC 560 – Subarray Sum Equals k**
    
    - Count subarrays with sum = k (prefix sums + hashmap).
        

---

## 🎭 Kadane + DP Mix

7. **LC 53 (follow-up)** – Reconstruct actual subarray.
    
    - FAANG interviewers often ask: “Not just the sum, print the subarray.”
        
8. **LC 918 (follow-up)** – Return the subarray, not just sum.
    
    - More implementation heavy.
        
9. **LC 363 – Max Sum of Rectangle No Larger Than K**
    
    - 2D Kadane → fix cols + apply 1D Kadane. Asked a lot at Google.
        
10. **LC 1749 – Maximum Absolute Sum of Any Subarray**
    

- Just max(Kadane, Kadane on -nums).
    

---

## 🌀 Advanced Kadane Variants

11. **LC 1191 – K-Concatenation Maximum Sum**
    

- Array repeated k times; must consider wrapping + mod.
    

12. **LC 2321 – Maximum Score of Spliced Array**
    

- Swap subarrays between two arrays → Kadane on difference.
    

13. **LC 238 – Product of Array Except Self**
    

- Similar flavor to max product subarray, though not exactly Kadane.
    

14. **LC 41 – First Missing Positive** (not Kadane, but often paired in FAANG rounds as array trick Q).