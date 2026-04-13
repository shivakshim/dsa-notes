# 🪄 Trick – Counting Subarrays with Sliding Window

**When window `[l…r]` is valid:**  
➡️ The number of subarrays ending at `r` = **`(r - l + 1)`**

---

**Why?**

- Subarrays ending at `r` are:  
    `[r], [r-1,r], [r-2,r], … [l,r]`
- That’s exactly `(r - l + 1)` subarrays.

---

**Usage**
- Problems where we _count_ valid subarrays (not find max/min).
- Typical conditions: product < K, sum ≤ K, at most K distinct, etc.