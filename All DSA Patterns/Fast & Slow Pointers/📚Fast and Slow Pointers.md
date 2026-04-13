### 🧠  Core Pattern

-  A technique where **two pointers move at different speeds (usually 1x and 2x)** to detect or exploit cycles, intersections, or relationships in sequences.
- Imagine you're running on a circular track with a friend:
    If it's circular → you’ll meet again.
    If it’s a straight line → your friend will reach the end and stop.
#### 💡Cheat Cue
> **Fast & Slow = "Is there a loop if we keep moving forward?"**
   
---
### ⚙️ Code Template


```cpp
 // Cycle Detection (Floyd’s Algorithm)
ListNode slow = head;
ListNode fast = head;
while (fast != null && fast->next != null) {
    slow = slow->next;
    fast = fast->next->next;
    if (slow == fast) { // cycle detected
        return true;
    }
}
return false;
```

---

#### 🔍 Keywords in Questions

- **loop, cycle, repeat, infinite, meeting point, intersection, turtle & hare, step repeatedly, next pointer, next index.**
❓***You're asked to:
- Detect cycle
- Detect infinite loops,
- Find entry/start of cycle,
- Calculate cycle length,
- Or find a special intersection point.

---

#### 🚫 Common Mistakes & Edge Cases

- **Empty or single-node linked list** → Always check `fast != null && fast.next != null`.
- List empty → return null/false early.
- **Off-by-one errors** in cycle start finding → Meeting point ≠ start.
- **Non-cyclic sequences** → Your loop must terminate.
- Thinking it's only for linked lists → Nope, arrays and number problems can be mapped as "linked lists with next pointers."

---

### 📊 Fast & Slow Pointer Master Sheet 

#### 1. Cycle Detection in LinkedList - [[🐢Floyd’s Cycle Detection Algorithm]]

- **Use case**: Detect if a linked list, find start of cycle.
- **Cue**: Problem talks about _loop, infinite, cycle, repeat without stopping_.
- **Follow-ups**: Find cycle start, cycle length, multiple cycles, array jump game cycle detection.
- **Must-do**:
- [x] [**LC 141 – Linked List Cycle**](https://leetcode.com/problems/linked-list-cycle/)   Solution : ***[[LC 141. Linked List Cycle|Click here]]
- [x] [**LC 142 – Linked List Cycle II**](https://leetcode.com/problems/linked-list-cycle-ii/)    Solution : ***[[LC 142. Linked List Cycle II|Click here]]

#### 2. Find Middle of Linked List

- **Use case**: Split a list into halves (palindrome, reorder list, merge sort).
- **Cue**: Mentions _middle node, split in half, reorder, reverse second half_.
- **Follow-ups**: Combine with reverse second half + merge technique (143, 234).
- **Must-do**:
- [x] [**LC 876 – Middle of the Linked List**](https://leetcode.com/problems/middle-of-the-linked-list/)    Solution : *[[876. Middle of the Linked List|Click here]]
- [x] [**LC 143 – Reorder List**](https://leetcode.com/problems/reorder-list/)    Solution : *[[143. Reorder List|Click here]]
- [x] [**LC 234 – Palindrome Linked List**](https://leetcode.com/problems/palindrome-linked-list/)     Solution : *[[234. Palindrome Linked List|Click here]]*

### 3. Detect Duplicate in Array (Cycle-based Index)

- **Use case**: Array where numbers point to indices, find duplicate without extra space.
- **Cue**: Values are from `1..n`, array length = n+1.
- **Follow-ups**: Multiple duplicates, find missing + duplicate.
- **Must-do**:
- [x] [**LC 287 – Find the Duplicate Number**](https://leetcode.com/problems/find-the-duplicate-number/)    Solution : *[[287. Find the Duplicate Number|Click here]]*
- [x]  [LC 645. Set Mismatch](https://leetcode.com/problems/set-mismatch/)    Solution : ***[[LC 645. Set Mismatch|Click here]]

### 4. Happy Number / Digital Cycle

- **Use case**: Detect if a number sequence eventually reaches a loop.
- **Cue**: Problem mentions _keep transforming number until it stabilizes or loops_.
- **Follow-ups**: Similar to cycle detection but with math transformations.
- **Must-do**:
- [x] [**LC 202 – Happy Number**](https://leetcode.com/problems/happy-number/)    Solution : ***[[202. Happy Number|Click here]]
- [x] [**LC 457 – Circular Array Loop**](https://leetcode.com/problems/circular-array-loop/)    Solution : ***[[457. Circular Array Loop|Click here]]

### 5. Relative by GAP (instead of speed)

- **Use case**: operate on the k-th node from the end of a linked list in one pass. ✅
- **Cue**: "Kth position"
- **Follow-ups**: Remove/rotate from k.
- **Must-do**:
- [x] [**LC 19 – Remove Nth Node From End of List**](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)    Solution : ***[[19. Remove Nth Node From End of List|Click here]]
- [x] [**LC 61 – Rotate List**](https://leetcode.com/problems/rotate-list/)   Solution : ***[[LC 61. Rotate List|Click here]]


---

### ✅ **VVIP FAANG-Worthy List (Must-Do)**

#### 🏎️🐢 Fast & Slow Pointer Must-Do Problems

- [x] [**LC 141 – Linked List Cycle**](https://leetcode.com/problems/linked-list-cycle/)
- [x] [**LC 142 – Linked List Cycle II**](https://leetcode.com/problems/linked-list-cycle-ii/)
- [x] [**LC 876 – Middle of the Linked List**](https://leetcode.com/problems/middle-of-the-linked-list/)
- [x] [**LC 202 – Happy Number**](https://leetcode.com/problems/happy-number/)
- [x] [**LC 234 – Palindrome Linked List**](https://leetcode.com/problems/palindrome-linked-list/)
- [x] [**LC 143 – Reorder List**](https://leetcode.com/problems/reorder-list/)
- [x] [**LC 19 – Remove Nth Node From End of List**](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)
- [x] [**LC 61 – Rotate List**](https://leetcode.com/problems/rotate-list/)
- [x] [**LC 287 – Find the Duplicate Number**](https://leetcode.com/problems/find-the-duplicate-number/)
- [x] [**LC 457 – Circular Array Loop**](https://leetcode.com/problems/circular-array-loop/)

#### 💡 Advanced follow-ups (NOT fast & slow : Linkedlist questions)

- [x] [**LC 82 – Remove Duplicates from Sorted List II**](https://leetcode.com/problems/remove-duplicates-from-sorted-list-ii/)   Solution : ***[[LC 82. Remove Duplicates from Sorted List II|Click here]]
- [x] [**LC 83 – Remove Duplicates from Sorted List**](https://leetcode.com/problems/remove-duplicates-from-sorted-list/)     Solution : ***[[LC 83. Remove Duplicates from Sorted List|Click here]]
- [x] [**LC 328 – Odd Even Linked List**](https://leetcode.com/problems/odd-even-linked-list/)  Solution : ***[[LC   328. Odd Even Linked List|Click here]]
