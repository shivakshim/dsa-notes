## 📌 Core Pattern – Quick Select / K-th Element / Top-K

Quick Select = **partition-based selection** → find k-th smallest/largest or top-k elements efficiently.

💡 Think: **pick a pivot → partition → recurse only where the answer can be**
- Average time: **O(n)**
- Worst case: **O(n²)** (rare if pivot is random)
- Often combined with: heap, custom comparator, distances, or profits

#### **🧠Points to remember : 
1. We work on the value of randomly selected index, but return index of sorted position of that value, since k is an index.
2. When we call the function(not the rec call, but the 1st main call) : we pass k-1 (0-based indexing).
3. 💡If we need to find Kth smallest we pass [k-1], if we want to find kth largest we pass :  [n - k]

---

## 🎯 Cue (When to Apply)

- “Find k-th smallest / largest element”
- “Top-k elements by frequency / distance / profit”
- “Median” or “percentile”
- “Optimize subset efficiently without full sort”
- “Partition array around pivot, recurse on one side only”

---

## ⚙️ Template (Typical Quick Select)

##### **🧠Quick select function Template : 

```cpp
int quickSelect(vector<int>& arr, int left, int right, int k) {
    // Pick a random pivot index
    int pivotIndex = left + rand() % (right - left + 1);

    pivotIndex = partition(arr, left, right, pivotIndex);

    if (pivotIndex == k) return arr[pivotIndex];            // Found k-th element
    else if (pivotIndex > k) return quickSelect(arr, left, pivotIndex - 1, k); // Search left
    else return quickSelect(arr, pivotIndex + 1, right, k); // Search right
}
```
💡Note :  When calling this function we pass k-1 (0-based indexing).

#####  **🧠Partition function: move smaller left, bigger right, pivot in final spot.
```cpp
int partition(vector<int>& arr, int left, int right, int pivotIndex) {
    int pivot = arr[pivotIndex];
    swap(arr[pivotIndex], arr[right]); // move pivot to end
    int storeIndex = left;

    for (int i = left; i < right; i++) {
        if (arr[i] < pivot) {
            swap(arr[i], arr[storeIndex]);
            storeIndex++;
        }
    }

    swap(arr[storeIndex], arr[right]); // put pivot in final place
    return storeIndex;
}
```


---

## ⚠️ Misses / Edge Cases

- Worst case O(n²) if pivot is unlucky → random pivot fixes this
- k-th largest → transform to k-th smallest by `k = n - k`
- Duplicates / equal elements → make sure partition handles `<=` vs `<` consistently
- Stream / continuous median → sometimes need heap variant instead


## ⚠️ Quick Notes
- Random pivot → avoid worst-case O(n²)  
- Always recurse only on the side where k-th element lives  
- Keep mental map: **smaller-left | pivot | bigger-right**  
- Simulate partition by hand on small arrays → builds intuition for all variants  


---

## 🔀 Quick Select – Variants / Must-Do + Optional

Quick Select = **pivot → partition → recurse only on the side where the answer lives**  


### 1️⃣ Duplicates / Edge Cases
**Must-Do:**
- [x] [LC 215 – Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/) → Arrays with duplicates / k-th largest
**Optional:**
- [x] [LC 414 – Third Maximum Number](https://leetcode.com/problems/third-maximum-number/) → Handle duplicates / negative numbers    [[DSA PATTERNS GUIDE/All DSA Patterns/Quick Select/LC 414. Third Maximum Number|💡]]


### 2️⃣ Linked List / Non-Array Variants
**Must-Do:**
- [x] [LC 148 – Sort List](https://leetcode.com/problems/sort-list/) → k-th smallest in linked list, partition logic  
**Optional:**

### 3️⃣ Two-pointer + Partition Hybrids
**Must-Do:**
- [x] [LC 658 – Find K Closest Elements](https://leetcode.com/problems/find-k-closest-elements/)                                                                           [[LC 658. Find K Closest Elements|💡]]

### 4️⃣ Matrix / 2D Index Variants
**Must-Do:**
- [x] [LC 378 – Kth Smallest Element in a Sorted Matrix](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/) → 2D → 1D mapping 
Solution : Convert to 1D array -> normal quickselect.

### 5️⃣ Conceptual / Partition Extensions
**Must-Do:**
- [x] [LC 324 – Wiggle Sort II](https://leetcode.com/problems/wiggle-sort-ii/) → median partitioning  
- [x] [LC 75 – Sort Colors](https://leetcode.com/problems/sort-colors/) → Dutch National Flag 3-way partition      [[LC 75. Sort Colors (Dutch National Flag)💡]]
**Optional:**
- [x] [LC 451 – Sort Characters By Frequency](https://leetcode.com/problems/sort-characters-by-frequency/) → frequency + partition hybrid  
- [x] [LC 414 – Third Maximum Number](https://leetcode.com/problems/third-maximum-number/) → order-statistics intuition


---

## 💼 Master List of Must-Do Questions (10–12 Core)


- [x] [LC 215 – Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/) – OG Quickselect template
- [x] [LC 347 – Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/) – hybrid with hash + quickselect on freq
- [x] [LC 973 – K Closest Points to Origin](https://leetcode.com/problems/k-closest-points-to-origin/) – Euclidean distance + partition trick
- [x] [LC 324 – Wiggle Sort II](https://leetcode.com/problems/wiggle-sort-ii/) – hard variant, median partitioning trick
- [x] [LC 75 – Sort Colors](https://leetcode.com/problems/sort-colors/) – Dutch National Flag, conceptual precursor to partitioning
- [x] [LC 148 – Sort List](https://leetcode.com/problems/sort-list/) – linked-list quicksort flavor, builds mental connection
- [x] [LC 451 – Sort Characters By Frequency](https://leetcode.com/problems/sort-characters-by-frequency/) – optional, frequency + partition logic
- [x] [LC 658 – Find K Closest Elements](https://leetcode.com/problems/find-k-closest-elements/) – two-pointer + quickselect hybrid
- [x] [LC 414 – Third Maximum Number](https://leetcode.com/problems/third-maximum-number/) – baby version, order-statistic intuition




