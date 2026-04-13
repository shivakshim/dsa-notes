
### 🧠Key Concept
Branching = “I can’t trust my gut to pick one path… so I try _both_ and see which survives.”

In code, this often becomes:
`return helper(l+1, r) || helper(l, r-1);`

---
### **📚Branching Cheat Sheet — When to Explore Both Sides**

##### **1. Palindrome-ish Problems**

- **Keywords:** _at most one removal_, _almost palindrome_, _delete ≤ 1 char_.
- **Examples:**
    - [[LC 680. Valid Palindrome II]] – skip left OR right at mismatch.
    - _Remove one char to make palindrome_ (same vibe).
- **Trigger:** _Mismatch where both sides look viable._

##### **2. “One Modification Allowed” Problems**

- **Keywords:** _at most one modification_, _can be non-decreasing after one change_.
- **Examples:**
    - [665. Non-decreasing Array] – change `nums[i]` OR `nums[i+1]` to fix break.
    - _One flip to make string monotone_.
- **Trigger:** _Single allowed change, unclear which element to tweak._

##### **3. Two Close Candidates**

- **Keywords:** _remove one element_, _insert one element_, _skip one_.
- **Examples:**
    - _Valid mountain array after removing one_
    - _Almost sorted after removing one element_.
- **Trigger:** _Two conflicting elements, both plausible to drop._

##### **4. Linked List Deletion/Tweak**

- **Keywords:** _delete one node to make palindrome/sorted_.
- **Examples:**
    - _Delete one node to make LL palindrome_ – skip left or right pointer.
- **Trigger:** _Mismatch in a linear structure, and you get only one skip._
    
##### **5. “Can you form X after ≤k edits?”**

- **Keywords:** _edit distance ≤ 1_, _insert/remove/replace one_.
- **Examples:**
    - _One edit away_ (LeetCode 161) – try insert/remove/replace branching.
- **Trigger:** _String diff where one extra/missing char can fix both._

##### **6. “Can you win if you flip/change this once?”**

- **Keywords:** _maximum of one swap/flip allowed_, _find if can be balanced_.
- **Examples:**
    - _Flip one 0 to get max consecutive 1s_ – branch at zero positions.
- **Trigger:** _Operation limit = 1, choices = multiple._

---

### **🙅‍♂️Quick Recognition Rules**

- **k ≤ 1 or 2?** → Branch suspicion level: HIGH.
- **Mismatch/conflict with two valid candidates?** → Branch.
- **Can’t decide locally without simulating?** → Branch.
- **Cost of branching low (O(2n), O(2logn))?** → Do it.

#### **🔁Mental Shortcut**

Whenever you're stuck thinking: _“Damn, I can’t pick — should I skip left or right?”_  
Stop. Fork both. Let the algorithm decide.