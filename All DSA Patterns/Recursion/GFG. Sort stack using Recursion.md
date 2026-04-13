🔗[Problem link](https://www.geeksforgeeks.org/problems/sort-a-stack/1)

---

#### 🗝️Key Concept

- We need 2 recursive functions :  
1. The first one keeps storing the top , while we reach the bottom of stack so that we can rearrange in sorted order.
2. The second one makes sure it's pushing the elements in sorted manner.


---

### ✅Solution

```cpp
    void helper(stack<int> &st, int ele){
        if(st.empty() || st.top() <= ele){
            st.push(ele);
            return;
        }
        
        int top = st.top(); st.pop();
        helper(st, ele);
        st.push(top);
    }
  
    void sortStack(stack<int> &st) {
        // code here
        if(st.empty()) return;
        
        int ele = st.top(); st.pop();
        sortStack(st);
        helper(st, ele);
    }
```
 
 