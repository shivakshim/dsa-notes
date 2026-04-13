## 🌋 1. Core Concept - [[🔎PQ Deep-Dive]]

**Priority Queue (Heap)** = a data structure where elements are ordered by _priority_ (not insertion order).  
It only guarantees that:
> 👉 The top element (root) is always the smallest/largest (depending on type).

So:
- **Min-heap** → smallest element on top.
- **Max-heap** → largest element on top.
That’s it. The rest of the heap is _partially ordered_, not fully sorted.
##### ⚙️ BASIC OPERATIONS

| Operation               | Time     |
| ----------------------- | -------- |
| push / insert           | O(log N) |
| pop / removeTop         | O(log N) |
| top / peek              | O(1)     |
| build heap from N items | O(N)     |
### 💡Heap & CBT
We use an array (not an actual tree).  
We _pretend_ it’s a CBT to make math for parent/child relations easy.  
The **CBT property** ensures it’s balanced → `O(log n)` operations.  The **heap-order    property** ensures we always know the top priority element.


---
### 🧩 CODE TEMPLATE (GENERIC)

```cpp
// TOP-K Pattern Template
priority_queue<int, vector<int>, greater<int>> pq; // min-heap

for (int x : arr) {
    pq.push(x);
    if (pq.size() > K)
        pq.pop();
}
// pq now contains K largest elements (min-heap version)
return pq.top(); // Kth largest
```

### 🧰 Common Variations

#### → Max-heap version:
```cpp
priority_queue<int> pq; // default max-heap
for (int x : arr) {
    pq.push(x);
    if (pq.size() > K)
        pq.pop();
}
return pq.top(); // Kth smallest
```

#### → Custom comparator:
```cpp
auto cmp = [&](auto &a, auto &b) { return a.second > b.second; };
priority_queue<pair<int,int>, vector<pair<int,int>>, decltype(cmp)> pq(cmp);
```


---
### 🔑 Quick-Identity cues

|Problem Phrase|Heap Type|Pattern|
|---|---|---|
|“top K”|min-heap|Top K Elements|
|“Kth largest/smallest”|min/max|Top K|
|“most frequent”|min-heap|Frequency Sort|
|“K sorted arrays/lists”|min-heap|Merge K|
|“matrix sorted row/col”|min-heap|Kth in Matrix|
|“data stream median”|two-heap|Median Pattern|
|“sliding window K”|dual heap or deque|Sliding Window|
|“K pairs smallest sum”|min-heap|K Pairs|
Basically, **anywhere you need partial sorting or ranked extraction** = PQ candidate.


---

## 🧱 Misses and Edge Cases
| Case                  | Fix                                        |
| --------------------- | ------------------------------------------ |
| K > N                 | Return all elements                        |
| Empty input           | Return []                                  |
| Duplicates            | Handle with freq map or tie-breaker        |
| Negative numbers      | Works fine unless absolute values involved |
| Custom sorting needed | Use comparator carefully                   |
| Large input (10⁵+)    | Avoid sorting; use heap (O(N log K))       |

### 💣 COMMON MISTAKES / TRAPS

- ❌ Using **max-heap** when problem expects min (and vice versa).
- ❌ Forgetting to `pop()` when heap size > K → leads to O(N log N).
- ❌ Not considering **ties** (like same frequency or distance).
- ❌ Forgetting to use **abs()** for distance-based problems.
- ❌ Assuming heap is fully sorted — it’s _partially sorted_.
- ❌ Forgetting to rebalance heaps in stream problems.


---

## ⚙️ Priority Queue / Top K Elements — CATEGORIES + VARIANTS

#### 1️⃣ Basic Top-K / Heap Fundamentals  
Use case: Find kth largest/smallest, top K frequent items, sort streams, etc.  
Cue: “Top K”, “Kth largest”, “frequency”, “stream”, “continuous median”.  

