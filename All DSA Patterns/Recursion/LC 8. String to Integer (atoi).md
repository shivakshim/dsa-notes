
🔗[Problem link](https://leetcode.com/problems/string-to-integer-atoi/description/)


---
#### ⌛Brute Force 

- Iteration

#### 🗝️Key Concept

- Recursively convert the chars into ints and if i == n or !isdigist(s[i]) then return the sign*ans

### 🧠Intuition/Approach

- In main funtion :- Skip spaces.
- Check `+`/`-` for sign.

Then in rec helper function
- Recursively build number from digits.
- Stop on non-digit or end, return `sign * ans`.
- Clamp to `INT_MIN/INT_MAX` if overflow.


### **Time Complexity (TC)**

- You scan **each character of the number once** in recursion.
- Let `n` = length of the numeric part of the string.  
    ✅ **TC = O(n)*

### **Space Complexity (SC)**

- Recursive calls go **one per digit**, so **stack depth = n**.
- Each call uses constant extra space.  
  ✅ **SC = O(n)** due to recursion stack

---

### ✅Solution

```cpp
 int helper(string &s, int i, long long ans, int sign){
      if(i >= s.length() || !isdigit(s[i])) 
        return (int)(sign*ans);

      ans = ans*10 + (s[i] -'0');
      if(sign*ans >= INT_MAX) return INT_MAX;
      if(sign*ans <= INT_MIN) return INT_MIN;

      return helper(s, i+1, ans, sign);
    }

    int myAtoi(string s) {
     int i = 0;
     while(i < s.length() && s[i] == ' '){
        i++;
     }

     int sign = 1;
     if(i < s.length() && (s[i] == '+' || s[i] == '-')){
        sign = (s[i] == '-') ? -1 : 1;
        i++;
     }

     return helper(s, i, 0, sign);
    }
```

 
 