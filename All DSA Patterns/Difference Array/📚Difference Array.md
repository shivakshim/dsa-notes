### 🔹 What is a Difference Array?

- Instead of storing the actual array values, we store how each element **differs from the previous one**.
- Formally:
    `diff[i] = arr[i] - arr[i-1]   (with arr[-1] = 0)`
- The **original array** can be rebuilt by taking a **prefix sum** of `diff`.
- Queries are generally given as [a,b,k] : add k to range (a,b)

### 🔹 Why use it?

- Useful for **range updates** (add a value `k` to all elements in `[l, r]`).
- Naive way: update each element in the range → O(r-l+1) per query → too slow.
- Difference array way:
    - `diff[l] += k
    - `diff[r+1] -= k`
    - Then take a prefix sum once at the end to “spread out” the effect.
- Complexity:
    - Build/updates: **O(1) per query**
    - Reconstruct final array: **O(n)**
    - Much faster when multiple queries are involved.

---

#### ✅Code Template

```
vector<int> diff(n, 0);

// Apply all updates o(m)
for (auto &op : updates) {
    int l = op[0], r = op[1], val = op[2];
    diff[l] += val;
    if (r + 1 < n) diff[r + 1] -= val;
}

// Build final array o(N)
vector<int> res(n, 0);
res[0] = diff[0];
for (int i = 1; i < n; i++) {
    res[i] = res[i-1] + diff[i];
}

```

---
### 🧠**Mental Cue to Recognize It**

- You see:
    - “Add to a range” (increment/decrement) repeatedly
    - Final answer needed after **all operations**
    - No real-time queries in between
Think: _Difference array is my Excalibur.

✅IMP Questions -[[DSA PATTERNS GUIDE/All DSA Patterns/Difference Array/📑Problem Set|📑Problem Set]]
