[🔗Problem link](https://leetcode.com/problems/two-sum/description/)
Given an array of integers `nums` and `target`, return _indices of the two numbers such that they add up to `target`_.

---

### 🧠Intuition

 Approach 1 : Using Hashmap
 - We use a hashmap to store nums[i],i .
 - for each element check if target - nums[i] is present in map. if yes-> return indices.
 - Store the element, its_idx in the map.
 - This way TC is optimized from o(n2) to o(n).

Approach 2 : Sorting + 2 pointer (similar to [[LC 167. Two Sum II (sorted)]])
- First sort the array.
- keep 2 pointer at opposite ends. 
- i(nums[i] + nums[j]) < target -> move i++, else move j--.

---

### ✅Solution

```cpp
vector<int> twoSum(vector<int>& nums, int target) {
       unordered_map<int,int> mp;
       for(int i=0; i<nums.size(); i++){
        if(mp.count(target - nums[i]))
            return {i, mp[target - nums[i]]};
        mp[nums[i]] = i;
       }
       return {};
    }
```


