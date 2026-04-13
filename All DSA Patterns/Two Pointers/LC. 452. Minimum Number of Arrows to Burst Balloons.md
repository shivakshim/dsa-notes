🔗[Problem link](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/description/)
Given the array `points` of balloons coordinates [x0, x1], return _the **minimum** number of arrows that must be shot to burst all balloons_.A balloon with `xstart` and `xend` is **burst** by an arrow shot at `x` if `xstart <= x <= xend`.

---
#### ⌛**Key Intuition**

- This screams **interval overlap problem**.  
  If two balloons overlap, **one arrow can pop them both** — just shoot anywhere inside the overlap.  
  If they **don’t overlap**, you need a separate arrow.

### 🧠Intuition

- **Step 1: Sort the Intervals**
	Sort balloons by their **ending coordinate** (`end`), not ***start.  
	Why? Because you want to shoot as early as possible (greedy) so you can cover max upcoming balloons. 
- **Step 2** :  Based on the overlapping, increment ans when interval doesn't overlap.

### ❓Why sort based on the End and not start of balloon

- ![[Pasted image 20250831124147.png|300]]
- As seen above if sorting was done based on the starting index, we would have checked balloons inside 10, which is wrong, because even inside 10 we need to make sure they are overlapping with each other.
- This can only be ensured by checking overlaps based on the minimum endpoints f the balloons.
- ***Sorting by start can fail if the first interval is long and the rest are far apart — it tricks you into thinking one arrow is enough but can force an early arrow that blocks you from an optimal future shot.

### ⌛TC 
- Brute - (n2)
- Optimized - **O(n log n)**

### 📦SC
- Brute - O(1)
- Optimized - O(1)

---

### ✅Solution

1. With Two Pointers
```cpp
int findMinArrowShots(vector<vector<int>>& points) {
        //sort by endpoints
        sort(points.begin(), points.end(), [](auto &a, auto &b) {
        return a[1] < b[1];
        });
        int ans = 1;
        int i = 0, j = 1;
        while(i < points.size() && j < points.size()){
            if(points[j][0] <= points[i][1]) j++;
            else{
                ans++;
                i = j;
                j++;
            }
        }
      return ans;
    }
```
 
 2. With Single pointer
 ```cpp
 int findMinArrowShots(vector<vector<int>>& points) {
        //sort by endpoints
        sort(points.begin(), points.end(), [](auto &a, auto &b) {
        return a[1] < b[1];
        });
        int ans = 1;
        int endpoint = points[0][1];
        for(int i = 1; i<points.size(); i++){
            if(points[i][0] > endpoint){
                endpoint = points[i][1];
                ans++;
            }
        }
      return ans;
    }
```