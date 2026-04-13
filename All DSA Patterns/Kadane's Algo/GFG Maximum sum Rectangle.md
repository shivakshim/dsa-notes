🔗[Problem link](https://www.geeksforgeeks.org/problems/maximum-sum-rectangle2948/1)
2d Kadane- return maximum submatrix sum.

---
#### ⌛Brute Force 

- 6loops.

#### 🗝️Key Concept

- Convert the **2D maximum submatrix sum** problem into a series of **1D maximum subarray sum (Kadane’s)** problems by:
1. **Fixing two row boundaries** (`top` and `bottom`).
2. **Compressing columns** between those rows into a 1D array (`colSum`), where each entry = sum of that column between `top` and `bottom`.
3. Running **Kadane’s algorithm** on `colSum` to find the best left–right boundary for that row range.
4. Repeating for all `(top, bottom)` pairs to cover all possible rectangle heights.

This reduces the problem from checking every rectangle explicitly (O(n²·m²)) to **O(n²·m)**.

### 🧠Intuition/Approach

- Step1 : We make rectangles for all possible heights. So we fix top & bottom(for every top & bottom possible).
- Step2: Now we compress all columns by taking each columns sum from top to bottom. , so basically we have a 1d array now, from top to bottom for each column.
- Step3 : now we use Kadane's algo to find maxsubarray for this height. this gives the particular sub matrix for this height that has maximum sum.
- Step4 :  once an entire height is checked from a top ,say top = 0 bottom = n-1, move to top =1, check for all heights.
- Step5 :  Keep updating max at every compressed array.

### ❓Note

- You don’t need to re-sum columns from `top → bottom` (4th loop) every time.  
  You can just **reuse the compressed array**:
- At the start of each new `top`, reset `compressed[col] = 0`.
- Then, as `bottom` increases row by row, just do:
    `compressed[col] += mat[bottom][col];`
- This way, `compressed[col]` always represents the sum of column `col` from `top → bottom`.

### ⌛TC 
- Brute - O(n6)
- Optimized - O(n3)

### 📦SC
- Brute - O(n)
- Optimized - O(n)

---

### ✅Solution

```cpp
int kadane(vector<int> &compressed){
        int currsum = compressed[0], maxsum = compressed[0];
        for(int i = 1; i<compressed.size(); i++){
            currsum = max(compressed[i], currsum+compressed[i]);
            maxsum = max(maxsum, currsum);
        }
        return maxsum;
    }
    int maxRectSum(vector<vector<int>> &mat) {
        // code here
        int ans = INT_MIN;
        int n = mat.size();
        int m = mat[0].size();
        
        for(int top=0; top<n ;top++){
            vector<int> compressed(m,0);
            for(int bottom = top; bottom < n; bottom++){
                for(int col=0; col<m; col++){
                    compressed[col] += mat[bottom][col];
                }
                ans = max(ans, kadane(compressed));
            }
        }
        return ans;
    }
```
 
 