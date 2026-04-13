
### ❓**When to Use/Identify

- Both lists are **sorted by start time**.
- Each list is **pairwise disjoint** (no internal overlaps).
- You want **intersection**, **union**, or to check overlaps.

### 🧠**Core Idea**

- Maintain two pointers `i` and `j` for `A` and `B`.
- At each step, look at `A[i]` and `B[j]`.
- Find **overlap** using:
    `start = max(A[i].start, B[j].start) end   = min(A[i].end,   B[j].end)`
    If `start <= end` → intersection exists.
    
### 🔁**Pointer Movement Rule**

- Move the pointer with the **smaller end** forward:
    `if A[i].end < B[j].end: i++ else: j++`
- Why? Because that interval **can't intersect any further**.

### ✅Code Template

  ```cpp
   int i = 0, j = 0;
        while(i < firstList.size() && j < secondList.size()){
           int start = max(firstList[i][0], secondList[j][0]);
           int end = min(firstList[i][1], secondList[j][1]);
           //check for overlap
           if(start <= end){
            ans.push_back({start,end});
           }
           //move the pointer with smaller end
           if(firstList[i][1] < secondList[j][1]) i++;
           else j++;
        }
```

### ⌛**Time & Space**

- **O(m + n)** time (one scan each).
- **O(1)** extra space (ignoring output).

### 📝**Use Cases**

- Interval intersections (LeetCode 986).
- Merging k sorted intervals (if each is disjoint).
- Calendar free/busy time overlaps.

---

### ⚠️**Key Pitfalls**

1. Works only when each list is **individually merged/disjoint**.
2. If not → merge each list first (O(n log n)).
3. Don't increment both pointers blindly — move the one with smaller end.