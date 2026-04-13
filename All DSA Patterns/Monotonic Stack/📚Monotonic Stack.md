## 📌 Core Pattern - Monotonic Stack / Queue

Find the **next greater/smaller elements or sliding window max/min** using a **stack or deque** that maintains elements in monotone order.  
Linear-time (O(n)) solution using **stack/deque + smart popping**.

When scanning the array:  
1. Maintain a **monotone stack/deque** (increasing or decreasing).  
2. For each element:
    - Pop elements from stack/deque that **break monotonicity**.  
    - Compute needed result (next greater, width, max/min in window).  
    - Push current element (or index) onto stack/deque.  
3. Optional: handle **wrap-around or sliding window** with circular or deque logic.

| Pattern              | Stack Order (bottom→top) | Top holds | Pop condition      |
| -------------------- | ------------------------ | --------- | ------------------ |
| Next Greater Element | Decreasing               | Smallest  | while (top < curr) |
| Next Smaller Element | Increasing               | Largest   | while (top > curr) |

---

## 🎯 Cue (When to Apply)

- “Next greater/smaller element”, “nearest larger/smaller”  
- “Largest rectangle in histogram”, “maximal rectangle”  
- “Sliding window max/min”  
- Array or string problems needing **range influence, span, or limits**  
- Phrases like:  
    - “next”, “previous”, “span”, “width of influence”  
    - “sliding window maximum/minimum”  
    - “circular array / histogram / stock span”

---

## ⚙️ Template (Next Greater Element / Single Pass)

```cpp
vector<int> nextGreater(vector<int>& nums) {
    int n = nums.size();
    vector<int> ans(n, -1);
    stack<int> st; // store indices
    for (int i = 0; i < n; i++) {
        while (!st.empty() && nums[i] > nums[st.top()]) {
            ans[st.top()] = nums[i];
            st.pop();
        }
        st.push(i);
    }
    return ans;
}```

- Note :  For next smaller element simply change the > to < in the while.

## ⚠️ Misses / Edge Cases

- Circular arrays → may need modulo trick
- Stack stores **index** for ranges; storing value alone often breaks width calculations
- For sliding window, always **remove out-of-window indices**
- Watch monotone direction: increasing vs decreasing depending on problem

---

## 🔀 Variants & Must-Do Questions

### 1️⃣ Next Greater / Smaller Element

- **Use case**: Find nearest larger/smaller value on left/right.
- **Cue**: “Next greater element”, “temperature trend”, “stock span”.
- **Must-do**:
- [x] [LC 739 – Daily Temperatures](https://leetcode.com/problems/daily-temperatures/)
- [x] [LC 503 – Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/)    Solution : ***[[LC 503. Next Greater Element II|Click here]]
- [x] [LC 496 – Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)     Solution : ***[[LC 502. Next Greater Element I|Click here]]
- [x] [GFG – Next Smaller Element](https://www.geeksforgeeks.org/problems/immediate-smaller-element1142/1)

---

### 2️⃣ Range Influence / Largest Rectangle

- **Use case**: Find max area under histogram / width of influence.
- **Cue**: “Largest rectangle”, “maximal rectangle”, “width span”.
- **Must-do**:
- [x] [LC 84 – Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)    Solution : ***[[LC 84. Largest Rectangle in Histogram|Click here]]
- [x] [LC 85 – Maximal Rectangle](https://leetcode.com/problems/maximal-rectangle/)    Solution : ***[[LC 85. Maximal Rectangle|Click here]]
- [x] [LC 907 – Sum of Subarray Minimums](https://leetcode.com/problems/sum-of-subarray-minimums/)     Solution : ***[[LC 907. Sum of Subarray Minimums|Click here]]

---

### 3️⃣ Sliding Window Maximum / Minimum (Monotonic Queue)

- **Use case**: Max/min in every window of size k.
- **Cue**: “Sliding window maximum/minimum”.
- **Must-do**:
- [x] [LC 239 – Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)    Solution : ***[[LC 239. Sliding Window Maximum|Click here]]
- [x] [LC 862 – Shortest Subarray with Sum at Least K](https://leetcode.com/problems/shortest-subarray-with-sum-at-least-k/) ☠️   Solution : ***[[LC 862. Shortest Subarray with Sum at Least K|Click here]]
- [x] [LC 325 – Maximum Size Subarray Sum Equals k](https://www.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/1?utm_source=chatgpt.com) *(Premium)*    Solution : ***[[LC 325. Longest Subarray with Sum K|Click here]]


---

### 4️⃣ Custom / Condition-Based Monotonic

- **Use case**: Stock span, sums with conditions, constrained windows.
- **Cue**: Mentions “span”, “threshold sum”, or conditions on ranges.
- **Must-do**:
- [x] [LC 862 – Shortest Subarray with Sum at Least K](https://leetcode.com/problems/shortest-subarray-with-sum-at-least-k/)
- [x] [LC 901 – Online Stock Span](https://leetcode.com/problems/online-stock-span/)
- [x] [LC 42 – Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)     Solution : ***[[LC 42. Trapping Rain Water - Monotonic stack|Click here]]
- [x] [LC 456 – 132 Pattern](https://leetcode.com/problems/132-pattern/)    Solution : ***[[LC 456. 132 Pattern|Click here]]

---

## 💼 Master List of Questions (All Variants)

- [x] [LC 739 – Daily Temperatures](https://leetcode.com/problems/daily-temperatures/)
- [x] [LC 503 – Next Greater Element II](https://leetcode.com/problems/next-greater-element-ii/)
- [x] [LC 496 – Next Greater Element I](https://leetcode.com/problems/next-greater-element-i/)
- [x] [GFG – Next Smaller Element](https://www.geeksforgeeks.org/problems/immediate-smaller-element1142/1)
- [x] [LC 84 – Largest Rectangle in Histogram](https://leetcode.com/problems/largest-rectangle-in-histogram/)
- [x] [LC 85 – Maximal Rectangle](https://leetcode.com/problems/maximal-rectangle/)
- [x] [LC 907 – Sum of Subarray Minimums](https://leetcode.com/problems/sum-of-subarray-minimums/)
- [x] [LC 239 – Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)
- [x] [LC 862 – Shortest Subarray with Sum at Least K](https://leetcode.com/problems/shortest-subarray-with-sum-at-least-k/)
- [x] [LC 325 – Maximum Size Subarray Sum Equals k](https://leetcode.com/problems/maximum-size-subarray-sum-equals-k/) *(Premium)*
- [x] [LC 901 – Online Stock Span](https://leetcode.com/problems/online-stock-span/)
- [x] [LC 42 – Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/)
- [x] [LC 456 – 132 Pattern](https://leetcode.com/problems/132-pattern/)

####  Optional / Bonus (4 Questions) ([[📚 Greedy Algorithm]]+[[📚Monotonic Stack]])
 High-yield remixes or numeric/string edge-case variants.

- [x] [LC 316 – Remove Duplicate Letters](https://leetcode.com/problems/remove-duplicate-letters/)
- [ ] [LC 321 – Create Maximum Number](https://leetcode.com/problems/create-maximum-number/)
- [x] [LC 402 – Remove K Digits](https://leetcode.com/problems/remove-k-digits/)
- [ ] [LC 581 – Shortest Unsorted Continuous Subarray](https://leetcode.com/problems/shortest-unsorted-continuous-subarray/)
