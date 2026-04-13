🔗[Problem link](https://www.geeksforgeeks.org/problems/common-elements1132/1)
Find intersection/common elements of 3 arrays(only unique)

---
#### ⌛Brute Force 

- Store elements

### 🧠Intuition

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
 vector<int> commonElements(vector<int> &arr1, vector<int> &arr2,
                               vector<int> &arr3) {
        // Code Here
        vector<int> ans;
        sort(arr1.begin(), arr1.end());
        sort(arr2.begin(), arr2.end());
        sort(arr3.begin(), arr3.end());
        
        int i = 0, j = 0, k = 0;
        
        while(i < arr1.size() && j < arr2.size() && k < arr3.size()){
            if(i > 0 && arr1[i] == arr1[i-1]) {i++; continue; }
            if(j > 0 && arr2[j] == arr2[j-1]) {j++; continue; }
            if(k > 0 && arr3[k] == arr3[k-1]) {k++; continue; }
            
            if(i < arr1.size() && j < arr2.size() && k < arr3.size()){
            if(arr1[i] == arr2[j] && arr1[i] == arr3[k]) 
            {
                ans.push_back(arr1[i]);
                i++; j++; k++;
            }
            else {
                int mn = min({arr1[i], arr2[j], arr3[k]});
                if (arr1[i] == mn) i++;
                if (arr2[j] == mn) j++;
                if (arr3[k] == mn) k++;
             }
            }
        }
     return ans;
    }
```
 
 