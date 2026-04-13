🔗[Problem link](https://www.geeksforgeeks.org/problems/n-meetings-in-one-room-1587115620/1)
You are given timings of **n** meetings in the form of **(start[i], end[i])** .Return the **maximum** number of meetings that can be accommodated in a single meeting room, when only one meeting can be held in the meeting room at a particular time.

---
#### ⌛Brute Force 

- 

#### 🗝️Key Concept

- 

### 🧠Intuition/Approach

- 

### ❓Note

- 

### ⌛TC 
- Brute - 
- Optimized - 

### 📦SC
- Brute - O(1)
- Optimized - 

---

### ✅Solution

```cpp
int maxMeetings(vector<int>& start, vector<int>& end) {
        int n = start.size();
        vector<pair<int, int>> meets(n);
        for(int i=0; i<n; i++){
            meets[i] = {start[i], end[i]};
        }
        
        sort(meets.begin(), meets.end(), [](const pair<int, int>& a,
         const pair<int, int>& b) {
         return a.second < b.second;  // sort by end time
        });
        
        int prev = 0, ans = 1;
        for(int i=1; i<n; i++){
            if(meets[prev].second < meets[i].first){ //no overlap
            ans++;
            prev = i;
            }
        }
        
        return ans;
    }
```
 
 
