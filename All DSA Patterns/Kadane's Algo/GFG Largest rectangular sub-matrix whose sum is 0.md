🔗[Problem link](https://www.geeksforgeeks.org/problems/largest-rectangular-sub-matrix-whose-sum-is-0/1)


---
#### ⌛Brute Force 

- Only prefix sum 2d.

#### 🗝️Key Concept

- same as [[LC 363. Max Sum of Rectangle No Larger Than K]], just instead of <=k, we need to check maxlenght of compressed array that gives subarray sum = 0.

### 🧠Intuition/Approach

- **Fix top row**.
- **Iterate bottom row** → build a **compressed 1D array** of column sums between top..bottom.
- **Run 1D max subarray ≤ k** on compressed:
    - Maintain running prefix sum.
    - Use an map to find longest length subarray = 0.
    - Update maxWidth.
- After every bottom's compression arrays maxWidth is found, find area = (bottom-top)) * maxWidth.
- **Track global max**area across all top–bottom choices.

### ❓Note

- Don’t try plain Kadane → it only works for max-sum, not exact sum=0.
- Init hashmap with `{0: -1}` to catch cases starting at col 0.
- Time complexity = O(n² * m).

### ⌛TC 
- Brute - O(n4 * m)
- Optimized - O(n² * m)

### 📦SC
- Brute - O(1)
- Optimized - O(n)

---

### ✅Solution

```cpp
 int prefixsum(vector<int> &compressed){
        unordered_map<int, int> mp;
        mp[0] = -1;
        int preSum = 0, maxWidth = INT_MIN;
        
        for(int i = 0; i<compressed.size(); i++){
            preSum += compressed[i];
            if(mp.count(preSum))
                maxWidth = max(maxWidth, i - mp[preSum]);
            else 
                mp[preSum] = i;
        }
        return maxWidth;
    }
    int zeroSumSubmat(vector<vector<int>>& mat) {
        //compress like kadane's
        int n = mat.size();
        int m = mat[0].size();
        int ans  = INT_MIN;
        
        for(int top=0; top<n ; top++){
            vector<int> compressed(m, 0);
             for(int bottom = top; bottom < n; bottom++){
                 for(int col = 0; col<m; col++){
                    compressed[col] += mat[bottom][col];
                 }
                ans = max(ans ,(bottom-top+1)*prefixsum(compressed));
             }
        }
        return ans;
    }
```
 
 