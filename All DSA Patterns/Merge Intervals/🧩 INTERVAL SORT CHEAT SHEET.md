
**1. Merge intervals / insert intervals / employee free time / meeting rooms**  
👉 Sort by **start time**  
Because you care about when things _begin_, and you need to check if the next one overlaps the current.

**2. Minimum number of arrows to burst balloons (LeetCode 452)**  
👉 Sort by **end time**  
Because you want to shoot one arrow that covers as many intervals as possible — you wanna finish one before starting another.

**3. Non-overlapping intervals / activity selection / maximum meetings**  
👉 Sort by **end time** again  
You’re greedy — take the one that ends earliest so you can fit more after it.

**4. Interval scheduling conflicts (detect overlaps)**  
👉 Sort by **start time**, then check if current.start < prev.end.

**5. Remove intervals / merge k intervals**  
👉 Depends. Usually by **start time**, unless explicitly told to minimize overlaps — then **end time**.

---

### 🧠 INTERVAL PROBLEM MASTER REFERENCE

|#|Goal / Problem Type|What You’re Really Trying To Do (Core Logic)|Sort By|Underlying Concept (Abstract Form)|Key Idea / Pattern Name|Example Problems|
|---|---|---|---|---|---|---|
|**1**|**Merge Overlapping Intervals**|Combine all touching or overlapping intervals into one|**Start time**|You want to process intervals as they begin and merge those that overlap|**“Merge as you go”** pattern|Merge Intervals (56), Insert Interval (57)|
|**2**|**Activity Selection / Max Non-Overlapping Intervals**|Choose the maximum number of non-overlapping intervals|**End time**|End earliest → leaves room for more later|**“Greedy by earliest finishing time”**|Non-overlapping Intervals (435), Max Meetings in Room|
|**3**|**Minimum Number of Meeting Rooms / Max Concurrent Intervals**|You need to handle _all_ intervals; find how many overlap at once|**Start time** (use min-heap on ends)|Process in start order, always free the earliest-ending task|**“Sweep line + min-heap”**|Meeting Rooms II (253)|
|**4**|**Detect if Overlap Exists / Can Attend All Meetings**|Just check if any overlap exists|**Start time**|Compare each interval’s start to previous end|**“Overlap check”**|Meeting Rooms I (252)|
|**5**|**Minimum Number of Arrows / Covering Intervals**|You need to hit/cover all intervals with min actions|**End time**|Finish earliest so each action covers max future overlap|**“Covering with earliest finishing”**|Minimum Arrows to Burst Balloons (452)|
|**6**|**Employee Free Time / Common Free Interval**|Merge busy intervals and find gaps between merged ones|**Start time**|Combine overlapping intervals → gaps are the answer|**“Merge + find gaps”**|Employee Free Time (759)|
|**7**|**Insert Interval**|Add one interval into sorted list and merge if needed|**Start time**|Sequential merge process|**“Sequential merge”**|Insert Interval (57)|
|**8**|**Remove Covered Intervals**|Delete intervals that are completely inside another|**Start time**, tie-break by longer end first|Sorting ensures larger intervals come first|**“Containment check”**|Remove Covered Intervals (1288)|
|**9**|**Find Right Interval**|For each interval, find the next starting after it ends|**Start time**|Binary search for next start ≥ end|**“Search by start position”**|Find Right Interval (436)|
|**10**|**Minimum Platforms / Concurrent Trains**|Count simultaneous intervals at a station|**Sort start & end separately**|Two-pointer sweep: increment count at start, decrement at end|**“Two-pointer sweep line”**|Minimum Platforms (GFG classic)|
|**11**|**Interval Intersection**|Find overlapping portions of two sorted interval lists|**Both lists sorted by start**|Move pointer of interval that ends first|**“Two-pointer intersection”**|Interval List Intersections (986)|
|**12**|**Erase Overlap to Make Non-Overlapping**|Remove min intervals so none overlap|**End time**|Keep earliest finishing, delete conflicting ones|**“Greedy by earliest end”**|Non-overlapping Intervals (435 again)|
|**13**|**Merge K Interval Lists (sorted)**|Combine multiple sorted lists of intervals|**Start time**|Multi-way merge using min-heap of start times|**“K-way merge”**|Merge K Sorted Interval Lists|
|**14**|**Interval Coverage Length / Total Busy Time**|Find total union length of intervals|**Start time**|Merge intervals, sum merged lengths|**“Merge + sum”**|Total Covered Time (986 variant)|
|**15**|**Scheduling with Deadlines / Jobs / Tasks**|Maximize tasks before deadlines or minimize lateness|**End / deadline time**|Process by earliest deadline|**“Earliest deadline first”**|Job Scheduling, Course Schedule III|
### 🧩 Quick “When To Sort By” Mental Triggers

| When you...                                      | Sort by...                    | Why                                                 |
| ------------------------------------------------ | ----------------------------- | --------------------------------------------------- |
| want to **combine** overlaps                     | **Start time**                | you need to see when things begin and merge forward |
| want to **check for overlap**                    | **Start time**                | easy to compare each start vs last end              |
| want to **cover everything with fewest actions** | **End time**                  | end earliest → covers most                          |
| want to **select max non-overlapping intervals** | **End time**                  | end earliest → frees timeline                       |
| want to **count simultaneous events**            | **Start + end separately**    | sweep timeline for concurrency                      |
| want to **schedule all, tracking usage**         | **Start time** (heap on ends) | process in order, reuse freed slots                 |

