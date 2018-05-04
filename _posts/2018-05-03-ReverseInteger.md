---
layout: post
title: Leetcode07 Reverse Integer
tags: [Leetcode]
---
Given a 32-bit signed integer, reverse digits of an integer.

<!--excerpt-->

For example:

```
Input: 123
Output: 321
```

```
Input: -123
Output: -321
```

```
Input: 120
Output: 21
```

Note:
Assume we are dealing with an environment which could only store integers within the 32-bit signed integer range: [−231,  231 − 1]. For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

Solution:

```C++
class Solution {
public:
    int pow(int v) {
        int ret = 1;
        for (int i = 0; i < v; i++) {
            int pre = ret;
            ret *= 10;
            if (ret / pre != 10) return 11;
        }
        return ret;
    }
    int reverse(int x) {
        if (x == INT_MIN) {
            return 0;
        }
        int abs_x = abs(x);
        vector<int> record;
        while (abs_x != 0) {
            int last = abs_x % 10;
            abs_x = (abs_x - last) / 10;
            record.push_back(last);
        }
        int ret = 0;
        for (int i = record.size() - 1; i >=0; i-- ) {
            int powv = pow(record.size() - 1 - i);
            if (powv == 11) return 0;
            int mulv = record[i] * powv;
            if (mulv / powv != record[i]) return 0;
            int sumv = ret + mulv;
            if (sumv < 0) return 0;
            if (sumv - mulv != ret) return 0; 
            ret = sumv;
        }
        if (x > 0) return ret;
        return 0 - ret;
    }
};
```

Conclusion:
I have learned and reviewed several things from this question: