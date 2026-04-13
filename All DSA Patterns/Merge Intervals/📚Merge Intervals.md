  
## 🌟 **Core Pattern Idea**

> “Sort the intervals by start time, then **merge overlapping ones** by tracking a ‘current’ interval and extending it when the next interval overlaps.”

You’re basically cleaning up a messy calendar — combining overlapping meetings into one neat timeline.

#### 🏁 **Mental Tagline**

> **“Sort → Sweep → Merge → Push last.”**
That’s the entire Merge Intervals pattern in one breath. 🧘‍♀️

- For any 2 intervals [a1,a2], [b1,b2] they overlap only and only if 
```
max(a1, b1) <= min(a2, b2)
```

---

## 🧠 **Recognition Cues**

💬 If a problem says words like:

- “merge overlapping intervals”
- “combine”, “union”, “consolidate”
- “summarize calendar”, “merge schedules”, “free time after merging”
- “find non-overlapping intervals after merging”  
    → 🚨 **This is your Merge Intervals pattern.**

---

## 🧩 **Algorithm Intuition

1. Sort all intervals by their start time.
2. Take the first one as your “current merged interval.”
3. For each next interval:
    - If it **overlaps** (`next.start <= current.end`) → merge them:  
        `current.end = max(current.end, next.end)`
    - Else → push the current into result and start a new one.
4. At the end, don’t forget to push the last one.

---

## 🧰 **C++ Code Template**

```cpp
vector<vector<int>> merge(vector<vector<int>>& intervals) {
    if (intervals.empty()) return {};
    
    // Step 1: Sort intervals by start time
    sort(intervals.begin(), intervals.end());
    
    // Step 2: Prepare result
    vector<vector<int>> merged;
    merged.push_back(intervals[0]);
    
    // Step 3: Iterate through all intervals
    for (int i = 1; i < intervals.size(); i++) {
        if (intervals[i][0] <= merged.back()[1]) {
            // Overlap → merge them
            merged.back()[1] = max(merged.back()[1], intervals[i][1]);
        } else {
            // No overlap → push new interval
            merged.push_back(intervals[i]);
        }
    }
    
    return merged;
}
```

### ⚙️ **Time & Space Complexity**

|Operation|Complexity|
|---|---|
|Sorting|O(n log n)|
|Merge pass|O(n)|
|**Total**|**O(n log n)**|
|Space|O(n) (result storage)|

---

## 🧭 **When NOT to Use Merge Intervals**

If the question talks about:

- “Minimum number of removals to eliminate overlaps”
- “How many meeting rooms needed”
- “Find max non-overlapping intervals”  
    → ❌ That’s **Overlapping Intervals** : [[💡Merge Interval vs Overlapping Intervals]]


---


### 🧩 MERGE INTERVALS PATTERN — Variants + Their Must-Do Questions

### **Variant 1: Basic Merge (the OG)**

📘 **Concept:** Sort by start → merge overlaps.  
🧠 Recognition cues: _“merge”, “combine”, “union”, “consolidate intervals”_  
✅ **Must-do:**
- [x]  [**LC 56 – Merge Intervals**](https://leetcode.com/problems/merge-intervals/) 🔥 (The base template)

🪶 **Optional (practice):**
- [ ]  [**LC 1272 – Remove Interval**](https://leetcode.com/problems/remove-interval/) _(reverse operation of merging)_   

### **Variant 2: Insert and Merge**

📘 **Concept:** Given a new interval, insert it into the sorted list, and merge if it overlaps.  
🧠 Recognition cues: _“insert an interval”, “add new interval into existing schedule”_  
✅ **Must-do:**
- [x]  [**LC 57 – Insert Interval**](https://leetcode.com/problems/insert-interval/)                                    💡 [[LC 57. Insert Interval|Solution]]

### **Variant 3: Intersection (Two Lists)**

📘 **Concept:** Find overlapping parts (intersection) between two sets of intervals.  
🧠 Recognition cues: _“intersection”, “common time”, “mutual overlap”_  
✅ **Must-do:**
- [x]  [**LC 986 – Interval List Intersections**](https://leetcode.com/problems/interval-list-intersections/)                💡[[LC 986. Interval List Intersections|Solution]]

### **Variant 4: Multi-list Merge (Flatten + Merge)**

📘 **Concept:** Multiple people’s intervals → flatten → merge to get consolidated busy/free time.  
🧠 Recognition cues: _“employee schedules”, “common free time”, “merge all intervals across lists”_  
✅ **Must-do:**

- [x]  [**LC 759 – Employee Free Time**](https://leetcode.com/problems/employee-free-time/)                         💡[[LC 759. Employee Free Time|Solution]]

### **Variant 5: Two-person Scheduling / Find Overlap Slot**

📘 **Concept:** Given two people's intervals + duration, find earliest meeting slot.  
🧠 Recognition cues: _“meeting slot”, “duration”, “find earliest overlap”_  
✅ **Must-do:**

- [x]  [**LC 1229 – Meeting Scheduler**](https://leetcode.com/problems/meeting-scheduler/)        similar to [[LC 986. Interval List Intersections]]

## 🏆 MERGE INTERVALS — Final Master List

### **MUST-DO (Core Mastery — FAANG++ Level)**

- [x]  [LC 56 – Merge Intervals](https://leetcode.com/problems/merge-intervals/)
- [x]  [LC 57 – Insert Interval](https://leetcode.com/problems/insert-interval/)
- [x]  [LC 986 – Interval List Intersections](https://leetcode.com/problems/interval-list-intersections/)
- [x]  [LC 759 – Employee Free Time](https://leetcode.com/problems/employee-free-time/)
- [x]  [LC 1229 – Meeting Scheduler](https://leetcode.com/problems/meeting-scheduler/)
- [x]  [LC 1272 – Remove Interval](https://leetcode.com/problems/remove-interval/) _(reverse merging logic)_
- 632

