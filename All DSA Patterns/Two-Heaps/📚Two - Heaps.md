
## 🌟 **Core Pattern Idea**

> “Keep two heaps — one for the smaller half (max-heap), and one for the larger half (min-heap) — so that you can always grab medians or balance streaming data _on the fly_.”

It’s literally like splitting your numbers into two perfectly balanced squads:

- 🧊 **Left Heap (Max-Heap):** Holds the _smaller half_
- 🔥 **Right Heap (Min-Heap):** Holds the _larger half_

Balance = the power. The sizes differ by at most 1.

---

#### 🏁 **Mental Tagline**

> **“Balance the halves, peek for median.”**  
> That’s Two Heaps in one smooth mantra 😌

---

## 🧠 **Recognition Cues**

💬 If the problem says stuff like:

- “find median from a data stream”
- “running median”, “continuous median”, “sliding median”
- “maximize/minimize after balancing two sides”
- “split around median or pivot dynamically”

→ 🚨 **That’s your Two Heaps pattern.**

---

## 🧩 **Algorithm Intuition**

1. Use **two heaps**:
    - **Max-Heap (lowHalf)** → keeps track of smaller numbers
    - **Min-Heap (highHalf)** → keeps track of larger numbers
2. Balance the two heaps so that:  
    `abs(size(lowHalf) - size(highHalf)) <= 1`
3. Depending on the operation:
    - To get **median**:
        - If equal size → `(top(lowHalf) + top(highHalf)) / 2.0`
        - Else → top of the bigger heap
    - To get **kth largest**, tweak heap size logic accordingly.
4. For **insertion**, decide which heap the new number belongs to based on current tops, then rebalance.

---

## 🧰 **C++ Code Template — Running Median**

```cpp
class MedianFinder {
    priority_queue<int> left; // max-heap
    priority_queue<int, vector<int>, greater<int>> right; // min-heap

public:
    void addNum(int num) {
        // Step 1: Insert
        if (left.empty() || num <= left.top()) left.push(num);
        else right.push(num);

        // Step 2: Balance heaps
        if (left.size() > right.size() + 1) {
            right.push(left.top());
            left.pop();
        } else if (right.size() > left.size()) {
            left.push(right.top());
            right.pop();
        }
    }

    double findMedian() {
        if (left.size() == right.size())
            return (left.top() + right.top()) / 2.0;
        return left.top();
    }
}
```

---

### ⚙️ **Time & Space Complexity**

|Operation|Complexity|
|---|---|
|Insert|O(log n)|
|Find median|O(1)|
|**Total (for n inserts)**|**O(n log n)**|
|Space|O(n)|

---

## 🧭 **When NOT to Use Two Heaps**

If:
- Data is _static_ and you just need one-time median → ❌ use sorting (O(n log n))
- You need top-_k_ elements but not running median → use one heap (Min or Max)
- Problem doesn’t need **balancing halves** → probably not Two Heaps.

---

## ⚖️ **TWO HEAPS — Pattern Variants + Must-Do Problems**

### **Variant 1: Running Median / Median from Stream**

📘 **Concept:** Add numbers dynamically, get median anytime.  
🧠 Recognition cues: “running median”, “data stream median”, “find median on the fly”  
✅ **Must-do:**
- [x] [**LC 295 – Find Median from Data Stream**](https://leetcode.com/problems/find-median-from-data-stream/) 🔥                [[LC 295. Find Median from Data Stream|💡]]

### **Variant 2: Sliding Window Median**

📘 **Concept:** Move a window over stream → median of each window.  
🧠 Recognition cues: “sliding window”, “median for every window of size k”  
✅ **Must-do:**
- [ ] [**LC 480 – Sliding Window Median**](https://leetcode.com/problems/sliding-window-median/) 💣  
  (same two-heaps idea + remove from heaps carefully)

### **Variant 3: IPO / Capital Maximization**

📘 **Concept:** Use two heaps — one sorted by profit, one by capital — to greedily pick projects within constraints.  
🧠 Recognition cues: “maximize capital”, “choose projects”, “profit vs cost tradeoff”  
✅ **Must-do:**
- [x]  [**LC 502 – IPO**](https://leetcode.com/problems/ipo/) ⚡ _(Two Heaps + Greedy)_
same as 1 heap, just the sorting of capital in asc order will be done by minheap.

### **Variant 4: Continuous Percentile / Stream Quantile**

📘 **Concept:** Generalize median (50th percentile) to any percentile — maintain two heaps with dynamic ratio.  
🧠 Recognition cues: “stream percentile”, “live percentile computation”  
✅ **Must-practice:**
-  Custom implementation — design-style question variant of 295

---

# 💼 Two Heaps Pattern Must-Do Set

## 🧠 Core Coding Problems
- [x] [LC 295 – Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/)
- [ ] [LC 480 – Sliding Window Median](https://leetcode.com/problems/sliding-window-median/)
- [x] [LC 502 – IPO](https://leetcode.com/problems/ipo/)

## 🧩 Advanced / Design-Style Variants
- [ ] Continuous Median (custom variant of LC 295) — stream of numbers, maintain median dynamically using two balanced heaps.
- [ ] Online Percentile Finder (design variant) — generalize median logic to compute any percentile (e.g., 90th percentile) using two heaps.
