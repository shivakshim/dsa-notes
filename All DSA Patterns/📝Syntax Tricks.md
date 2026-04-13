
- unordered_set<int> s(nums1.begin(), nums1.end());  
  -  vector<int>(ans.begin(), ans.end()); 
  -  presum.resize(n, vector<int>(m, 0));
  - swap(nums1, nums2) 

- find in unordered_set takes O(1), in ordered set it takes O(logn)

- Sorting an vector of vectors that have 2 elements.
 sort(points.begin(), points.end(), [](auto &a, auto &b)
 