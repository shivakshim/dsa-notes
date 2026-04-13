[[💡Sliding window + 2 hashmaps trick|OG sheet]]
## 🔑 When to Use

- Whenever we want to find **windows in string `s` that contain all the elements of another string `p`**.
- `p` can be:
    - An anagram
    - A permutation
    - A plain string
    - A string of words

Since there’s a constraint on the window, we know sliding window is the way.

---

## ⚠️ Issues in Using Sliding Window

- We need to track if all elements of `p` are present in `s`.
- Naturally → think of a frequency map.
- But then:
    - How do we know when to stop expanding the window?
    - How do we check if the frequencies are “right”?
    - How do we know when _all_ the elements are satisfied?

This pushes us to keep **two maps**
1. `needed` → the elements + freq of `p` (static).
2. `window` → the elements + freq in the current sliding window (dynamic).

But just maps aren’t enough → we also keep a **count variable** to track how many elements are correctly matched.
- When `count == p.size()` (or `count == k` in word problems) → window is valid.
- This avoids O(n²) repeated comparisons.
    
---
## 📏 Types of Windows

### 1. Flexible Sliding Window

- Used when we just need to check if all elements of `p` are present in some window of `s`.
- Elements don’t have to be contiguous, so the window flexes (expand/shrink).

---

### 2. Fixed-Size Window

- Some problems guarantee the window size = `p.size()`.
- Example: finding anagrams/permutations of `p` in `s`.
- Logic:
    - Compute the first window.
    - Then slide: remove from left, add from right, update counts.
- Here we can directly compare `needed == window` since window length is fixed.
    - ⚠️ This is slower than using `cnt`, but still acceptable.

---

## 🧮 Maps vs Frequency Arrays

- If input space is tiny (e.g. lowercase letters only), use **arrays** instead of maps.
- Example: `p` over lowercase English letters → max 26 elements → use `int freq[26]`.

👉 Steps:
1. Build `needed[26]` and `window[26]`.
2. For the first window → update both.
3. While sliding:
    - `window[s[i-k]]--`
    - `window[s[i]]++`
4. Compare arrays directly (`O(26)` is way faster than map compare).

---

⚡ **Note:**

- In fixed-window problems, you _can_ directly compare maps because the window length is fixed → but it’s slower.
- In flexible-window problems, always use `cnt` to track matches.