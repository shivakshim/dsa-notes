# 🌀 **Core Pattern – Linked List Reversal (and its Derivatives)**

Linked List reversal is the **“foundation stone”** for a ton of LL problems.  
Once you nail this, you basically unlock _half of Linked List DSA_ 😎

💡 Think: “Pointers doing a little dance — next, prev, temp.”

At its heart, every question here is about controlling how pointers move and connect nodes while keeping track of what’s lost in reversal.

---

## 🎯 Cue (When to Apply)

- “Reverse k nodes / reverse a sublist / rotate / reorder”
- “Find palindrome / clone / detect cycle”
- “Modify links while traversing”
- “In-place operations (no extra space)”
- “Merge or split reversed halves”

If you ever find yourself juggling 2–3 pointers (`prev`, `curr`, `next`), it’s probably this pattern 😎

---

## ⚙️ Template (Iterative Reversal)

### 🧱 Iterative Reversal (The Classic One)

👉 use 3 pointers → `prev`, `curr`, `next`  
we keep flipping `next` pointers till the end, then `prev` becomes new head.

```cpp
ListNode* reverseList(ListNode* head) {
    ListNode* prev = nullptr;
    ListNode* curr = head;
    ListNode* next = nullptr;

    while (curr != nullptr) {
        next = curr->next;    // store next node
        curr->next = prev;    // reverse current node’s pointer
        prev = curr;          // move prev forward
        curr = next;          // move curr forward
    }

    return prev; // new head of reversed list
}
```

🧠 **time:** O(n)  
🧠 **space:** O(1)  

### 🪄 Recursive Reversal (Elegant but tricky)

👉 idea: reverse the rest of the list first, then fix the first node’s link.  
base case = when `head` or `head->next` is `NULL`.  
on returning back up the stack, make each node’s `next` point backward.

```cpp
ListNode* reverseListRecursive(ListNode* head) {
    // base case
    if (head == nullptr || head->next == nullptr)
        return head;

    // reverse the rest of the list
    ListNode* newHead = reverseListRecursive(head->next);

    // fix the current node
    head->next->next = head;
    head->next = nullptr;

    return newHead; // new head remains the last node of original list
    }  
```


🧠 **time:** O(n)  
🧠 **space:** O(n) (recursion call stack)

---

## ⚠️ Misses / Edge Cases

- Forgetting to reconnect tails and heads when reversing sublists/groups
- Losing `next` pointer before re-linking (classic segfault)
- Forgetting null-checks when the list is shorter than k
- Palindrome/reorder problems where you must _restore_ the original list after reversal

---

## 🔀 Variants & Must-Do Questions

### 1️⃣ Basic Reversal

**Use case:** Reverse entire list — the OG pattern.  
**Cue:** “Reverse the linked list”, “return reversed head”.

- [x] [LC 206 – Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)
- [x] [LC 92 – Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/)                         💡[[LC 92. Reverse Linked List II - ITERATIVE|Solution]]

### 2️⃣ K-Group Variant (Advanced Iterative)

**Use case:** Reverse k nodes at a time.  
**Cue:** “k-group”, “chunk reversal”, “in groups of k”.

- [x]  [LC 25 – Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/)                💡[[LC 25. Reverse kGroup|Solution]]

### 3️⃣ Recursive Reversal (Mind-Bender 🤯)

**Use case:** Do reversal via recursion + chain unwinding.  
**Cue:** “recursive”, “call stack reversal”.
 - [x]  [LC 206 (Recursive Approach)](https://leetcode.com/problems/reverse-linked-list/)
 - [x]  [LC 92 – Reverse Linked List II (Recursive)](https://leetcode.com/problems/reverse-linked-list-ii/)       💡[[LC 92. Reverse Linked List II - Recursive|Solution]]

### 4️⃣ Palindrome Check /Reorder / Modify Order (Reversal + Compare)

###### 🧠**NOTE : [[📚Fast and Slow Pointers]] can be used to find middle of LL, Without having to count all nodes and looping till mid.
**Use case:** Check if list is palindrome by reversing second half.  Mix first and second halves (reversal + merge).  
**Cue:** “palindrome linked list”, “check same forward & backward”. “Reorder list”, “zigzag”, “folded list”.

- [x]  [LC 234 – Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)                           💡[[234. Palindrome Linked List|Solution]]
- [x]  [LC 143 – Reorder List](https://leetcode.com/problems/reorder-list/)                                            💡[[143. Reorder List|Solution]]
**LC 445 – Add Two Numbers II** → reverse both lists before addition


---

## 💼 **Master List of Must-Do Questions**

- [x]  [LC 206 – Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)
- [x] [LC 25 – Reverse Nodes in k-Group](https://leetcode.com/problems/reverse-nodes-in-k-group/)
- [x] [LC 92 – Reverse Linked List II](https://leetcode.com/problems/reverse-linked-list-ii/)
- [x]  [GFG – Reverse a Linked List in groups of given size](https://www.geeksforgeeks.org/problems/reverse-a-linked-list-in-groups-of-given-size/1)
- [x]  [LC 234 – Palindrome Linked List](https://leetcode.com/problems/palindrome-linked-list/)
- [x]  [LC 143 – Reorder List](https://leetcode.com/problems/reorder-list/)

