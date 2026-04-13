
### 💡 What it is:

- A technique where you maintain a **contiguous window (subarray / substring)** over the input, and “slide” it left/right without restarting the computation from scratch.
- The trick: reuse previous computations while moving the window, instead of recalculating everything every time.
-  Brute force = O(n²) or worse ➡️ Sliding window = O(n) or O(n log n)⚡
- 👉 you’re **tracking some property of a contiguous window** (length, sum, count, distinct chars, product, max/min, etc.) _while sliding across the array/string_.
- ❓Kadane vs Sliding window : how to differentiate?
   _“max sum” → Kadane_   ||   _“length/min/max/count with condition” → Sliding Window_

✨ Rule of thumb:
- **Fixed-size window (k known):** works with negatives ✅
- **Variable-size window (shrink/grow until condition met):** requires positives 🚨|| once i get a window, i need window bigger than this, i don't care about smaller or equal, hence lazy movement of l is guaranteed to work, it can only miss the smaller or equal length window, never bigger.


### 🧩 Core Pattern

- **Keep a right & left pointer
- **Expand right pointer** → grow the window.
- **Check condition** → “Is my window still valid?”
- **Shrink from left** → until window is valid again.
- **Update answer** → depending on problem: max length, min length, sum, count, etc.

### 🎯 Cues in Questions (How to Spot Sliding Window)

- Mentions _substring_ / _subarray_ /_window_ repeatedly.
- Talks about _consecutive elements_.
- Keywords like **longest**, **minimum window**, **at most k**, **fixed size k**, **maximum in every window**, **anagram / permutation / contains all**.
- Conditions like _“product < k”_, _“sum ≥ target”_, _“no repeating chars”_, _“at most X distinct”_.

### ⚙️ Generic Code Template

1. For variable sized window.
```cpp
int slidingWindow(vector<int>& nums, int k) {
    int n = nums.size(), left = 0, ans = 0; 
    unordered_map<int,int> freq; 

    for (int right = 0; right < n; right++) {
        freq[nums[right]]++;  
        while (/* window invalid */) {
            freq[nums[left]]--;
            if (freq[nums[left]] == 0) freq.erase(nums[left]);
            left++;
        }
        ans = max(ans, right - left + 1); // longest window
    }
    return ans;
}
```

2. For fixed size window
```cpp
int fixedSlidingWindow(vector<int>& nums, int k) {
		int sum = 0;
        for(int i=0; i<k; i++){
            sum += cardPoints[i];
        }
        
        int min/max_sum = sum;
		//keep sliding window : remove left, add right
        for(int i=len; i<nums.size(); i++){
            sum += nums[i] - nums[i-k];
            min/max_sum = min/max(sum, min/max_sum);
	        }
        return min/max_sum;
        }
```

### ⚠️ Misses and Edge Cases

-  Forgetting `while` instead of `if` when shrinking.
-  Off-by-one errors in `right - left + 1`.
-  Forgetting to update answer **before** shrinking (esp. in “minimum window” problems).
-  Mishandling when no valid window exists (return `0`, `""`, or check problem statement).
-  Over/under counting frequency maps (anagram/permutation style).
-  Forgetting to pop expired indices in deque-based max/min.


### 🧠 Keywords (Quick Pattern Recognition)

- **Longest** → expand right, shrink left when invalid.
- **Minimum** → expand until valid, shrink aggressively.
- **Fixed size k** → simple sliding sum/average or deque for max/min.
- **Anagram/Permutation/Contains all** → hashmap/freq array.
- **Max/Min each window** → deque monotonic trick.


---

## 🔀 Variants & Must-Do Questions

### 1️⃣ Fixed-size / Exact K Window

- **Use-case:** Max/min sum, max/min value in fixed-length numeric or string window  , works with negatives.
- **Cue / Keywords:** “Window of size K”, “maximum sum”, “maximum product”, “exact K elements”  
- **Approach / Mini-template:** Fixed-size window, keep running sum / max / min / deque, slide window.
- **Core Must-Do Questions:**
- [x] [LC 239 – Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)     Solution : ***[[LC 239. Sliding Window Maximum|Click here]]
- [x] [LC 1423 – Maximum Points from Cards](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/)    Solution : ***[[LC 1423. Maximum Points You Can Obtain from Cards|Click here]]
- [x] [LC 643 –Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)     Solution : ***[[LC 643. Maximum Average Subarray I|Click here]]

### 2️⃣ Variable-size / Expand-Shrink Window

- **Use-case:** Longest substring/subarray satisfying a condition (distinct chars, product < K, at-most-K) 
- **Cue / Keywords:** “Longest substring”, “at most K distinct”, “maximum consecutive…”, “product < K”  
- **Approach / Mini-template:** Expand right until invalid, shrink left while valid, track max / count / result  

- *There are 2 subvariants of variable sized widow based on the shrinking of l:
 ##### 🪄 **Shrink Rule (Lazy vs Jump)
1.  **Lazy shrink (`l++` step by step):** use when handling **counts/frequencies** (e.g., ≤ K distinct). We can’t skip extras. eg. LC 340, LC 904, LC 76.
2.  **Jump shrink (`l = lastDupIdx+1`):** use when handling **uniqueness** (e.g., all unique substring), or when we want all subarrays(not max/min) We must cut past the duplicate in one go.  eg. LC 3 

- **Core Must-Do Questions:**
- [x] [LC 3 – Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)   Solution : ***[[LC 3. Longest Substring Without Repeating Characters|Click here]]
- [x] [LC 340 – Longest Substring with At Most K Distinct Characters](https://www.geeksforgeeks.org/problems/longest-k-unique-characters-substring0853/1?utm_source=chatgpt.com)    Solution : ***[[LC 340. Longest Substring with K Uniques|Click here]]
- [x] [LC 904 – Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets/)      Solution : ***[[LC 904. Fruit Into Baskets|Click here]]
- [x] [LC 1004 – Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/)    Solution : ***[[LC 1004. Max Consecutive Ones III|Click here]]
- [x] [LC 713 – Subarray Product < K](https://leetcode.com/problems/subarray-product-less-than-k/)  Solution : ***[[LC 713. Subarray Product Less Than K|Click here]]


### 3️⃣ Minimum-length / Shrinking Window

- **Use-case:** Find smallest window/subarray satisfying sum or character constraints  
- **Cue / Keywords:** “Shortest substring/subarray”, “minimum length”, “sum ≥ target”, “contains all characters”  
- **Approach / Mini-template:** Expand right until valid, record valid, shrink left while valid, update min_length  
- **Core Must-Do Questions:**
- [x] [LC 76 – Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)   Solution :  ***[[LC 76. Minimum Window Substring|Click here]]
- [x] [LC 209 – Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)     Solution :  ***[[LC 209. Minimum Size Subarray Sum|Click here]]


### 4️⃣ Numeric / At-most-K / Replacement Tricks  

- **Use-case:** Transform array/string with limited flips/replacements/modifications  
- **Cue / Keywords:** “at most K flips/replacements/modifications”, “maximize consecutive…”, “pattern constraint”  
- **Approach / Mini-template:** Expand right, apply transformation/count changes, shrink left if exceeding K, track result  
- **Core Must-Do Questions:**
- [x] [LC 424 – Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)    Solution : ***[[LC 424. Longest Repeating Character Replacement|Click here]]


### 5️⃣ Fixed window + 2 maps : String / Permutation / Bonus Variants

- **Use-case:** Edge-case remixes, concatenations, exact-K, permutations  
- **Cue / Keywords:** “exactly K distinct”, “permutation”, “concatenation of all words”  
- **Approach / Mini-template:** [[🪟 Sliding Window + Freq Maps Cheat Sheet]]+  frequency counts  
- **Core Must-Do Questions:**
- [x] [LC 438 – Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)   Solution : ***[[LC 438. Find All Anagrams in a String|Click here]]
- [x] [LC 567 – Permutation in String](https://leetcode.com/problems/permutation-in-string/)  Solution : ***[[LC 567. Permutation in String|Click here]]
- [x] [LC 30 – Substring with Concatenation of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)   Solution : ***[[LC 30. Substring with Concatenation of All Words|Click here]]


####  Optional / Bonus (4 Questions)
 High-yield remixes or numeric/string edge-case variants.

- [ ] [LC 480 – Sliding Window Median](https://leetcode.com/problems/sliding-window-median/)
- [ ] [LC 2401 – Longest Nice Subarray](https://leetcode.com/problems/longest-nice-subarray/)  ->  Do with Bitwise
- [x] [LC 1838 – Longest Subarray with at Most K Modifications](https://leetcode.com/problems/frequency-of-the-most-frequent-element/)   Solution : ***[[LC 1838. Frequency of the Most Frequent Element|Click here]]

---

## 💼 Master List of Questions (All Variants)
These cover all core sliding window patterns for FAANG 50–70 LPA.

- [x] [LC 643 –Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)
- [x] [LC 3 – Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
- [x] [LC 1423 – Maximum Points from Cards](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/)
- [x] [LC 76 – Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)
- [x] [LC 239 – Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/)
- [x] [LC 209 – Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)
- [x] [LC 340 – Longest Substring with At Most K Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/)
- [x] [LC 904 – Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets/)
- [x] [LC 1004 – Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/)
- [x] [LC 713 – Subarray Product < K](https://leetcode.com/problems/subarray-product-less-than-k/)
- [x] [LC 424 – Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)
- [x] [LC 438 – Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)
- [x] [LC 567 – Permutation in String](https://leetcode.com/problems/permutation-in-string/)

####  Optional / Bonus (4 Questions)
 High-yield remixes or numeric/string edge-case variants.

- [x] [LC 30 – Substring with Concatenation of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)
- [ ] [LC 480 – Sliding Window Median](https://leetcode.com/problems/sliding-window-median/)
- [ ] [LC 2401 – Longest Nice Subarray](https://leetcode.com/problems/longest-nice-subarray/)
- [x] [LC 1838 – Longest Subarray with at Most K Modifications](https://leetcode.com/problems/frequency-of-the-most-frequent-element/)

