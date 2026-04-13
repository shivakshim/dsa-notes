
## **1️⃣ SUBSET PATTERN (Pick / Not Pick)**

**Used when:**

- Order does NOT matter
- Each element can be either taken or skipped
- Typical problems: subsets, subsequences, “power set”

**Template:**
```cpp
void helper(int i, vector<int>& arr, vector<int>& temp) {
    if (i == arr.size()) {
        res.push_back(temp);
        return;
    }

    // Take
    temp.push_back(arr[i]);
    helper(i + 1, arr, temp);
    temp.pop_back();

    // Not Take
    helper(i + 1, arr, temp);
}
```


**Key idea:**  
👉 Every index has 2 choices: **pick or skip**.  
👉 No loop. Pure binary recursion.

---

## **2️⃣ COMBINATION PATTERN (Loop + choose element)**

**Used when:**

- You want combinations (order doesn’t matter)
- You want to avoid duplicates like picking the same index again
- Typical problems: combination sum, subsets with loops, k-combinations

**Template:**
```cpp
void helper(int start, vector<int>& arr, vector<int>& temp) {
    res.push_back(temp);

    for (int i = start; i < arr.size(); i++) {
        temp.push_back(arr[i]);
        helper(i + 1, arr, temp); // i + 1 ensures forward-only
        temp.pop_back();
    }
}
```

**Key idea:**  
👉 Use a **for loop** to generate next choices.  
👉 Move forward with `i+1` to avoid reusing earlier elements.  
👉 No skip/take — loop handles branching.

---

## **3️⃣ PERMUTATION PATTERN (Visited[] OR Swap)**

**Used when:**

- Order DOES matter
- Need to generate permutations
- Typical problems: permutations, string permutations

**Visited[] template:**
```cpp
void helper(vector<int>& arr, vector<int>& temp, vector<int>& used) {
    if (temp.size() == arr.size()) {
        res.push_back(temp);
        return;
    }

    for (int i = 0; i < arr.size(); i++) {
        if (!used[i]) {
            used[i] = 1;
            temp.push_back(arr[i]);

            helper(arr, temp, used);

            used[i] = 0;
            temp.pop_back();
        }
    }
}
```

**Key idea:**  
👉 Loop explores ALL indices  
👉 visited[] prevents repeating elements  
👉 Great when order matters

---

# 🌈 SUPER CUTE SUMMARY (for your brain)

|Pattern|When?|How it branches|
|---|---|---|
|**Subset (pick/not pick)**|All subsets|2 choices every index|
|**Combination (loop)**|Choose elements in increasing index order|Loop decides choices|
|**Permutation**|All arrangements, order matters|Loop + visited[]|


