🔗[Problem link](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/)
Given a string `s`, find the length of the **longest** **substring** without duplicate characters.

---
#### ⌛Brute Force 

- Nested loops

#### 🗝️Key Concept

- Maintain a sliding window + hashmap  to track characters; shrink window when duplicate appears → ensures substring always has unique chars.

### 🧠Intuition/Approach

- Use two pointers `l` and `r` for window.
- Expand `r`, add `s[r]` into map.  also keep removing s[l] from map, since it is no longer part of substring.
- If duplicate → shrink `l` until window has no duplicate.
- Track max length of valid window.

### ❓Note

- Remember to remove the arr[l] from map as we move l.
- To get rid of 2nd loop to move l, we do l++, and say continue this till l exceeds the duplicate element, by doing this, we end up at l 1step ahead of the duplicate.

### ⌛TC 
- Brute - O(n2)
- Optimized - O(n)

### 📦SC
- Brute - O(1)
- Optimized - O(1)

---

### ✅Solution

```cpp
int lengthOfLongestSubstring(string s) {
        int l = 0, r = 0, maxlen = 0;
        unordered_map<char, int> mp

        while(r < s.length()){
            if(mp.count(s[r])){  
                mp.erase(s[l]);  //remove them since it's out of the subarray we are considering
                l++;   //keep going till l goes ahead of the element to be removed
                if(l <= mp[s[r]]) continue;  
            }
            mp[s[r]] = r;
            maxlen = max(maxlen, r-l+1);
            r++;
        }
       return maxlen;
    }
```
 
 