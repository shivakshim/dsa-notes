
### 📏 1️⃣ Interval Length Rules

| Interval Type | Example  | Includes       | Length Formula | Why                                                   |
| ------------- | -------- | -------------- | -------------- | ----------------------------------------------------- |
| `[l, r]`      | `[2, 5]` | both ends      | `r - l + 1`    | you’re counting inclusively — 2, 3, 4, 5 = 4 elements |
| `(l, r]`      | `(2, 5]` | right end only | `r - l`        | 3, 4, 5 = 3 elements                                  |
| `[l, r)`      | `[2, 5)` | left end only  | `r - l`        | 2, 3, 4 = 3 elements                                  |
| `(l, r)`      | `(2, 5)` | neither end    | `r - l - 1`    | 3, 4 = 2 elements                                     |

---

### 🧭 2️⃣ 0-Based vs 1-Based Indexing

| Concept                                           | 0-based (like arrays)      | 1-based (like LinkedList positions) | Notes                                                             |
| ------------------------------------------------- | -------------------------- | ----------------------------------- | ----------------------------------------------------------------- |
| First element                                     | index `0`                  | position `1`                        | ✅ most confusion starts here                                      |
| To reach n'th position from i'th position         | move `i` steps from start  | move `i - 1` steps from start       | e.g. 0→1→2 vs 1→2→3                                               |
| Difference formula                                | distance = `abs(r - l)`    | distance = `abs(r - l)`             | same numerically, but “meaning” shifts                            |
| Count of elements between `l` and `r` (inclusive) | `r - l + 1`                | `r - l + 1`                         | formula same, interpretation different                            |
| No. of loops needed to go from [i to n]           | for(int i=0 ; i <= n; i++) | for(int i=1 ; i < n; i++)           | Because we are already starting at the i'th step so loops : = n-i |
| Decrement n till till we reach n                  | from 0 : <br>till n == 0   | From 1 :<br>Till n == 1             | To reach from i to n, decremenet n till it becomes i              |
| Reach the nth node                                | < n                        | < n                                 | in the last iteration we reach it & don't move ahead              |
| Process the n nodes                               | < n                        | <= n                                | also enter loop when its n'th node<br><=n-i                       |


---

### 🧮 4️⃣ Common Mini Rules

| Case                                    | Formula / Rule        | Intuition                        |
| --------------------------------------- | --------------------- | -------------------------------- |
| To move `k` steps ahead                 | decrement `k` until 0 | means you started before index 0 |
| To reach `n`th node (1-based)           | decrement until `1`   | means you started _on_ node 1    |
| Number of elements in `[i, j]`          | `j - i + 1`           | inclusive both ends              |
| Distance between two pointers `p` & `q` | `abs(p - q)`          | just numeric gap                 |
| Number of _edges_ between nodes         | `r - l`               | edges = nodes - 1                |


