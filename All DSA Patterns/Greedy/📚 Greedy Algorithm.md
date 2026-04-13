## 📌 Core Pattern – Greedy Algorithm

Greedy = **make the best local choice** at every step → hope it leads to the global optimum 💰  
You don’t backtrack or explore; just **grab what looks best right now** (but with brains).  

💡 Think: **sort, choose, repeat.**

When scanning or processing data:

1. Sort or organize data by some key (end time, value, ratio, etc.)
2. Pick elements based on a **greedy condition** (max gain, min cost, earliest finish).
3. Maintain feasibility (capacity, overlap, constraints).
4. Stop when constraints break — you’re done.

## 🎯 Cue (When to Apply)

- “Maximize / minimize something” (profit, cost, meetings, etc.)
- “Choose optimal subset” or “schedule non-overlapping events”
- “Select tasks/jobs/meetings” or “minimum resources”
- “Minimize coins / refueling / arrows / platforms”
- “Local decision feels obvious — pick the best at each step”

## ⚙️ Template (Typical Greedy + Sorting)

```cpp
// Example: Activity Selection / Non-overlapping Intervals
int maxMeetings(vector<int>& start, vector<int>& end) {
    vector<pair<int,int>> intervals;
    for (int i = 0; i < start.size(); i++) intervals.push_back({end[i], start[i]});
    sort(intervals.begin(), intervals.end());
    int count = 0, lastEnd = -1;
    for (auto [e, s] : intervals) {
        if (s > lastEnd) {
            count++;
            lastEnd = e;
        }
    }
    return count;
}
```

🧠 **Tip:** Greedy is all about _sorting + smart picking_.  
If you can’t define a clear greedy choice → it’s probably DP, not greedy 😏

## ⚠️ Misses / Edge Cases

- Greedy doesn’t always give global optimum → verify with “exchange argument” logic
- Overlaps, constraints, or cumulative limits can break pure greedy
- Sorting order is everything — one wrong comparator and your result’s cooked
- Some require heap/PQ for dynamic greedy (like ropes, tasks, workers)

---

## 🔀 Variants & Must-Do Questions

### 1️⃣ Interval Scheduling / Selection  - [[💡Sorting Logic Cheatsheet]]
**Use case:** Select max non-overlapping intervals or minimum arrows to burst all balloons.  
**Cue:** “Non-overlapping intervals”, “minimum arrows”, “maximum meetings”.

