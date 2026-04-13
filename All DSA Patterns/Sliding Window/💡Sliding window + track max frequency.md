If we want to find the longest window with at most k replacements.

---

### ✅Core Solution : 

- For any window `[l..r]`, the number of changes needed = `(window size) – (max frequency of a single char in that window)`.
- If that number ≤ k → window is valid.
- Else → shrink from the left.
- we calculate this maxfreq by keeping a variable maxfreq = max(maxfreq, freq[s[r]]);


### 🚨The Trick : We *don’t decrease* maxFreq when we shrink left

- When you shrink from the left, you **don’t decrease maxFreq** even if that was the max char.
- How is this even safe :
1. This is safe and never counts an invalid window because, even if the actual freq of maxfreq element does decrease, in the next loop, the window size also increases, making the difference bigger than k, thus making the window eventually invalid.
2. Otherwise some other elements frequency overrides this, because it becomes more, then this is our new max freq element we need answer for that.
3. Basically the maxfreq stays as long as some other element with more freq doesn't override it.
4. Other way to look at it is, we are basically checking if the difference between window size & maxfreq is <= k for it to be valid, we worry that not decreasing maxfreq might count some invalid windows where maxfreq has actually reduced, making the difference > k, but our maxfreq still might return same <=k, but here we have to note that, the window size is always growing, if for a particular window size & maxfreq, we got a difference <= k; with a maxfreq < this one, this window will most Definity be > k, specially with increasing size, which makes the difference only bigger -> impossible to be <= k.