✅ Must-Do  
- [x] [LC 215 – Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)
- [x] [LC 347 – Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)          💡 ***[[LC 347. Top K Frequent Elements|Solution]]
- [x] [LC 973 – K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/)         💡 ***[[LC 973. K Closest Points to Origin|Solution]]
- [x] [LC 1046 – Last Stone Weight](https://leetcode.com/problems/last-stone-weight/)                   💡 ***[[LC 1046. Last Stone Weight|Solution]]
- [x] [LC 295 – Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/) 💡 ***[[LC 295. Find Median from Data Stream|Solution]]
- [x] [LC 414 – Third Maximum Number](https://leetcode.com/problems/third-maximum-number/)           💡[[DSA PATTERNS GUIDE/All DSA Patterns/Priority Queue/LC 414. Third Maximum Number|Solution]]

⚪ Optional  
- [ ] [LC 703 – Kth Largest in a Stream](https://leetcode.com/problems/kth-largest-element-in-a-stream/)  
- [x] [LC 658 – Find K Closest Elements](https://leetcode.com/problems/find-k-closest-elements/)             💡[[LC 658. K closest elements|Solution]]


#### 2️⃣ Interval + PQ Combo (Scheduling / Meeting Room Type) 
🧠Core Idea : PQ = “live” intervals → every element = an active meeting/trip/task  
Max PQ size = max overlap = answer (rooms, cars, servers, etc.)
↗️Steps : Sort on start, min_heap on end, pop the non overlapping intervals.

🔎These can be divided into 2 parts :      1. Classic interval problems (meeting rooms) 
								 2. Dynamic / explicit interval problems ( task scheduler)
Use case: Allocate resources (like meeting rooms or CPU cores).  
Cue: “Intervals”, “rooms”, “min number of resources”, “finish time”.  

✅ Must-Do  
- [x] [LC 253 – Meeting Rooms II](https://leetcode.com/problems/meeting-rooms-ii/)
- [x] [LC 1094 – Car Pooling](https://leetcode.com/problems/car-pooling/)                               💡 ***[[LC 1094. Car Pooling|Solution]]
- [x] [LC 621 – Task Scheduler](https://leetcode.com/problems/task-scheduler/)                            💡 ***[[LC 621. Task Scheduler|Solution]]

⚪ Optional  
- [x] [LC 502 – IPO](https://leetcode.com/problems/ipo/)                                              💡 ***[[LC 502. IPO|Solution]]
- [ ] [LC 630 – Course Schedule III](https://leetcode.com/problems/course-schedule-iii/)  


#### 3️⃣ Merge / Stream-Based Problems  
🧠Core Concept :
- When we need to merge/ find kth element of MERGED sorted list, and we are already given sorted lists, we don't need to push all the elements in the pq to get the elements back in sorted ordered.
- We can simply push as needed, because since the lists are sorted, the range of selection of which elements go next is limited. Which helps us keep pq of size k (no. of lists) and only 1 loop (!pq.empty()), since we are not blindly traversing though each element.
Use case: Combine multiple sorted lists/arrays efficiently.  
Cue: “Merge K lists/arrays”, “k-way merge”, “stream processing”.  

✅ Must-Do  
- [x] [LC 23 – Merge K Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)                     💡 ***[[LC 23. Merge k Sorted Lists|Solution]]
- [x] [LC 378 – Kth Smallest Element in a Sorted Matrix](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)    Similar to [[LC 23. Merge k Sorted Lists]]
- [ ] [LC 373 – Find K Pairs with Smallest Sums](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/)  💀

⚪ Optional  
- [ ] [LC 632 – Smallest Range Covering Elements from K Lists](https://leetcode.com/problems/smallest-range-covering-elements-from-k-lists/)  


#### 4️⃣ Greedy / Selection Using PQ  
Use case: Pick elements dynamically based on cost, ratio, or reward.  
Cue: “Max profit”, “min cost”, “combine sticks”, “cheapest cost”.  

✅ Must-Do  
- [ ] [LC 1167 – Minimum Cost to Connect Sticks](https://leetcode.com/problems/minimum-cost-to-connect-sticks/)  
- [ ] [LC 373 – K Pairs with Smallest Sums](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/)  

⚪ Optional  
- [ ] [LC 1642 – Furthest Building You Can Reach](https://leetcode.com/problems/furthest-building-you-can-reach/)  
- [x] [LC 502 – IPO](https://leetcode.com/problems/ipo/)                                              💡 ***[[LC 502. IPO|Solution]]


#### 5️⃣ Frequency / Reordering Problems (PQ + HashMap hybrid) 
[[🧩 Task Scheduler vs Interval Overlap]]
Use case: Rearrange or encode sequences based on frequency, spacing, or order.  
Cue: “Reorganize string”, “schedule tasks”, “rearrange”, “no adjacent duplicates”.  

✅ Must-Do  
- [x] [LC 621 – Task Scheduler](https://leetcode.com/problems/task-scheduler/)                             💡 ***[[LC 621. Task Scheduler|Solution]]
- [x] [LC 767 – Reorganize String](https://leetcode.com/problems/reorganize-string/)                        💡Same as task scheduler
- [x] [LC 451 – Sort Characters By Frequency](https://leetcode.com/problems/sort-characters-by-frequency/)     💡map + maxheap

⚪ Optional  
- [x] [LC 358 – Rearrange String k Distance Apart](https://leetcode.com/problems/rearrange-string-k-distance-apart/)    ->  exactly like task scheduler

---

### 🏆 THE PQ 7-PROBLEM MASTERY KIT

- [x] [LC 215 – Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/)
- [x] [LC 347 – Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
- [x] [LC 23 – Merge K Sorted Lists](https://leetcode.com/problems/merge-k-sorted-lists/)
- [x] [LC 253 – Meeting Rooms II](https://leetcode.com/problems/meeting-rooms-ii/)
- [x] [LC 621 – Task Scheduler](https://leetcode.com/problems/task-scheduler/)  
- [x] [LC 295 – Find Median from Data Stream](https://leetcode.com/problems/find-median-from-data-stream/)
- [x] [LC 502 – IPO](https://leetcode.com/problems/ipo/)

### 💪 Remaining Must-Do Problems  
- [x] [LC 973 – K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/)
- [x] [LC 373 – Find K Pairs with Smallest Sums](https://leetcode.com/problems/find-k-pairs-with-smallest-sums/)  
- [x] [LC 1167 – Minimum Cost to Connect Sticks](https://leetcode.com/problems/minimum-cost-to-connect-sticks/)  
- [x] [LC 767 – Reorganize String](https://leetcode.com/problems/reorganize-string/)
- [x] [LC 451 – Sort Characters by Frequency](https://leetcode.com/problems/sort-characters-by-frequency/)

### 🌀 Optional / Advanced (do if aiming Deep Dives / Competitive Edge)  
- [ ] [LC 632 – Smallest Range Covering K Lists](https://leetcode.com/problems/smallest-range-covering-elements-from-k-lists/)  
- [ ] [LC 630 – Course Schedule III](https://leetcode.com/problems/course-schedule-iii/)  
- [ ] [LC 1642 – Furthest Building You Can Reach](https://leetcode.com/problems/furthest-building-you-can-reach/)  
- [x] [LC 358 – Rearrange String k Distance Apart](https://leetcode.com/problems/rearrange-string-k-distance-apart/)
- [x] [LC 658 – Find K Closest Elements](https://leetcode.com/problems/find-k-closest-elements/)
