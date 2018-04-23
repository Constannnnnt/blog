---
layout: post
title: Leetcode128 Longest Consecutive Sequence
tags: [Leetcode]
---
Given an unsorted array of integers, find the length of the longest consecutive elements sequence.

Your algorithm should run in O(n) complexity.

<!--excerpt-->

For example:

```
Input: [100, 4, 200, 1, 3, 2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.
```

Approach:


Solution:

```C++
class Solution {
public:
    int longestConsecutive(vector<int>& nums) {
        int res = 0;
        unordered_map<int, int> Map;
        for (auto num : nums) {
            if (Map.find(num) != Map.end()) {
                // duplicates
            } else {
                // find if num - 1 has already had sequence
                int left = (Map.find(num - 1) != Map.end()) ? Map[num - 1] : 0;
                // find if num + 1 has already had sequence
                int right = (Map.find(num + 1) != Map.end()) ? Map[num + 1] : 0;
                int record = left + right + 1;

                // update num
                Map.insert({num, record});
                // update the maximum sequence length
                res = max(res, record);

                // since it is expanding, then update the boundary
                if (Map.find(num - left) != Map.end()) {
                    Map[num - left] = record;
                }

                 if (Map.find(num + right) != Map.end()) {
                    Map[num + right] = record;
                }
            }
        }
        return res;
    }
};
```

Conclusion:
I have learned and reviewed several things from this question: