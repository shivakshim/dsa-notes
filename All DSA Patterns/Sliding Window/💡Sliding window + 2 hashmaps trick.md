When to use
- Whenever we want to find the windows in string s that contain all the elements of other string p.
- p can be an anagram or permutation, or simply a string or a string of words.
- Since there's a constraints o the window, we know to use sliding window, but how?

Issues in using sliding window 
- We need to track if all elements of p are present in s.
- Naturally we think of map.
- But if we do keep a map to store freq of elements in out sliding window, how do we know eh to stop?
- How do we check f the frequencies are right? Ad when do we know that all the freq are right now and we have gotten all the elements.
- This makes us think about keeping a 2nd map, the map that has the elements and freq of p.
- This map is purely for comparing the freq of individual element of p with those in the window.
- But we still have the issue- when to stop? when to know map has all elements of p? This needed map still only tell us that individual freq are satisfied or not , but how to now when all are? And keeping a loop will make O(n * n).
- For this we keep a count variable, which keeps the count of how many variables from p wee have in the window.
- Now lang with the 2 maps(to check individual elements frequency ) and the count variables, we know when the window is valid.

when we have a sliding window : 
- When we are simply supposed to check if all the elements are present in a window, these element don't have to be contiguous.

When we have a fixed sized window :

- In some questions where we only need if a particular string p and its possible permutations/anagrams are present in string, we basically know that this window will always have the size of p.
- hence we don't need a sliding window, we need a fixed size window.
- So we can apply the same logic - compute 1st window, keep removing at left, adding at right.

   When we use Freq arrays instead of maps : 
- If our space is tiny ,only a certain number of input in the map), then we can replace maps with freq arrays.
- Suppose when we just need to check for a word in a string we know that maximum possible elements we put in map can be 26, even if frequencies are more.
- In such cases we use freq arrays instead of maps, since its faster.
- To use freq arrays-> take 2 arrays -> for needed & window both (26,0).
- for the 1st window update both.
- then as the window moves, keep updating windowfreq[i-k]--, windowfreq[i]++. and check if windowfreq == needed(direct compare array, much faster than direct comparing maps).


⚡ **NOTE : We can directly compare maps in foxed window problems, because there we know where the window            stops, so we can solve it without a cnt, but its slow,