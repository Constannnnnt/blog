---
layout: post
title: Leetcode23 Merge k Sorted Lists
tags: [Leetcode]
---
Merge k sorted linked lists and return it as one sorted list. Analyze and describe its complexity.

<!--excerpt-->

For example:

```
Input:
[
  1->4->5,
  1->3->4,
  2->6
]
Output: 1->1->2->3->4->4->5->6
```

Solution:

1. My first solution: The first time when I met this question, I thought of Leetcode21 - merge two lists and I thought we could use recursion to solve this problem. But it finally turns out it failed with memory exceed limit. The space complexity is O(1), while the time complexity is `2n + 3n + ... + kn = [(k+1)*k/2 - 1] *n = O(nk^2)`.
```C++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
        if (!l1) return l2;
        if (!l2) return l1;
        if (!l1 && !l2) return NULL;

        ListNode* ret = new ListNode(0);
        ListNode* record = ret;
        while (l1 && l2) {
            if (l1->val < l2->val) {
                record->val = l1->val;
                l1 = l1->next;
                if (l1) {
                    record->next = new ListNode(0);
                    record = record->next;
                }

            } else {
                record->val = l2->val;
                l2 = l2->next;
                if (l2) {
                    record->next = new ListNode(0);
                    record = record->next;
                }
            }
        }
        if (l1) {
            record->next = l1;
        }
        if (l2) {
            record->next = l2;
        }
        return ret;

    }
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        if (lists.size() == 0) return NULL;
        if (lists.size() == 1) return lists[0];
        ListNode* ret = NULL;
        for (int i = 0; i < lists.size(); i ++) {
            ret = mergeTwoLists(ret, lists[i]);
        }
        return ret;
    }
};
```

2. My second solution: We use priority queue here. First, we put the smallest element in every list in to a priority queue (min heap), and then we extract the smallest one from the queue at every step and put its next neighbor in the queue. Therefore, we could sucessfully put every element in this priority queue and then achieve the linking. The size of a priority queue is `k` all the time, it takes `logk` to insert a new element, and there are all `nk` elements, so, the time complexity is `O(nklogk)` and space complexity is `O(k)`.
```C++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:

    struct compareNode {
        bool operator()(ListNode* p, ListNode*q) {
            return p->val > q->val;
        }
    };

    ListNode* mergeKLists(vector<ListNode*>& lists) {
        if (lists.size() == 0) return NULL;
        if (lists.size() == 1) return lists[0];
        ListNode* ret = new ListNode(0);
        ListNode* record = ret;
        priority_queue<ListNode*, vector<ListNode*>, compareNode> pq;
        for (int i = 0; i < lists.size(); i ++) {
            if (lists[i]) pq.push(lists[i]);
        }

        while (!pq.empty()) {
            record->next = pq.top();
            record = record->next;
            pq.pop();
            if (record->next) pq.push(record->next);
        }

        return ret->next;
    }
};
```

Conclusion:
I have learned and reviewed several things from this question: