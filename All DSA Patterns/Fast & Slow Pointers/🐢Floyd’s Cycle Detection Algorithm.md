— a.k.a. the **Tortoise and Hare**.

### ❓What is it?

It uses **two pointers**:
- **Slow pointer (tortoise)** → moves **one step** at a time.
- **Fast pointer (hare)** → moves **two steps** at a time.

If there’s a cycle, eventually the fast pointer will “lap” the slow one, meaning they’ll meet at some node inside the cycle. 
If there’s no cycle, fast will just hit `nullptr`.

#### 💡Is it same as fast & slow pointers?
 **Fast and Slow Pointers
- One pointer moves one step (slow), the other moves two steps (fast).
 **Floyd's Cycle Detection algo - 
- A **specific use-case** of the fast/slow pointer method.
- Detects **if a linked list has a cycle**, and can also find **where the cycle starts**.
So yeah — **Floyd’s algorithm uses fast and slow pointers**, but not every fast/slow pointer problem is Floyd’s.


---

### 🧠Algorithm Steps

1. Start `slow = head`, `fast = head`.
2. Move:
    - `slow = slow->next`
    - `fast = fast->next->next`
3. If `fast` or `fast->next` becomes `nullptr` → **no cycle**.
4. If at any point `slow == fast` → **cycle detected!**

---

### ⚙️ Code Template

1. 🔄️**Cycle Detection

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


2. 🔛**Start of cycle

```cpp
// Once they meet, reset one pointer to head
slow = head;
while (slow != fast) {
    slow = slow->next;
    fast = fast->next;
}
return slow; // cycle start node
```


3. ↔️**Middle of cycle

```cpp
while (fast != null && fast.next != null) {
    slow = slow->next;
    fast = fast->next->next;
}
return slow; // middle
```


4. **📏Length of cycle

```cpp
if (fast) { // means a cycle exists
    int len = 0;
    ListNode *p = fast;   // pick the meeting point
    do {
        p = p->next;      // move step by step
        len++;
    } while (p != fast);  // stop once we loop back
    cout << len;
}
```

---

### ✨Why is it awesome?

- **Time:** O(n) 
- **Space:** O(1) (no extra set/hashmap)

Compare this to your brute force:
- Brute force → O(n²)
- Set-based → O(n) time, O(n) space
- Floyd’s → O(n) time, O(1) space (best of both worlds)