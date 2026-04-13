🔗[Problem link](https://www.geeksforgeeks.org/problems/consecutive-1s-not-allowed1912/1)

---
#### 🗝️Key Concept

- Instead of verfiying, we create.
- For every index we have 2 choices : 0 or 1.
- So take 1 recurse, undo. take 0 recurse undo. no recursion after that since we cant skip an index completely.

### 🧠Intuition/Approach

- Start at index `i = 0` with empty vector `v`.
- If `i == n`, return 1 (valid string).
- If `v` is empty or `v.back() == 0`, push 1 → recurse → pop back.
- Push 0 → recurse → pop back.
- Return sum of all recursive results modulo `mod`.

### ❓Note

- Condition for skipping 1's : if(v.empty() OR v.back == 1)
- OR because otherwise the 1st 1 will never be pushed.
- 💡In subsets :  if we wanna check prev element never do it with i, since i might not be aligned with the actual prev in the array with which we are calculating subsets.


---

### ✅Solution

```cpp
 int mod = 1e9 + 7;
    
    int helper(int i, int n, vector<int> &v){
        if(i == n) return 1;
        
        int res = 0; //for each idx
        //take 1
        if(v.empty() || v.back()==0){
        v.push_back(1);
        res = (res + helper(i+1, n , v)) % mod;
        v.pop_back();
        }
        
        //take 0
        v.push_back(0);
        res = (res + helper(i+1, n , v)) % mod;
        v.pop_back(); //clear to backtrack
        
        return res;
    }
    
    // #define ll long long
    int countStrings(int n) {
        // code here
        vector<int> v;
        return helper(0, n, v);
        
    }
```
 
 