- [x] [LC 435 – Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)                                   Solution : ***[[LC 435. Non-overlapping Intervals|Click here]]
- [x] [LC 452 – Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/)   Solution : ***[[LC 452. Minimum Number of Arrows to Burst Balloons|Click here]]
- [x] [GFG – N Meetings in One Room](https://www.geeksforgeeks.org/problems/n-meetings-in-one-room-1587115620/1)                                        Solution : ***[[GFG. N Meetings in a room|Click here]]

**Optional**
- [x] [LC 56 – Merge Intervals](https://leetcode.com/problems/merge-intervals/) *(Optional)*


### 2️⃣ Ratio / Value-Based Selection (Classic Greedy)  
**Use case:** Pick max profit/value given limited capacity or constraints.  
**Cue:** “Knapsack”, “maximum units”, “minimum coins”, “maximize ratio”.

- [x] [GFG – Fractional Knapsack](https://www.geeksforgeeks.org/problems/fractional-knapsack-1587115620/1)   
- [x] [GFG – Job Sequencing Problem](https://www.geeksforgeeks.org/problems/job-sequencing-problem-1587115620/1)      Solution : ***[[GFG Job Sequencing Problem|Click here]]

**Optional**
- [ ] [LC 630 – Course Schedule III](https://leetcode.com/problems/course-schedule-iii/) *(Optional / Advanced)*
- [ ] [GFG – Minimum Number of Coins](https://www.geeksforgeeks.org/problems/number-of-coins1824/1) *(Optional)*


### 3️⃣ Heap / PQ-based Greedy  
**Use case:** Combine or pick minimal elements repeatedly to minimize total cost.  
**Cue:** “Minimum cost”, “connect ropes”, “combine elements”, “encode”.

lc 502 - ipo
- [ ] [GFG – Connect Ropes to Minimize Cost](https://www.geeksforgeeks.org/problems/minimum-cost-of-ropes-1587115620/1)
- [ ] [GFG – Huffman Encoding](https://www.geeksforgeeks.org/problems/huffman-encoding3345/1)
- [ ] [LC 621 – Task Scheduler](https://leetcode.com/problems/task-scheduler/)

**Optional**
- [ ] [LC 857 – Minimum Cost to Hire K Workers](https://leetcode.com/problems/minimum-cost-to-hire-k-workers/) *(Optional)*
- [ ] [LC 871 – Minimum Number of Refueling Stops](https://leetcode.com/problems/minimum-number-of-refueling-stops/) *(Optional)*


### 4️⃣ Sorting + Decision (Simple Greedy)  
**Use case:** Sort and match / assign efficiently to maximize output or minimize cost.  
**Cue:** “Assign”, “distribute”, “minimum difference”, “boats”, “cookies”.

- [x] [LC 455 – Assign Cookies](https://leetcode.com/problems/assign-cookies/)
- [x] [LC 135 – Candy](https://leetcode.com/problems/candy/)    Solution : ***[[LC 135. Candy|Click here]]

**Optional**
- [ ] lemonade change
- [x] [LC 881 – Boats to Save People](https://leetcode.com/problems/boats-to-save-people/) *(Optional)*


### 5️⃣ Greedy Traversal / Path Optimization  
**Use case:** Find optimal stopping points or minimal jumps using local choices.  
**Cue:** “Minimum jumps”, “gas station”, “refueling”, “coverage”.

- [x] [LC 55 - Jump Gam](https://leetcode.com/problems/jump-game/)      Solution : ***[[LC 55. Jump Game|Click here]]
- [x] [LC 45 – Jump Game II](https://leetcode.com/problems/jump-game-ii/)     Solution : ***[[LC 45. Jump Game II|Click here]]
- [x] [LC 134 – Gas Station](https://leetcode.com/problems/gas-station/)     Solution : ***[[LC 134. Gas Station|Click here]]


### 6️⃣ String / Lexicographical Greedy  
**Use case:** Remove/reorder to form smallest or largest lexicographic string.  
**Cue:** “Smallest string”, “remove k digits”, “reorganize string”, “duplicate letters”.

- [x] [LC 402 – Remove K Digits](https://leetcode.com/problems/remove-k-digits/)
- [x] [LC 316 – Remove Duplicate Letters](https://leetcode.com/problems/remove-duplicate-letters/) 

**Optional**
- [ ] [LC 321 – Create Maximum Number](https://leetcode.com/problems/create-maximum-number/) *(Advanced)*
- [ ] [LC 767 – Reorganize String](https://leetcode.com/problems/reorganize-string/) *(Optional)*


### 7️⃣ Time / Event Scheduling (Composite Greedy)  
**Use case:** Overlapping events, platforms, or time windows.  
**Cue:** “Minimum platforms”, “meeting rooms”, “merge times”.

- [x] [GFG – Minimum Number of Platforms](https://www.geeksforgeeks.org/problems/minimum-platforms-1587115620/1)

**Optional**
- [x] [LC 253 – Meeting Rooms II](https://leetcode.com/problems/meeting-rooms-ii/) *(Optional)*

---

## 💼 Master List of Must-Do Questions (15 Total)

- [x] [LC 435 – Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)
- [x] [LC 452 – Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/)
- [x] [GFG – N Meetings in One Room](https://www.geeksforgeeks.org/problems/n-meetings-in-one-room-1587115620/1)
- [x] [GFG – Fractional Knapsack](https://www.geeksforgeeks.org/problems/fractional-knapsack-1587115620/1)
- [x] [GFG – Job Sequencing Problem](https://www.geeksforgeeks.org/problems/job-sequencing-problem-1587115620/1)
- [ ] [GFG – Connect Ropes to Minimize Cost](https://www.geeksforgeeks.org/problems/minimum-cost-of-ropes-1587115620/1)
- [ ] [GFG – Huffman Encoding](https://www.geeksforgeeks.org/problems/huffman-encoding3345/1)
- [ ] [LC 621 – Task Scheduler](https://leetcode.com/problems/task-scheduler/)
- [ ] [LC 455 – Assign Cookies](https://leetcode.com/problems/assign-cookies/)
- [x] [LC 135 – Candy](https://leetcode.com/problems/candy/)
- [x] [LC 45 – Jump Game II](https://leetcode.com/problems/jump-game-ii/)
- [x] [LC 134 – Gas Station](https://leetcode.com/problems/gas-station/)
- [x] [LC 402 – Remove K Digits](https://leetcode.com/problems/remove-k-digits/)
- [x] [GFG – Minimum Number of Platforms](https://www.geeksforgeeks.org/problems/minimum-platforms-1587115620/1)
- [ ] [LC 871 – Minimum Number of Refueling Stops](https://leetcode.com/problems/minimum-number-of-refueling-stops/)

---

## 💎 Optional / Advanced Practice (9 Total)

- [ ] [LC 56 – Merge Intervals](https://leetcode.com/problems/merge-intervals/)
- [ ] [LC 630 – Course Schedule III](https://leetcode.com/problems/course-schedule-iii/)
- [ ] [GFG – Minimum Number of Coins](https://www.geeksforgeeks.org/problems/number-of-coins1824/1)
- [ ] [LC 857 – Minimum Cost to Hire K Workers](https://leetcode.com/problems/minimum-cost-to-hire-k-workers/)
- [x] [LC 881 – Boats to Save People](https://leetcode.com/problems/boats-to-save-people/)
- [x] [LC 316 – Remove Duplicate Letters](https://leetcode.com/problems/remove-duplicate-letters/)
- [ ] [LC 321 – Create Maximum Number](https://leetcode.com/problems/create-maximum-number/)
- [ ] [LC 767 – Reorganize String](https://leetcode.com/problems/reorganize-string/)
- [x] [LC 253 – Meeting Rooms II](https://leetcode.com/problems/meeting-rooms-ii/)
