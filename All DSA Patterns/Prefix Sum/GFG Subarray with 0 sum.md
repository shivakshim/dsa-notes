🔗[Problem link](https://www.geeksforgeeks.org/problems/subarray-with-0-sum-1587115621/1)
Find if there is a **subarray** (of size at least one) with **0 sum**

---
#### ⌛Brute Force 

- Nested loops.

#### 🗝️Key Concept

- You’re checking **if the same preSum appeared before** → which means the in-between portion canceled out to zero.

### 🧠Intuition/Approach

- Keep a map of presum, index.
- for every i, calculate presum, check if it is already present in the map.
- If yes, that means the subarray between them is 0, return true.
- otherwise insert the presum ,i in the map.

### ❓Note

- We don't have to check if -presum is present, but if presum is present.

### ⌛TC 
- Brute - O(N2)
- Optimized - O(n)

### 📦SC
- Brute - O(1)
- Optimized - O(n)

---

### ✅Solution

```cpp
bool subArrayExists(vector<int>& arr) {
        // Your code here
        unordered_map<int,int> mp;
        mp[0] = -1; //for sum = 0; idx =0
        int presum = 0;
        
        for(int i=0; i < arr.size(); i++)
        {
            presum += arr[i];
            if(mp.count(presum) &&  (i - mp[presum] >= 1))
            return true;
            else mp[presum] = i;
        }
        return false;
    }
```
 
 