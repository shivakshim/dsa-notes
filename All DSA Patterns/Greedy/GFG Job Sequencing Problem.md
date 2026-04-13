🔗[Problem link](https://www.geeksforgeeks.org/problems/job-sequencing-problem-1587115620/1)
You are given two arrays: **`deadline[]`,** and **`profit[]`,** which represent a set of jobs, where each job is associated with a **deadline**, and a **profit**. Each job takes 1 unit of time to complete, and only one job can be scheduled at a time. You will earn the profit associated with a job only if it is completed by its deadline. find:
1. The **maximum number of jobs** that can be completed within their deadlines.
2. The **total maximum profit** earned by completing those jobs.

---
#### ⌛Brute Force 

- Try all possible job sequences → pick ones that meet deadlines & give max profit.  

#### 🗝️Key Concept

- Do high-profit jobs _as late as possible_ before deadline.
- But to make sure the earlier time slot isn't waster for jobs that have a higher deadline, maintain the slots array.

### 🧠Intuition/Approach

- Pair up jobs as `(profit, deadline)`
- Sort by profit (desc).
- Create a slots array of size = maxDeadline.
- For each job → put it in the **latest empty slot ≤ its deadline**.  
  **Note:** Greedy ensures max profit since earlier slots are saved for smaller deadlines.

### ❓Note

- The search for slots starts from the deadline of the job and goes backward, this was it's guaranteed that the deadline is larger or equal to the slot's time.

### ⌛TC

- **Brute** – O(N! × N) 😭
- **Optimized** – O(N log N + N × maxDeadline)

### 📦SC

- **Brute** – O(1)
- **Optimized** – O(maxDeadline)

---

### ✅Solution

```cpp
class Solution {
  public:
    vector<int> jobSequencing(vector<int> &deadline, vector<int> &profit) {
        //create a vector of pairs
        int n = profit.size();
        vector<pair<int, int>> p;
        for(int i=0; i<n ; i++){
            p.push_back({deadline[i], profit[i]});
        }
        
        //sort the pairs vector based on profit(descending order)
        sort(p.begin(), p.end() , [](const pair<int, int>& a ,
        pair<int, int>& b){
            return a.second > b.second;
        });
        
        //find the maxdeadline to craete the slots array
        int maxdeadline = 0, maxprofit = 0, maxjobs= 0;
        for(auto x : deadline)
        maxdeadline = max(maxdeadline, x);
        
        vector<int> slots(maxdeadline+1, -1);
        
        //go through each job, insert if possible in slots, and count.
        for(auto &job : p){
           int deadline = job.first;
           int profit = job.second;
           
           for(int d = deadline; d> 0; d--){
               if(slots[d] == -1){
                   slots[d] = profit;
                   maxprofit += profit;
                   maxjobs++;
                   break;
               }
           }
        }
        
        return {maxjobs, maxprofit};
    }
};
```
 
 