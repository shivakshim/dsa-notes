
### ⚙️ Core Idea:

In _Merge Intervals_ → you **combine** overlapping intervals into one big chunk.  
In _Overlapping Intervals_ → you **detect** or **count** overlaps, not merge them.

So same raw materials (intervals + sorting + comparisons), but different end goals.

### 🧠 Mnemonic:
| Sorting by     | Works for                                                      | Why                                                                     |
| -------------- | -------------------------------------------------------------- | ----------------------------------------------------------------------- |
| **End time**   | Checking for overlap / scheduling max non-overlapping meetings | Greedy selection of compatible intervals                                |
| **Start time** | Counting overlaps / min number of rooms                        | You simulate the timeline in order, tracking concurrent meetings via PQ |

##### 💡**WHY?

|Problem|Question|What we’re minimizing|
|---|---|---|
|**Meeting Rooms I (a.k.a. “Can attend all meetings?”)**|Are there _any_ overlaps?|Just checking if overlap exists|
|**Meeting Rooms II (a.k.a. “Min number of rooms required”)**|How many meetings overlap at once (i.e., min #rooms)?|**Count of overlaps at the same time**|
- maximize non - overlaps : Keep early ending ones, sort by end.
- Merge - sort by start.
---

### 🧩 Theory TL;DR:

1. **Sort intervals by start time** (always the first move).
2. Keep a variable `end` (the end of the last interval you’ve seen).
3. For each interval:
    - If `current.start < end` → that means **overlap detected**.
    - Otherwise, no overlap; update `end = current.end`.
4. You can:
    - Count overlaps
    - Return `true`/`false` if any overlap exists

---

## 🔁 **OVERLAPPING INTERVALS — Master List (FAANG-Core)**

### 🟨 Detect / Remove / Count Overlaps

> Optimize or track overlapping ranges.

- [x] [LC 435 – Non-Overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)                 💡[[LC 435. Non-overlapping Intervals|Solution]]
- [x] [LC 1288 – Remove Covered Intervals](https://leetcode.com/problems/remove-covered-intervals/)               💡[[LC 1288. Remove Covered Intervals|Solution]]
- [x]  [LC 253 – Meeting Rooms II](https://leetcode.com/problems/meeting-rooms-ii/)
- [x]  LC 252 – Meeting Rooms I

### 🟦 Greedy + Interval Optimization

> Choose minimal operations / ranges while handling overlaps.

- [x] LC 452 – Minimum Number of Arrows to Burst Balloons
- [x] [LC 1024 – Video Stitching](https://leetcode.com/problems/video-stitching/)                                 💡[[LC 1024. Video Stitching|Solution]]